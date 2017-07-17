# Project-1-Basic-Data-Manipulation
Project: Data Wrangling Exercise 1: Basic Data Manipulation 

1: Clean up brand names
Clean up the 'company' column so all of the misspellings of the brand names are standardized. For example, you can transform the values in the column to be: philips, akzo, van houten and unilever (all lowercase).

CODE
refine_original <-transform(refine_original, company=tolower(company))

2: Separate product code and number
Separate the product code and product number into separate columns i.e. add two new columns called product_code and product_number, containing the product code and number respectively

CODE
refine_original <-separate(refine_original, Product.code...number, c("product_code", "product__number"), sep = "-")
