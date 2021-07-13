# The Challenge

````{panels}
:column: col-12
:card: border-2 shadow
:header: bg-warning
**This project in a nutshell**
^^^
Train and test a predictive model for forecasting Alzheimer's disease progression.

````

````{panels}
:column: col-12
:card: border-2 shadow
:header: bg-warning
**Code**
^^^

- [Jupyter Notebook(s) for this project](../notebooks/overview)
   - Pretty much all you'll need, alongside ADNI data access
- [TADPOLE GitHub repository](https://github.com/noxtoby/TADPOLE)
   - Mostly for information only
- [TADPOLE SHARE initiative](https://tadpole-share.github.io)
   - Some shared algorithms from TADPOLE Challenge

````

## Outcome Variables

The essence of TADPOLE is very simple. We provide a list of individuals previously recruited to the Alzheimer's Disease Neuroimaging Initiative (ADNI). These individuals have all provided data within earlier ADNI studies and have agreed to provide follow-up data in [ADNI 3](http://adni3.org/), which is just starting. ADNI refers to these individuals as "rollovers"; we will use the same term here. You are asked to forecast three features of each rollover individual at the time of their future data provision. Each feature is a common or likely outcome measure for clinical trials:

```{figure} ../../_static/img/tadpole_overview.png
---
name: tadpole_overview
align: center
width: 100%
---
**TADPOLE Challenge overview**.
```

### 1. Clinical status

- `CN` - Cognitively normal;
- `MCI` - mild cognitive impairment; or
- `AD` - probable Alzheimer's Disease
- At any point in time, this is one of CN (cognitively normal), MCI (mild cognitive impairment) or AD (probable Alzheimer's Disease).
- Provide relative likelihood of each option for each individual. Methods/algorithms that don't produce probabilistic estimates can still participate by setting binary probabilites (zero or one). N.B. relative likelihoods != probabilities.
- _Example: relative likelihoods of 1, 2, and 3 for a particular individual in a particular future month mean the participant believes the probabilities pCN, pMCI, and pAD are 1/6, 1/3, and 1/2 for CN, MCI, and AD, respectively, at that future time point. Negative likelihoods will be set to zero._

### 2. ADAS-Cog13 score

- The ADAS-Cog is frequently used as a primary outcome measure in clinical trials, e.g. [Doody et al., NEJM 2014](http://doi.org/10.1056/NEJMoa1312889); [Salloway et al., NEJM 2014](http://doi.org/10.1056/NEJMoa1304839).
- Continuous variable; provide a best-guess value as well as a 50% confidence interval for each individual.
- The intervals indicate the participant's confidence in the prediction. Participants should choose the intervals aiming for a coverage probability of 0.5, i.e. 50% of the best guesses should lie within the corresponding confidence interval.
- _Example: ADAS13 forecast for individual A is 25 with 50% CI of [21, 26]; ADAS13 forecast for individual B is 40 with 50% CI of [25, 50]. There is thus more confidence in the forecast for individual A (CI size 5) than for individual B (CI size 25)._

### 3. Ventricles volume, divided by intracranial volume

- As estimated via the [standard ADNI image processing pipeline](http://adni.loni.usc.edu/methods/mri-analysis/mri-pre-processing/), which uses the [FreeSurfer](http://freesurfer.net/) software.
- Same as ADAS13 (continuous variable, provide best-guess prediction plus 50% CI).

Since we do not know the exact time of future data acquisitions for any individual, **participants must make month-by-month forecasts** for each feature of each individual. Evaluation will use forecasts at the months that correspond to data acquisition.

The table below summarises the format of the forecasts using the above examples:

```{figure} ../../_static/img/sampleforecast_v1.png
---
name: tadpole_sample_forecasts
align: center
width: 100%
---
**TADPOLE sample forecasts**.
```


## Data Sets

Prior to TADPOLE, the ADNI study had [three phases](http://adni.loni.usc.edu/study-design/): ADNI1, ADNI GO and ADNI2. New participants were recruited across North America during each phase of the study and agreed to complete a variety of imaging and clinical assessments. Participants are followed and reassessed over time to track the pathology of the disease as it progresses. [ADNI3 launched in September 2016](https://fnih.org/what-we-do/current-research-programs/adni3) and i scheduled to run until 2022, aiming to recruit 1,200 volunteers as well as re-evaluate 800 previous ADNI participants ("rollovers") in this time.

We split the ADNI data into:

- `D1`: **Training** (from ADNI1/GO/2),
- `D2`, `D3`: **Prediction** (existing data from rollovers), and
- `D4`: **Test** data (ADNI3: future data from rollovers).

```{figure} ../../_static/img/Figure_Datasets.png
---
name: tadpole_datasets
align: center
width: 100%
---
**TADPOLE Challenge datasets.** See the [TADPOLE website for more information](https://tadpole.grand-challenge.org/data/).
```

We also split D1 into training/testing data for a leaderboard at PyCon UK 2017 Alzheimer's Hackathon:

- **`LB1_LB2`: Longitudinal training set** <br/>
Longitudinal measurements (i.e. over multiple visits) with associated outcomes (i.e. labelled training set) compiled from the entire ADNI history. Contains all individuals that have provided data in at least two visits (different dates) across ADNI1, ADNI GO and ADNI2 **up until May 2010**. Data from sources such as MR & PET imaging, cognitive tests, CSF biomarkers and clinical assessment have been processed using standard ADNI data pipelines.<br/>
Individuals flagged under the `LB2` column are rollover individuals who were invited to participate in ADNI3. This is the population for whom TADPOLE predictions should be made, but the PyCon UK hackathon leaderboard data can also be used in this summer school project.
- **`LB4`: Longitudinal held-out test set** <br/>
Longitudinal measurements for visits for LB2 patients **from May 2010 onwards**.


## TADPOLE Submission Types

There are two ways to enter the TADPOLE Grand Challenge: 
a [simple entry](https://grand-challenge-public-prod.s3.amazonaws.com/f/challenge/141/3c45a2b2-7480-4426-8971-f0cd4f5c72cf/TADPOLE_Simple_Submission_TeamName.xlsx) or a 
[full entry](https://grand-challenge-public-prod.s3.amazonaws.com/f/challenge/141/8a6be549-c835-414c-9de3-bb2e5e4af2d2/TADPOLE_Submission_TeamName.xlsx).

**Simple entry:** Submit a month-by-month forecast on at least one of the outcome variables (clinical status, ADAS13 or ventrical volume), using any training data or prediction sets.

**Full entry:** Submit a month-by-month forecast of all three outcome variables, optionally using any "custom" (i.e. constructed by the participant) training or prediction data sets. Full entries should provide two sets of forecasts using the standard TADPOLE data sets only (i.e. D1 for training, and a separate forecast for each of the D2 and D3 prediction sets), and optionally an additional forecast only if using custom datasets.

## Evaluation of forecasts

Once you're ready to "submit" your forecasts, you can evaluate them locally (rather than submit to the actual challenge) using [evalOneSubmissionD4.py](https://github.com/noxtoby/TADPOLE/blob/master/evaluation/evalOneSubmissionD4.py) from the TADPOLE GitHub repository.

