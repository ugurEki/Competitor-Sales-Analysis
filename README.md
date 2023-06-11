# Competitor Sales Analysis in Power BI

This project aims to provide a comprehensive sales analysis report for Sintec(fictional manufacturing company). The report focuses on not only Sintec's internal performance but also analyze the sales and market share of its top competitors. 


# Methodology

To do this project, we will use Power BI which is a powerful business intelligence tool. Power BI allows us to connect, transform and visualize data from multiple sources and enable us to create interactive and nice reports/dashboards.

This project will involve the following steps :

1. <b>Data Preparation :</b> We will gather the necessary data for Sintec and its competitors. The data will be cleaned, transformed and prepared for analysis in Power BI. ( Data type checks, missing values, split columns, transpose, merging tables and others )
3. <b>Data Exploration :</b> We will conduct a comprehensive analysis of Sintec's performance and its competitors's sales and market share. We will identify key trends, patterns and business insights to aid decision-making.
4. <b>Dashboard : </b> Using Power BI's interface, we will design a visually appealing and user-friendly sales analysis report. This report combine various charts, tables and visualizations to present the data effectively.

## 1. Data Preparation
* In this section, I loaded Sales.csv, bi_dimensions.xlsx( Tables : Products, Geography, Manufacturer ), International Sales Folder ( Canada.csv, Germany.csv, Japan.csv, Nigeria.csv )
* In these files, I did the following operations :
1. Data type checks of each columns such as I changed the zip code from the number to the text in Sales.csv

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/7e645ae1-5f13-4f7c-9aa5-6af26bf61ecd)

2. I challenged the missing values such as Category column in the Products table, In the Ribbon Transform menu, I clicked the Fill - Down button to fill missing values based on the previous row. 

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/c1e57e7e-920c-45c8-9124-1d152995e29a)

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/5effec2f-b74c-47d6-87e3-3b1b7223e54e)

3. I splitted the Price column into two columns in the Products table. 

At the beginning :

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/a8a3eb5a-2ad2-4134-9f1a-453a64a53f65)

I split the price column into Currency and Price Value columns :

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/fdfaa586-517a-400b-aa8a-eae606880673)

4. I removed top 2 rows from the table and promoted first row as a header.

At the beginning :

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/10873551-0a15-4286-91b6-8c2baca821fc)

Last version :

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/19b07af1-8a33-4baf-be0b-7623f3fa935d)

5. Transpose the Manufacturer table :

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/53cce3aa-0fa2-4f51-b637-d3363e6bce6b)

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/4ce9e2c0-4f52-47fe-93ac-be9c7882b9a2)


## 2. Data Exploration and Analysis 

-- > Before the data exploration in Power BI we need to create some calculated columns using DAX functions.

1. Create a new table called Date :

<b>Date = CALENDAR( DATE(2017,1,1), DATE(2021, 12, 31) )</b>

2. We need to create a calculated column since there is no direct relationship between Sales table and Geography table :

* <b>ZipCountry = Geography[Zip] & "," & Geography[Country]</b>
* <b>ZipCountry = Sales[Zip] & "," & Sales[Country]</b>

3. Create a calculated column for the Sintec Revenue, Sintec Market Share, Previous Year Sales, % Growth rate based on previous year :

* <b>Sintec Revenue = Calculate( SUM(Sales[Revenue]), Manufacturer[ManufacturerID] = 4 )</b>
* <b>Sintec Market Share = DIVIDE ( Sales[Sintec Revenue], SUM(Sales[Revenue]), 0)</b>
* <b>PY Sales = Calculate( SUM(Sales[Revenue]), SAMEPERIODLASTYEAR('Date'[Date] )</b>
* <b>% Growth = DIVIDE ( SUM(Sales[Revenue]) - [PY Sales], [PY Sales] )</b>

-- > Now we can create some visualizations to explore the data and create business insights.

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/5183888d-a947-4e4f-8ed6-7915f07739ae)   ![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/e42c33c2-a44c-4e20-a739-937f27518fb0)

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/453a944f-7161-43ba-a637-303779c4fbdd)   ![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/0993cf4e-6560-4f76-bb2e-57c904515541)


## 3. Dashboard 

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/13874fab-e4a9-411a-a406-ee5c92c747b3)

![image](https://github.com/ugurEki/Competitor-Sales-Analysis/assets/82041882/193d31e8-1bd9-4096-bc15-ede6c801f8f9)


## Conclusion :

1. In the USA, Sintec holds a market share that accounts for % 38.22 of the total market.
2. In Germany, Artisans is the dominant player with a market share exceeding % 50 and generating substantial revenue.
3. Sintec's market share across the globe stands at % 21.15 of the total market in 2021.
4. There was a significant growth of % 18.8 in the 2021 compared to the previous year.



























