# Evaluation-of-templates-for-requirements-documentation 

This repository contains data and code related to experimentation on a compartive evaluation of different template notations for requirements documentation in semi-formal natural language.

## Summary of Artifact 

The repository contains different artifacts:

- A corpus of natural language requirements from five different projects in different domains (249 requirements):
  - The "FLEX" requirements document is a system level specifiaction from a space flight/satellite project from ESA. 
  - The "CS E 50" requirements document (Certification Specifications for Engines) is an EASA standard related to the aviation/aerospace domain.  
  - The "ECSS E60-30" requirements document is an ECSS standard from the aerospace domain.  
  - The "TSS (Time Sheet System)" requirements document specifies a work hour management system for student reasearch assistents at universities. (The requirements loosely follow the MASTeR Templates)  
  - The "EVS (Electronic Voting System)" requirements document specifies a system for electronic polls in the university context. (The requirements loosely follow the MASTeR Templates)
  - Each of the above requirements sets rephrased into five different template notations respectively
    - "Easy Approach to Requirements Syntax (EARS)"
    - "Mustergültige Anforderungen - Das SOPHIST Templates für Requirements (MASTeR)"
    - "Advanced-EARS"
    - "Bolierplates" (DODT)
    - SPIDER
   - The requirement lists do *not* contain any additional project information or traceability liks
- A metric suite with metrics to measure quality factors relevant to compare requirement template performance
  -  Metric definitions
  -  Tool support for metric calculation
  -  Calculated + manually evaluated metric values for the given requirement corpus
  -  Statistics and charts for metric analysis
- A corpus of two natural language requirements re-written by 43 test subjects following "Easy Approach to Requirements Syntax (EARS)" and "Mustergültige Anforderungen - Das SOPHIST Templates für Requirements (MASTeR)" respectively

## Description of Artifact 

The repository contains three folders: 

- Source: Python code (Quality metrics.ipynb) to evaluate 14 particular metrics, details under "Usage Instructions". 
- Data: contains the files with the actual data
  -  metric_definitions_and_results.pdf, detailed definition tables for quality metrics and data items, as well as underlying guideline rules (+ comparison of five phrasing guidelines) and results in effects sizes comparing the five template systems with free text.
  -  two sunburst diagrams "QualityAttributes.png" and "RulesPerGuideline.png" illustrating the attribution of evaluated metrics to quality attributes and the conformance to phrasing guidelines as described in "metric_definitions_and_results.pdf"
  - TemplateComparisonAnalytics.xlsx, the workbook contains several different data sheets
    - a sheet per document phrasing variant named after the document (FLEX, CS_E_50, ECSS_E60-30, TSS, EVS) and 5 random groups (Random1, ..)
	and the respective template System (free, EARS, MASTER, AdvEARS, boilerplates (DODT), SPIDER) 
	as "document name" + "template name" and one "Empty Sheet" as a template for extension. 
	Each such sheet contains
      - one row per requirement with its id, text and 54 assessed quality metrics, e.g., # counts and ? bools 1-positive/0-negative, (17 manually, 20 Excel formula, 17 by Python script from auxiliary file)
      - a header with 78 aggregated metrics for the whole requirement set, e.g., Σ sums and Ø averages (1 by Python script from auxiliary file, 12 manual from readability tool, 65 Excel formula)
    - "Summary" sheet summarizing the metrics per set in a comapartive overview together with averages and other statistical values   
    - "Summary effects" sheet summarizing the metrics effect sizes and significance per set in a comapartive overview
    - "radar charts" sheet containing 62 radar charts for all none-auxiliary metrics  
    - "all *" sheets that aggregate the header values over all requirements per notartion (free, EARS, MASTER, AdvEARS, boilerplates (DODT), SPIDER) 
    - "Reading box plots" sheet with box-and-whisker plots for readability metrics (with respectively re-arranged data from the summary sheet)
    - "Quality box plots" sheet with box-and-whisker plots for percentage-based quality metrics (with respectively re-arranged data from the summary sheet)
    - "Spearman Correl" sheet with a correlation matrix for spearman rank correlation over all metrics in the summary sheet (n=30, values significant at α=0.01 in green, α=0.05 in yellow)
    - "Pearson Correl" sheet with a correlation matrix for pearson correlation over all metrics in the summary sheet (significant values in green, however not applicable as most values are not normally distributed)
    - "Readability bar charts indiv" sheet with bar charts of readability metrics
    - "Readability bar charts all" sheet with aggregated bar charts of readability metrics
    - "Quality Line charts" sheet with line charts of percentage-based quality metrics
    - "Quality bar chart" sheet with bar charts of percentage-based quality metrics
    - and additional sheets with aggregated bar charts over all qualities per document (FLEX, CS_E_50, ECSS_E60-30, TSS, EVS)

  - TemplateComparison_calculatedMetrics.xlsx, an auxiliary file contains requirement quality metric results from the Python script
