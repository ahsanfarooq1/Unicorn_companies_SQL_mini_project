# SQL Mini Project: Analyzing Unicorn Companies
## 1. Project Overview:
 This project involves analyzing a dataset of unicorn companies, which are privately held
 companies valued at over $1 billion as of November 2021. The project will include data creation,
 analysis using SQL, and answering specific questions about the dataset.

 ## 2. CSV Data Structure:
 You can use the following CSV structure to represent the dataset:
 Company,Country,Sector,Valuation (Billion USD),Founded Year,Select
 Investors
 SpaceX,United States,Aerospace,100.3,2002,Fidelity, Founders Fund,
 Baillie Gifford
 Stripe,United States,FinTech,95.0,2010,Sequoia Capital, Andreessen
 Horowitz, Baillie Gifford
 ByteDance,China,Artificial Intelligence,140.0,2012,Sequoia Capital
 China, General Atlantic
 UiPath,United States,Robotics,35.0,2005,Accel, CapitalG, Sequoia
 Capital
 Klarna,Sweden,FinTech,46.0,2005,Sequoia Capital, Silver Lake,
 Dragoneer
 ## 3. SQL Database Setup:
 I created a database and a table using the following SQL commands:
-- Creating a database
 CREATE DATABASE unicorn_companies;
 USE unicorn_companies;
 
 -- creating a table in database unicorn_companies
  CREATE TABLE unicorns (
 Id INT AUTO_INCREMENT PRIMARY KEY,
 Company VARCHAR(255),
 Country VARCHAR(100),
 Sector VARCHAR(100),
 valuation DECIMAL(10, 2),
Founded_year INT,
 Investors TEXT
 );
 
 INSERT INTO unicorns(Company,Country,Sector,valuation,Founded_year,Investors)
 VALUES
('SpaceX','United States','Aerospace',100.3,2002,'Fidelity, Founders Fund,Baillie Gifford'),
('Stripe','United States','FinTech',95.0,2010,'Sequoia Capital, Andreessen Horowitz, Baillie Gifford'),
('ByteDance','China','Artificial Intelligence',140.0,2012,'Sequoia Capital China, General Atlantic'),
( 'UiPath','United States','Robotics',35.0,2005,'Accel, CapitalG, Sequoia Capital'),
('Klarna','Sweden','FinTech',46.0,2005,'Sequoia Capital, Silver Lake, Dragoneer');

 # 4. Analysis Questions:
 Here are some questions you can answer using SQL queries:
 1- Top 5 Countries by Number of Unicorns
 2- Top 3 Sectors by Average Valuation:
 3- Unicorns Founded After 2010
 4- Total Valuation of Unicorns in the FinTech Sector
 5- Most Common Investors
 ## 5. Challenges:
 ● Identify Trends: Explore trends in the data, such as the growth of unicorns in specific
 sectors or countries.
 ● Investor Analysis: Which investors have the most unicorns in their portfolio?
 ● GrowthAnalysis: Compare valuations of companies founded in different decades to
 understand growth trends.

 ## My Queries to answer the questions
**1- Top 5 Countries by Number of Unicorns**
SELECT 
    Country, COUNT(*) AS number_of_unicorns
FROM
    unicorns
GROUP BY Country
ORDER BY number_of_unicorns DESC
LIMIT 5;

### Results showed that the United States had the highest number of unicorns, followed by countries like China and Sweden.

--- 
**2- Top 3 Sectors by Average Valuation:** 
SELECT sector, ROUND(AVG(valuation) ,2) AS Average_Valuation
FROM unicorns
GROUP BY sector
ORDER BY Average_Valuation DESC
LIMIT 3;

**The results revealed that sector Artificial Intelligence had the highest average valuations.**
---
**3- Unicorns Founded After 2010**
 
SELECT 
    *
FROM
    unicorns
WHERE
    Founded_year > 2010;
**result is shown in pdf**
---
**4- Total Valuation of Unicorns in the FinTech Sector**
SELECT 
    SUM(valuation) AS Total_Valuation_of_FinTech_Sector
FROM
    unicorns
WHERE
    Sector LIKE 'FinTech';
**The total valuation of FinTech unicorns was found to be 141.00 , reflecting the sector's significance.**
---







