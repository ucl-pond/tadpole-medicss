# TADPOLE Challenge project at MedICSS

Self-contained background information and Jupyter notebooks for the UCL Medical Image Computing Summer School (MedICSS) project on The Alzheimer's Disease Prediction Of Longitudinal Evolution (TADPOLE) Challenge.

This page contains information for project organisers who wish to contribute content.

## Structure

The site is built using [Jupyter Book](https://jupyterbook.org/).

To add your Markdown & Jupyter files, add them within the `pages` folder, and link them from the `_toc.yml` file so that they appear in the website content.
Overall, you have :
- `pages/main` : overview of the summer school project
- `pages/notebooks` : Jupyter notebook(s) for the project
- `pages/other` : credits, etc.


### Other files
- `README.md` : this file
- `_toc.yml`, `_config.yml` : Jupyter book configuration files. Note that `_toc.yml` contains the structure of the website


## How to contribute

1. Clone the repo
```
git clone https://github.com/ucl-pond/tadpole-medicss
cd tadpole-medicss
```

2. Add/edit content

For example:
  - Add Python notebooks and markdown in the `pages` directory (and subdirectories).
  - Once added, edit the `_toc.yml` file to organize the website table of content accordingly.

Preferably fork the repo into your own GitHub account first, and always create your own branch to add/modify content before creating a pull request.

3. Build the website once you have added the notebooks

To check you materials and how they integrate within the website, run :
```
jupyter-book build ./
```
You can view and navigate the website locally by opening the `_build/html/index.html` file in your browser.

4. Add to the website online

Once you are satisfied with your changes, you can open a pull request so that administrators review your code and add it to the website

Note for administrators :
Github tracks the `_build` folder of the `gh-pages` branch. To push the static files to this branch, we use the `ghp-import` package.
To use it, you just have to run the following code :
```
ghp-import -n -p -f _build/html
```
