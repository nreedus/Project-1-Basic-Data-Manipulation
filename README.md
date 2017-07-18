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

4: Add full address for geocoding

You'd like to view the customer information on a map. In order to do that, the addresses need to be in a form that can be easily geocoded. Create a new column full_address that concatenates the three address fields (address, city, country), separated by commas.

CODE
refine_original <-unite(refine_original, "full_address", address, city, country, sep = ",")
