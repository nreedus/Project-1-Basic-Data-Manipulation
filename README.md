# Project-1-Basic-Data-Manipulation
Project: Data Wrangling Exercise 1: Basic Data Manipulation 

1: Clean up brand names
Clean up the 'company' column so all of the misspellings of the brand names are standardized. For example, you can transform the values in the column to be: philips, akzo, van houten and unilever (all lowercase).

CODE:
refine_original <-transform(refine_original, company=tolower(company))
refine_original$company[refine_original$company=="Phillips"] <- "philips"
refine_original$company[refine_original$company=="phillips"] <- "philips"
refine_original$company[refine_original$company=="phllips"] <- "philips"
refine_original$company[refine_original$company=="akz0"] <- "akzo"
refine_original$company[refine_original$company=="ak zo"] <- "akzo"
refine_original$company[refine_original$company=="fillips"] <- "philips"
refine_original$company[refine_original$company=="phlips"] <- "philips"
refine_original$company[refine_original$company=="unilver"] <- "unilever"

2: Separate product code and number
Separate the product code and product number into separate columns i.e. add two new columns called product_code and product_number, containing the product code and number respectively

CODE
refine_original <-separate(refine_original, Product.code...number, c("product_code", "product__number"), sep = "-")

3: Add product categories

CODE:
refine_original <- mutate(refine_original, "product_category" = ifelse(product_code == "p", "Smartphone", "")) %>% mutate("product_category" = ifelse(product_code == "x", "Laptop", product_category)) %>% mutate("product_category" = ifelse(product_code == "q", "Tablet", product_category)) %>% mutate("product catagory" = ifelse(product_code == "v", "TV", product_category)) %>% mutate("product catagory" = ifelse(product_code == "v", "TV", product_category))

4: Add full address for geocoding

You'd like to view the customer information on a map. In order to do that, the addresses need to be in a form that can be easily geocoded. Create a new column full_address that concatenates the three address fields (address, city, country), separated by commas.

CODE
refine_original <-unite(refine_original, "full_address", address, city, country, sep = ",")

5: Create dummy variables for company and product category

Both the company name and product category are categorical variables i.e. they take only a fixed set of values. In order to use them in further analysis you need to create dummy variables. Create dummy binary variables for each of them with the prefix company_ and product_ i.e.,

    Add four binary (1 or 0) columns for company: company_philips, company_akzo, company_van_houten and company_unilever.
CODE:
    refine_original <-mutate(refine_original, company_philips = ifelse(company =="philips", 1, 0)) %>%
+     mutate(company_akzo = ifelse(company == "akzo", 1, 0)) %>%
+     mutate(company_van_houten = ifelse(company == "van_houten", 1, 0)) %>%
+     mutate(company_unilever = ifelse(company == "unilever", 1, 0))

    Add four binary (1 or 0) columns for product category: product_smartphone, product_tv, product_laptop and product_tablet.
