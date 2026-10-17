# Committed dataset

**Source dataset:** UCI Online Retail II — product pricing subset

**Selection:** All source transactions for the 25 most frequently appearing StockCodes in the first 50,000 source rows; original values and source order retained across both workbook sheets.

**Data license:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). This applies to the data, independently of the project code.

## Sources

- https://archive.ics.uci.edu/dataset/502/online+retail+ii

## CSV files

| File | Rows | Bytes |
|---|---:|---:|
| [retail_pricing_products.csv](raw/retail_pricing_products.csv) | 49,894 | 4,561,569 |

Attribution: Daqing Chen / UCI. Replaces the originally proposed research-restricted Dominick's source. This is an observational purchase table, not a randomized pricing experiment or a complete product-availability log. Prices are observed; margins/costs and unobserved demand require explicit assumptions. Product selection uses the initial source rows and does not inspect future price outcomes. Selected StockCodes: 20914, 21034, 21181, 21212, 21232, 21479, 21485, 21527, 21733, 21843, 22086, 22111, 22112, 22114, 22125, 22138, 22139, 72756, 79323W, 82482, 84029E, 84029G, 84879, 85099B, 85123A

The CSV files contain published observations or their documented format conversion; no training records were invented. Source formats and raw CSV exports are distinguished by the manifest. File checksums and schemas are recorded in [csv-manifest.json](csv-manifest.json).