- UserTestEval: Application of the above described metric suite in Python/Excel to test subject written requirements. Contains again "Source" and "Data" folders with simplified versions of the above described script and .xlsx files (without random groups, sorted not by document but test subject background)
 


## System Requirements 

 
- Microsoft Ecxel 2016 or newer (for .xlsx files)  
- A PDF reader (for .pdf files) 
- Anaconda for Python (only for metric re-calculation) with the following libraries:
  - pandas 
  - numpy
  - NLTK
  - spaCy
  - Matcher
  - re
  - readability 
  - PassivePy
  - syllapy
  - stemming
  - quantulum3
 
## Installation Instructions 

Below, you will find links to instructions on how to install: 
- [Microsoft Office](https://support.microsoft.com/en-us/office/download-and-install-or-reinstall-microsoft-365-or-office-2021-on-a-pc-or-mac-4414eaaf-0478-48be-9c42-23adc4716658) 
- [Adobe Reader](https://helpx.adobe.com/acrobat/kb/install-reader-dc-windows.html)
- [Anaconda](https://docs.anaconda.com/anaconda/install/windows/) 
- [NLTK](https://www.nltk.org/install.html) 
- [spaCy](https://spacy.io/usage#installation) 
- [readability](https://pypi.org/project/readability/) 
- [PassivePy](https://pypi.org/project/PassivePy/)
- [syllapy](https://github.com/mholtzscher/syllapy)
- [stemming](https://pypi.org/project/stemming/)
- [quantulum3](https://github.com/nielstron/quantulum3)

## Usage Instructions 

The data within TemplateComparisonAnalytics.xlsx can be used to compare different template systems used to phrase the different variants of requirements documents among each other. It can be used to find differences and pecurlarities with respect to the metrics selected for the quality factors relevant for template systems.
Further, the data can also be used to validate these metrics and in particlar the guideline rules behind them, e.g., through analysis of dependencies among metrics.
The requirements samples can also be extracted and used for other analysis on the requirement texts. Similar, the metrics can also be used with other requirements, to extend the analysis. 

The following columns in "TemplateComparisonAnalytics.xlsx" are updated through workbook links from "TemplateComparison_calculatedMetrics.xlsx":

- "liability? (R5)"
- "#syllables" 
- "active_voice? (R8)"
- "definite_articles?  (R15)" 
- "no_nominalization? (R10)" 
- "no_comparison? (R13)" 
- "units? (R16)" 
- "no_vague_terms? (R17)" 
- "no_escape_clause? (R18)" 
- "no_open_end? (R19)" 
- "no_superfluous_infinitives? (R20)" 
- "no_negation? (R22)" 
- "no_combinators? (R24)" 
- "no_pronouns? (R28)" 
- "no_absolutes? (R30)" 
- "clear_quantifiers? (R34)"
- "value_tolerance? (R35)" 
- "F-Score"

The two files should be in the same folder. As Excel stores absolute paths, the workbooklinks in "TemplateComparisonAnalytics.xlsx" have to be refreshed after download (Data -> Workbook Links -> Refresh, select the "TemplateComparison_calculatedMetrics.xlsx" file at its new location). 

If requirements texts are changed/new ones added, “Quality metrics.ipynb” needs to be run to update these values. Follow "Steps to Reproduce" for this.

## Steps to Reproduce

To reproduce the whole experiment, 
1. Take the requirements from all "xxx free" sheets and rephrase them according to the respective template systems and enter these re-phrasings to the respective sheets (emptied before - despite formula).
2. The Excel formula-based metrics will be calculated automatically.
3. The 17 manual metrics (marked in italic) have to be evaluated by a human reviewer and filled with 0 or 1 respectively.
	- "structured_sentence?  (R6)"
	- "#process_verbs (R3)"
	- "approriate_level? (R7)"
	- "precise_verb? (R9)"
	- "no_light_verb? (R11)"
	- "clear_comparison? (R14)"
	- "correct_grammar? (R21)" (use external spell-checker)
	- "rationale_excluded? (R25)"
	- "no_groupnoun? (R27)"
	- "contextfree? (R29)"
	- "explicit_conditions? (R31)"
	- "condition_combination_clear? (R32)"
	- "solution_free? (R33)"
	- "atomic? (R36)"
	- "clear_preconditions? (R37)"
	- "clear_business_logic? (R38)"
	- "clear subject? (R39)"
4. Calculate the redability metrics with an external tool (e.g., [https://readabilityformulas.com](https://readabilityformulas.com)) and enter the results to the respective header cells named after the metric (again marked in italic). Copy for this the colum with the requirements texts and enter this input to the tool. 
5 In case of use of random group sheets, update the references to the respective randomly assigned requirements on the original phrasing sheets and also process 4. for these random group texts 
5. To calculate the remaining metrics with the Python script, follow the next steps:

File: “Quality metrics.ipynb” in the Source folder.

Input: The "TemplateComparisonAnalytics.xlsx" document in the Data folder. 

Output: The "TemplateComparison_calculatedMetrics.xlsx" document in the Data folder.

1. Open the “Quality metrics.ipynb” file in the jupyter notebook. 
2. Check the name of your document and excel name used in the pd.read_excel method. They should be equal. 
	Sheets after the Summary sheet will not be processed, for sheets "Randomxx" only F-Score is calculated. 
4. Run the code and check the generated TemplateComparison_calculatedMetrics.xlsx document. 
5. You do not need to copy the processed data to the original document. All evaluated data from "TemplateComparison_calculatedMetrics.xlsx" should be linked automatically to "TemplateComparisonAnalytics.xlsx". If not, refresh workbook links. For this, press Data -> Workbook Links -> Refresh. Both files should be in the same folder.
6. Check all 0 values in "TemplateComparison_calculatedMetrics.xlsx" for false positives, in particular "no_comparison? (R13)", "units? (R16)", "value_tolerance? (R35)", and "no_vague_terms? (R17)", and potentially manually change them to 1

Generally the same procedure applies for the data in "UserTestEval"
 

### Steps to extend the analysis 

If you want to extend the document and add more data for analysis, do the following:

- Clone a sheet from the "empty sheet" sheet of the TemplateComparisonAnalytics.xlsx document. 
- Give a meaningful name for the sheet. The presented document uses the following notation for this: "document name" + "template name". If requirements are written in a free form, "template name" is equal to "free". 
- Adjust references in links and formula to the new name (e.g., STRG+F)
- Add necessary requirements from the selected requirement document to the "Text" column: one requirement per row. 
- Fill the "ID" and "name_of_template" columns if appropriate for your comparison. 
- Assess the requirements for the presented quality metrics. 
- Assess the requirements for the presented readability score metrics if applicable.
- Adjust links and references in formula to sheet names on the summary sheets to get overview.
- Some metrics can be evaluated by python code. To learn how to do this, take a look above.
  - The respective sheet needs to be added also within the TemplateComparison_calculatedMetrics.xlsx document and the sheet name adapted in the workbook links on the sheet.

If you would like to evaluate more metrics via code, do the following: 

- Add a new function to the “Quality metrics.ipynb” file, which accepts a requirement text as a parameter. 
- Add an evaluated column header name to the cell 20 "# Excel sheet column names used for calculation" 
- Call this function in cell 21. 
- Add the processed column header name to the df.to_excel function in cell 22 to write it to the output file. 
- Add links to the corresponding cells between "TemplateComparison_calculatedMetrics.xlsx" and "TemplateComparisonAnalytics.xlsx" documents to automatically copy evaluated data to the "TemplateComparisonAnalytics.xlsx" document 

## License

Software under MIT License

Copyright (c) 2022-2023

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

All non-software data files within the project are published under the CC-BY 4.0 license (https://creativecommons.org/licenses/by/4.0/)
