# Evaluation-of-templates-for-requirements-documentation 

## Description of Corpus 

To check the requirements documents quality and human readability, five documents from different domains were selected for assessment: 

- The "FLEX" requirements document is related to the aerospace domain. 

- The "CS E 50" requirements document is related to the aerospace domain. 

- The "ECSS E60-30" requirements document is related to the aerospace domain. 

- The "TSS (Time Sheet System)" requirements document. The TSS requirements are written to develop a system to track working hours, vacation, illness, etc. of employees with a monthly income below a certain amount (currently 850) in the university context. This document was written with the help of the MASTeR template. 

- The "EVS (Electronic Voting Sys)" requirements document. The EVS requirements are written to develop a system for electronic polls in the university context. This document was written with the help of the MASTeR template. 

 

These requirements documents can be found in the "TemplateComparisonAnalytics.xlsx" file inside the Data folder, which contains: 

- A requirement written in Natural Language (NL) in English. 

- Transformed requirements written with the selected template systems based on the corresponding NL requirement. 

- Assessed quality metrics. 

- Assessed readability metrics using the Readability Formulas web tool. 

- Summary (average) of the assessed quality metric values. 

- Graphs to analyze selected template systems. 

 

The "TemplateComparisonAnalytics.xlsx" document description is presented below: 

- The document has several sheets. Each corresponds to a particular template system of a particular document. The document uses the following notation for sheet names: "document name" + "template name". If requirements are written in a free form, "template name" is equal to "free". 

- Each template sheet has the following information: 

  - Most quality metric names have keywords in brackets, which refers to a corresponding quality document and quality number inside that document. 

  - Some metrics have the question mark at the end (e.g., "no_open_end? (IR9)"). This means true/false questions. Put "1" to the corresponding cell if the answer to the presented question is positive and "0" - if negative. 

  - Some columns have preset "0" in their cells. This means that values for the corresponding metrics are calculated automatically using EXCEL formulas. 

  - Some metrics have "#" in the beginning (e.g., "#letters"). They are related to syntactic assessment. Most of the metrics are evaluated automatically using EXCEL formulas. tool. 

  - Some metrics can be evaluated automatically using Python code. The code can be found in the “Quality metrics.ipynb” file. 

  - The sheet also contains columns for readability score metrics. The metrics used in the evaluation are accessed per the entire document and not per a separate requirement. So, the results are added to the Summary sheet directly. Some readability score metrics might be accessed per requirement. 

- Summary sheet contains aggregated information from the sheets with assessed requirements, except readability metrics: 

- Most metrics, except readability metrics, have references to summary values from other sheets. You do not need to copy-paste the values. If some values are updated in corresponding sheets, values are updated automatically in the Summary sheet. 

- To add more documents and/or templates for comparison, it is necessary to add them to the Summary sheet with references to corresponding sheets. 

 

## Steps to extend the "TemplateComparisonAnalytics" document 

If you want to extend the document and add more data for analysis, do the following:

- Clone a sheet from the "ReqSet Template" sheet of the TemplateComparisonAnalytics.xlsx document. 

- Give a meaningful name for the sheet. The presented document uses the following notation for 

this: "document name" + "template name". If requirements are written in a free form, "template name" is equal to "free". 

- Add necessary requirements from the selected requirement document to the "Text" column: one requirement per row. 

- Fill the "ID" and "name_of_template" columns if appropriate for your comparison. 

- Assess the requirements for the presented quality metrics. 

- Assess the requirements for the presented readability score metrics if applicable.

- Some metrics can be evaluated by python code. To learn how to do this, take a look at the "How to evaluate particular quality metrics with python code" section.

 
## Steps to extend the analysis 

- Each chart is based on data from the Summary sheet. So, if the Summary data is updated, charts will be updated automatically. 

- When more templates or documents are added, it is necessary to add series manually. 

- Final readability and quality tables are based on the data from the Summary sheet, but not directly connected. So, if the Summary data is updated, it is necessary to update tables manually. 

Requirements do not contain unnecessary information, such as examples or comments. Requirements are autonomous and thus they do have links with the textual segments which precede or follow them. 

## How to evaluate particular quality metrics with python code

In the Source folder, there is a python code to evaluate particular quality metrics. The processed metrics have the following header in the "TemplateComparisonAnalytics.xlsx" document: 

- "#syllables" 

- "definite_articles?  (IR5,SR10-11)" 

- "no_nominalization? (SR3)" 

- "no_comparison? (SR8,Rupp09)" 

- "clear_comparison? (SR8)" 

- "units? (IR6)" 

- "no_vague_terms? (IR7,SR2+12,E106)" 

- "no_escape_clause? (IR8)" 

- "no_open_end? (IR9)" 

- "no_superfluous_infinitives? (IR10)" 

- "no_negation? (IR16,E106)" 

- "no_combinators? (IR19,SR9,E106)" 

- "no_pronouns? (IR24)" 

- "no_absolutes? (IR26)" 

- "clear_quantifiers? (IR32+34,SR8+10-11,E106)" 

- F-Score

File: “Quality metrics.ipynb” in the Source folder.

Input: The "TemplateComparisonAnalytics.xlsx" document in the Data folder. 

Output: The "TemplateComparison_calculatedMetrics.xlsx" document in the Data folder. 

- Open the “Quality metrics.ipynb” file in the jupyter notebook. 

- Check the name of your document and excel name used in the pd.read_excel method. They should be equal. 

- Sheets after the Summary sheet will not be processed. 

- Run the code and check the generated TemplateComparison_calculatedMetrics.xlsx document. 

- You do not need to copy the processed data to the original document. All evaluated data from "TemplateComparison_calculatedMetrics.xlsx" should be linked automatically to "TemplateComparisonAnalytics.xlsx". If not, refresh workbook links. For this, press Data -> Workbook Links -> Refresh. Both files should be in the same folder.


If you would like to evaluate more metrics via code, do the following: 

- Add a new function to the “Quality metrics.ipynb” file, which accepts a requirement text as a parameter. 

- Add an evaluated column header name to the cell 20 "# Excel sheet column names used for calculation" 

- Call this function in cell 21. 

- Add the processed column header name to the df.to_excel function in cell 22 to write it to the output file. 

- Add links to the corresponding cells between "TemplateComparison_calculatedMetrics.xlsx" and "TemplateComparisonAnalytics.xlsx" documents to automatically copy evaluated data to the "TemplateComparisonAnalytics.xlsx" document 

