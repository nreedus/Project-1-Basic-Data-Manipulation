# Project-1-Basic-Data-Manipulation
Project: Data Wrangling Exercise 1: Basic Data Manipulation 
1: Clean up brand names

Clean up the 'company' column so all of the misspellings of the brand names are standardized. For example, you can transform the values in the column to be: philips, akzo, van houten and unilever (all lowercase).

CODE

refine_original <-transform(refine_original, company=tolower(company))

