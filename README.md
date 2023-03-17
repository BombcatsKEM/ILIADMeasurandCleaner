# ILIADMeasurandCleaner

This repo contains the code that we used to refine the *measurands* we use in ILIAD for the CV-22 project. The ultimate goal of this work was to make the *measurands* inherently more meaningful than the original values we had been using.

# Overview of Process

1. Export to *Excel* the `measurands` table from the *Microsoft Access* database used by ILIAD.

1. Extract all of the significant words from the `description` field.

1. Consolidate this list of *significant descriptor words* to remove any duplicates.

1. For each *significant descriptor word*, assign a meaningful, intuitive abbreviation.

1. Run the `R` code in this repo, which performs the following steps.

   1. For each row in the `measurands` table, perform a RegEx search using each *significant descriptor word*.
   
   1. If a match is found, replace the *significant descriptor word* with its assigned abbreviation to which
      a `_` character has been added to the beginning and ending of the word.
      
   1. After all rows have been tested, scan through the list of *preliminary measurand replacements*. If a `_`
      character is located at either the beginning or ending of a *preliminary measurand replacement* string, remove it.
      
   1. Verify that the set of *preliminary measurand replacement* terms are unique. If `TRUE`, proceed to the next step.

   1. For each existing `measurand` value in the `measurands` table, update the corresponding record with its
      *measurand replacement* value.
