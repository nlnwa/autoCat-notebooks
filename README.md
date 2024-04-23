# autoCat-notebooks
This repository contains Jupyter notebooks to automatically identify the access category of material in the Norwegian Web Archive collection, in accordance with the Legal Deposit Act and legislative preparations.[^1]

The objective of automatic classification is to enable role-based access to different parts of the collection, offering access to as much of our collection as possible, to as many as possible, within the limits of copyright and personal data restrictions.

## autoCat2
autoCat2 is used to identify material falling in category 2, meaning websites with a responsible editor. Typically, these are news sites and webzines that have declared editorial responsibilty, and therefore are regarded as part of the public sphere with information that are widely known.

The notebook includes code to:
- load WARC files
- parse HTML from WARC
- filter front pages
- identify text with regex ("Ansvarlig redaktør" and similar)
- identify links with regex ("nored.no/Redaktorplakaten" and similar)
- assign a confidence score (indicating the probability of a domain being in category 2)

### Preliminary test results
When run on a test set of 300 html files from front page, the script proved quite good results:
- 83% correct classifications,
- 14% flagged as uncertain (conf_score 0.3-0.7),
- 3% false negatives
- 0% false positives

Domain flagged as uncertain and the false negatives all related to sites declaring this information in dynamic content (.js) and/or on a about page. This is a known limitation of the current version of the script, and reflects its focus on html and front pages.

### Requirements
Jupyter notebook with Python 3.8 or later, and installing the following packages:

- **warcio**: `pip install warcio`
- **pandas**: `pip install pandas`
- **openpyxl**: `pip install openpyxl`

## Footnotes
[^1]: Legal Deposit Act of 19 June 2015 https://lovdata.no/dokument/NL/lov/1989-06-09-32/%C2%A74b#%C2%A74b; Familie- og kulturkomiteen. (2015). “Innstilling fra familie- og kulturkomiteen om endringer i lov om avleveringsplikt for allment tilgjengelige dokumenter (innsamling av digitale dokumenter m.m.)” [Innst. 286 L – 2014-2015]. 
