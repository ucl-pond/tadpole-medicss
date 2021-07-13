# Background

AD, and dementia in general, is a key challenge for 21st century healthcare. The statistics are sobering: 7% of people over 65 and 20% over 80 suffer from dementia of which AD is the most common cause. Dementia has higher health and social care costs than cancer, stroke and chronic heart disease combined. These costs are projected to be \$1T in 2018 and \$2T in 2030. A treatment slowing progression by 50% would reduce annual care costs by about 10%, i.e., \$100B (2018 estimate).

No current treatments provably cure or even slow AD. Of the hundreds of clinical trials into putative treatments (often running to billions of dollars) fewer than 1% have proceeded to the regulatory approval stage and none have managed to prove a disease-modifying effect (including the latest among the handful of [approved drugs](https://www.alzforum.org/therapeutics/search?fda_statuses%5B%5D=184&target_types=&therapy_types=&conditions=&keywords-entry=&keywords=#results)). One key reason for these failures is difficulty in identifying patients at early stages of the disease where treatments are most likely to be effective.

TADPOLE challenges you to identify what data and algorithms best predict AD progression. This facilitates early identification of patients likely to be receptive to treatment, thus purifying cohorts for clinical trials, highlighting positive treatment effects, and facilitating translation of effective treatments to market.

## TADPOLE

Data science will play a key role in the endeavour to learn more about the causes of Alzheimer’s Disease, currently believed to be a combination of genetic and environmental factors. The goal of [The Alzheimer's Disease Prediction Of Longitudinal Evolution (TADPOLE) Challenge](https://tadpole.grand-challenge.org/) is to identify which people within an age group at risk of AD (Alzheimer's Disease) will start to show symptoms in the short to medium term (1-5 years). It focusses on "rollover individuals", i.e., patients coming from an earlier phase, in the Alzheimer's Disease Neuroimaging Initiative (ADNI) study. The challenge is to use historical measurements from these individuals to forecast future measurements. The following scientific questions motivate the challenge:

- How predictable is progression to AD in at-risk individuals?
- Which data, processing pipelines, and predictive models best predict future AD progression?
- Can we use such methods to improve cohort selection for clinical trials?

The TADPOLE datasets contain a list of individuals at an age that puts them at risk of AD, with associated measurements to inform forecasts (from imaging, psychology, demographics, genetics, etc.). Each individual has agreed to a follow-on assessment.

Your challenge is to predict future measurements from these individuals and submit your predictions for evaluation. The original challenge used future measurements for evaluating these forecasts (the data was not available until long after the original challenge submission deadline in Nov 2017), but this deadline has since passed and we will perform the actual evaluation during this summer school project.

To find out more about TADPOLE and current approaches to predicting AD, please see the [TADPOLE website](https://tadpole.grand-challenge.org/background/).

```{figure} ../../../../_static/img/Figure_TrainForecast_new.png
---
height: 150px
name: Logo
align: center
```

