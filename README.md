![Network courtesy Ann Sizemore Blevins](img/repo_pic.png)

# Table of Contents

* [Diversity Statement and Code Notebook](https://github.com/dalejn/cleanBib#diversity-statement-and-code-notebook)

  - [Diversity statement template](https://github.com/dalejn/cleanBib#diversity-statement-template)

    + [Template](https://github.com/dalejn/cleanBib#template)

    + [Benchmark](https://github.com/dalejn/cleanBib#benchmark)

* [Instructions](https://github.com/dalejn/cleanBib#instructions)

  - [Input/output](https://github.com/dalejn/cleanBib#inputoutput)

* [FAQ](https://github.com/dalejn/cleanBib#faq)

* [Other Resources](https://github.com/dalejn/cleanBib#other-resources)

* [References](https://github.com/dalejn/cleanBib#references)

* [Contributors](https://github.com/dalejn/cleanBib#contributors)

* [Changelog](https://github.com/dalejn/cleanBib#changelog)

# Diversity Statement and Code Notebook

[![DOI](https://zenodo.org/badge/232916183.svg)](https://zenodo.org/badge/latestdoi/232916183)

Motivated from work by [J. D. Dworkin, K. A. Linn, E. G. Teich, P. Zurn, R. T. Shinohara, and D. S. Bassett (2020). bioRxiv. doi: https://doi.org/10.1101/2020.01.03.894378](https://www.biorxiv.org/content/10.1101/2020.01.03.894378v1.full.pdf)

For `.pdf` and `.tex` templates of the statement, see the `/diversityStatement` directory in this repository.

A `.bib` file containing the references used in the statement can be found in `/diversityStatement/bibfile.bib`

## Diversity statement template

### Template

> Recent work in several fields of science has identified a bias in citation practices such that papers from women and other minorities are under-cited relative to the number of such papers in the field [1, 2, 3, 4, 5]. Here we sought to proactively consider choosing references that reflect the diversity of the field in thought, form of contribution, gender, and other factors. We obtained predicted gender of the first and last author of each reference by using databases that store the probability of a name being carried by a woman [5, 6]. By this measure (and excluding self-citations to the first and last authors of our current paper), our references contain `A`% woman(first)/woman(last), `B`% man/woman, `C`% woman/man, `D`% man/man, and `E`% unknown categorization. This method is limited in that a) names, pronouns, and social media profiles used to construct the databases may not, in every case, be indicative of gender identity and b) it cannot account for intersex, non-binary, or transgender people. We look forward to future work that could help us to better understand how to support equitable practices in science.

### Benchmark

For the top 5 neuroscience journals (Nature Neuroscience, Neuron, Brain, Journal of Neuroscience, and Neuroimage), the expected gender proportions in reference lists as reported by [Dworkin et al.](https://www.biorxiv.org/content/10.1101/2020.01.03.894378v1.full.pdf) are 6.7% for woman(first)/woman(last), 9.4% for man/woman, 25.5% for woman/man, and 58.4% for man/man. Expected proportions were calculated by randomly sampling papers from 28,505 articles in the 5 journals, estimating gender breakdowns using probabilistic name classification tools, and regressing for relevant article variables like publication date, journal, number of authors, review article or not, and first-/last-author seniority. See [Dworkin et al.](https://www.biorxiv.org/content/10.1101/2020.01.03.894378v1.full.pdf) for more details. 

# Instructions

The goal of the coding notebook is to clean your `.bib` file to only contain references that you have cited in your manuscript. This cleaned `.bib` will then be used to generate a data table of full first names that will be used to query the probabilistic gender classifier, [Gender API](https://gender-api.com). Proportions of the predicted gender for first and last author pairs (man/man, man/woman, woman/man, and woman/woman) will be calculated. 

1. Obtain a `.bib` file of your manuscript's reference list. You can do this with common reference managers. __Please export your .bib in an output style that uses full first names (rather than only first initials) and using the full author lists (rather than abbreviated author lists with "et al.").__

   * [Export `.bib` from Mendeley](https://blog.mendeley.com/2011/10/25/howto-use-mendeley-to-create-citations-using-latex-and-bibtex/)
   * [Export `.bib` from Zotero](https://libguides.mit.edu/ld.php?content_id=34248570)
   * [Export `.bib` from EndNote](https://www.reed.edu/cis/help/LaTeX/EndNote.html). Note: Please export full first names by either [choosing an output style that does so by default (e.g. in MLA style)](https://canterbury.libguides.com/endnote/basics-output) or by [customizing an output style.](http://bibliotek.usn.no/cite-and-write/endnote/how-to-use/how-to-show-the-author-s-full-name-in-the-reference-list-article185897-28181.html)
   * [Export `.bib` from Read Cube Papers](https://support.papersapp.com/support/solutions/articles/30000024634-how-can-i-export-references-from-readcube-papers-)

2. Launch the coding environment. Please refresh the page if the Binder does not load after 5-10 mins.

    [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/dalejn/cleanBib/master)

3. Open the notebook `cleanBib.ipynb`. Follow the instructions above each code block. It can take 10 minutes to 1 hour complete all of the instructions, depending on the state and size of your `.bib` file. We expect that the most time-consuming step will be manually modifying the `.bib` file to find missing author names, fill incomplete entries, and fix formatting errors. These problems arise because automated methods of reference mangagers and Google Scholar sometimes can not retrieve full information, for example if some journals only provide an author's first initial instead of their full first name.

## Input/output

| Input                 | Output                                                                                                                        |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------|
| `.bib` file(s)**(REQUIRED)**    | `cleanBib.csv`: table of author first names, titles, and .bib keys                                                            |
| `.aux` file (OPTIONAL)| `Authors.csv`: table of author first names, estimated gender classification, and confidence                                   |
| `.tex` file (OPTIONAL)| `yourTexFile_gendercolor.tex`: your `.tex` file modified to compile .pdf with in-line citations colored-coded by gender pairs |

![Color-coded .tex file, Eli Cornblath](img/texColors.png)

# FAQ

* Why do I receive an error when running the code?
  * The most common errors are due to misformatted .bib files. Errors will usually provide an indication of the line or type of problem in the .bib file. They will require you to manually correct the `.bib` file of formatting errors or incomplete entries. After editing the `.bib` file, try re-running the code block that gave you the error. If you cannot resolve an error, please open an `issue`, paste the error text or a screenshot of the error, and attach the files that you used so that we can reproduce the error. We will try to help resolve it.
* What should I do if the Binder crashes, times out, or takes very long to launch?
  * Please refresh the Binder or re-launch from our step 2 instruction upon a crash. This has often resolved the issue. The environment will time out if you are inactive for over 10 minutes (but leaving the window open counts as activity). Long launch times can be due to a recent patch by us (temporary slow-down from re-building the Docker image) or heavy load on the server. Please try again at a later time. Please refer to the [Binder User Guide](https://mybinder.readthedocs.io/en/latest/index.html) and [FAQ](https://mybinder.readthedocs.io/en/latest/index.html) for other questions.
* Will this method work on non-Western names?
  * Yes, the [Gender API supports 177 countries](https://gender-api.com/en/frequently-asked-questions?gclid=Cj0KCQiAmZDxBRDIARIsABnkbYTy9MHmGoR2uBhxEKANbT9B9EFVOSiRzbGeQi7nUn6ODH83s6-RZKwaAjpZEALw_wcB#which-countries-are-supported) but will classify genders with varying confidence. 
* Are self-citations included?
  * We do not include self-citations by default because we seek to measure engagement with and citation of other researchers' work. We define self-citations as those including your first or last author as a co-author. 
* What if a reference has only 1 author?
  * We count that author as both the first and last author.
* What if a reference has more than 1 first author or last author?
  * We do not automatically account for these cases. If you are aware of papers with co-first or co-last authors, then you could manually add duplicate entries for each co-first or co-last author so that they are double-counted.
* What about gender-neutral names?
  * We exclude names that cannot be classified with >70% confidence. These are reported in the `Diversity Statement` as "unknown." 
* Should I include the diversity statement references in the gender proportion calculation?
  * Please do not include the diversity statement references. The descriptive statistic of primary interest is of your citation practices.
* What is a `.bib` file?
  * The `.bib` file is a bibliography with tagged entry fields used by LaTeX to format a typesetted manuscript's reference list and its in-line citations. If you are not using LaTeX to write your manuscript, common reference managers that are linked to Microsoft Word or Google Docs also allow you to export `.bib` files (See Instructions, Step 1).
* What is an `.aux` file?
  * The `.aux` file is generated when you compile the `.tex` file to build your manuscript. It is linked to the `.bib` file(s) used to populate your manuscript's reference list and records the citations used.
* I have an idea to advance this project, suggestions about how to improve the notebook, and/or found a bug. Can I contribute?
  * Yes, please open an `issue` or `pull request`. We welcome feedback on any pain points in running this code notebook. If you contribute, please modify the `README.md` to credit yourself alphabetically in the `Contributors` section in the `pull request`. 

# Other Resources

* [Gender base-rates of neuroscience](https://biaswatchneuro.com/base-rates/neuroscience-base-rates/), based on a poll of SfN attendees from 2014-2018, categorized by subject area.

* A [list highlighting woman neuroscientists](https://anneslist.net/). Categorized by subject area and seniority. 

# References

> [1] S. M. Mitchell, S. Lange, and H. Brus, “Gendered citation patterns in international relations journals,” International Studies Perspectives, vol. 14, no. 4, pp. 485–492, 2013.

> [2] D. Maliniak, R. Powers, and B. F. Walter, “The gender citation gap in international relations,” International Organization, vol. 67, no. 4, pp. 889– 922, 2013.

> [3] N. Caplar, S. Tacchella, and S. Birrer, “Quantitative evaluation of gender bias in astronomical publications from citation counts,” Nature Astronomy, vol. 1, no. 6, p. 0141, 2017.

> [4] M. L. Dion, J. L. Sumner, and S. M. Mitchell, “Gendered citation patterns across political science and social science methodology fields,” Political Analysis, vol. 26, no. 3, pp. 312–327, 2018.

> [5] J. D. Dworkin, K. A. Linn, E. G. Teich, P. Zurn, R. T. Shinohara, and D. S. Bassett, “The extent and drivers of gender imbalance in neuroscience reference lists,” bioRxiv, 2020.

> [6] D. Zhou, E. J. Cornblath, J. Stiso, E. G. Teich, J. D. Dworkin, A. S. Blevins, and D. S. Bassett, “Gender diversity statement and code notebook v1.0,” Feb. 2020.

# Contributors
(alphabetical)

* Ann Sizemore Blevins
* Eli Cornblath
* Jordan Dworkin
* Jeni Stiso
* Erin Teich
* Dale Zhou

# Changelog

* __6/12/2020__
  * modify statement, references, and acknowledgment of limitations

* __5/19/2020__
  * fix typos in readme
  * typo in warning for editing .bib instead of cleanedBib.csv
  * add flush.console() to give progress index for R code
  * added code to handle case one of the main gender pair categories has 0 references
  * add a savepoint for Authors.csv in codeblock for API query rather than just at the end
  * fix unknown category rounding
  * add extra escape backslashes to printed LaTeX template statement
  * changed to man/woman

* __5/1/2020__
  * fix bug with round function
  * add more informative string outputs to descriptive statistics code
  * add code to automatically output a template to copy-and-paste in both plain text and LaTeX with the percentages filled in
  * simplified instructions for descriptive statistics code
  * updated FAQ

* __4/9/2020__
  * fix bug with entry ID string matching for optional aux route, changed to regex
  * fix bug with duplicate check for optional aux route
  * added code to auto-remove the 7 references included in the diversity statement
  * add more descriptive instructions for the last section generating tables and comparing against benchmark
  * updated FAQ

* __3/16/2020__
  * fix bug with CrossRef title confirmation
  * add to README instructions on exporting .bib with a style that includes full first author (not just initials) when possible
  * added a sleep timer for CrossRef API queries
  * added another self-citation check from the CrossRef search results

* __2/17/2020__
  * streamlined instructions
  * added repository photo for social media (thanks, Ann!)
  * move instructions into Jupyter notebook
  * added code to automatically remove unused .bib entries instead of needing user to manually remove them (thanks, Eli and Erin!)
  * made removing self-citations default
  * added FAQ
  * added screenshots to instructions
  * added error message to request users remove entries with duplicate IDs. Not automated in case duplicate entry key refers to different references.
  * throw error if entries are incomplete or blank
  * fixed handling of optional middle initial correctly for self-citations
  * added SOS notebook support to put all code and instructions into 1 notebook so users don't have to manually change kernel
  * added optional entry for co-first or co-last authors
  * added optional code block to color-code `.tex` file's citation keys by gender pair classifications
  * added code to search `Crossref` API to automatically complete some incomplete `.bib` entries (thanks, Jeni!)
  * add another self-citation check after manual editing

* __1/19/2020__ 
  * added code to output a column with article titles to make it easier to manually search which bib entries need manual editing
  * added code to output another column that optionally checks for self-citations
