
`template` package
------------------

### Generic template for research projects structured as R packages (adapted from Pakillo/template)

[![Travis-CI Build Status](https://travis-ci.org/Pakillo/template.svg?branch=master)](https://travis-ci.org/Pakillo/template)

[Rmarkdown](http://rmarkdown.rstudio.com/index.html) documents are great to keep reproducible scientific workflows, tightly integrating code, results and text. I keep a collection of Rmarkdown templates (including some for writing scientific articles, or manuscript reviews) [here](https://github.com/Pakillo/rmdTemplates).

Once we are dealing with more complicated data analysis, and writing custom code and functions for a research project, structuring our project as an [R package](http://r-pkgs.had.co.nz/) can bring many advantages (e.g. see [here](http://rmflight.github.io/posts/2014/07/analyses_as_packages.html) and [here](https://github.com/ropensci/rrrpkg)).

Hence this package works as a template for new research projects, with the idea of having everything (data, R scripts, functions and manuscripts reporting results) self-contained in the same package (a "research compendium") to facilitate collaboration and promote reproducibility.

A short presentation introducing this approach on 'Structuring data analysis projects as R packages' is available here: <https://github.com/Pakillo/template/blob/master/slides/Projects_as_Packages.pdf>

### Installation

``` r
library("devtools")
install_github("sirusb/template")
```

### Usage

1.  First, load the package

``` r
library("template")
```

1.  Now run the function `new_project` to create a directory with all the scaffolding (slightly modified from R package structure). For example, to start a new project about tree growth, just use:

``` r
new_project("treegrowth")
```

If you want to create a GitHub repository for the project at the same time, use instead:

``` r
new_project("treegrowth", github = TRUE, private.repo = FALSE, travis = TRUE)
```

This will create a new folder with this structure:

![](http://i.imgur.com/4BuMkCc.png?1)

Note that to create a GitHub repo you will need to have configured your system as explained in <http://www.rdocumentation.org/packages/devtools/functions/use_github>. And for Travis to run you will need to activate it at <https://travis-ci.org/profile>.

### Developing the project

1.  Now edit `README.Rmd` and the `DESCRIPTION` file with some basic information about your project: title, brief description, licence, package dependencies, etc. You may also check that project options in Rstudio are fine for you.

2.  Place original (raw) data in `data-raw` folder. Save all R scripts used for data preparation in the same folder.

3.  Save final (clean, tidy) datasets in the `data` folder. You may save them as plain text (txt, csv) or `rda` format (using `save`, `saveRDS` or `devtools::use_data`). You may write documentation for these data (see <http://r-pkgs.had.co.nz/data.html#documenting-data>).

4.  R scripts or Rmarkdown documents used for data analyses may be placed at the `analyses` folder. The final manuscript/report may be placed at the `manuscript` folder. You may want to use an Rmarkdown template from e.g. [rmdTemplates](https://github.com/Pakillo/rmdTemplates) or [rticles](https://github.com/rstudio/rticles).

5.  If your analyses use functions from other CRAN packages, include them as dependencies (`Imports`) in the `DESCRIPTION` file. Also use `Roxygen` `@import` or `@importFrom` in function definitions to import these dependencies in the namespace.

6.  If you write custom functions, place them in the `R` folder. Document all your functions with `Roxygen` (see <http://r-pkgs.had.co.nz/man.html>). Write tests for your functions (see <http://r-pkgs.had.co.nz/tests.html>) and place them in the `tests` folder.

7.  Write a `makefile` or master script to organise and execute all parts of the analysis. Render Rmarkdown reports using `rmarkdown::render`, and use Rstudio `Build` menu to create/update documentation, run tests, build package, etc.

8.  Save all the figures to the `figures` folder. You can create sub-directories inside to keep it organized.

9. Save the ppt reports to the `reports` folder.

8.  Share.

### Thanks to:

-   Carl Boettiger and his [template package](https://github.com/cboettig/template)
-   Jeff Hollister and his [manuscriptPackage](https://github.com/jhollist/manuscriptPackage)
-   Robert Flight: <http://rmflight.github.io/posts/2014/07/analyses_as_packages.html>
-   Hadley Wickham: <http://r-pkgs.had.co.nz/>
-   Yihui Xie: <http://yihui.name/knitr/>
-   Rstudio

### Links

-   <https://github.com/ropensci/rrrpkg>
-   <https://github.com/Reproducible-Science-Curriculum/rr-init>
-   <http://ropensci.github.io/reproducibility-guide/>
