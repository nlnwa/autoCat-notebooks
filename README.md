# autoCat-notebooks
This repository contains Jupyter notebooks in development. They aim to automatically identify access categories for content in the Norwegian Web Archive, based on the current Legal Deposit Act and its legislative preparations.[^1]

The objective is to make as much of the collection as possible available to as many as possible, within the framework of copyright and privacy legislation.

## autoCat2
Identifying material with access category 2 means deciding if a website has declared responsible editorship. This is not declared in structured metadata, but can often be found in semantic information and semiotics. Thus, it can be identified with computation analysis of the content.

The autoCat2 notebook currently:
- loads WARC files
- extracts HTML from WARC
- filters front pages
- look for regular expressions in texts ("Ansvarlig redaktør" and similar)
- look for regular expressions in links ("https://nored.no/Redaktoeransvar" and similar)
- calculates a confidence score for whether a front page has declared responsible editorship

### Test results (preliminary)
Running the script on a test set with 300 front pages of Norwegian news websites, autoCat2 v0.2 has proved quite good results:
83%  correct classifications
14%  uncertain
 3%  false negatives
 0%  false positives

From the sample, the cause of uncertainty was usually that information partly where published on other pages than the front page (often in a "about.html"), in dynamic content (.js) or in semiotics. It indicate how the current approach is HTML- and text-centric, and would benefit from another iteration, taking into account different sources and forms of declarations.

### Disclaimer
The current version of autoCat2 (v0.2) is a second iteration of automatic classification. Calculation of confidence score is still somewhat naïve.

### Running a notebook
Notebooks are interactive tools for computing, but they do not necessarily require computational expertise.
Basically, they contain a mix of explanatory text and code cells.
Text cells are written in Markdown, while code cells are written in Python.

To execute a code cell, you just have to make sure that it is marked, and then press <kbd>Shift</kbd> + <kbd>Enter</kbd>.

To read more about how you can work with and edit the notebooks, see our documentation for the [NWA Notebooks](https://nlnwa.github.io/research-services/docs/notebooks) or the [Jupyter Notebook documentation pages](https://jupyter-notebook.readthedocs.io/en/latest/).

## Footnotes

[^1]: Familie- og kulturkomiteen. (2015). “Innstilling fra familie- og kulturkomiteen om endringer i lov om avleveringsplikt for allment tilgjengelige dokumenter (innsamling av digitale dokumenter m.m.)” [Innst. 286 L – 2014-2015].
