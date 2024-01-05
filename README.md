# sales_analyst
The sales_insights dashboard in POwer BI provides real time visibility into key sales metric, utilizing dynamic charts and graphs to analyze revenue, customer acquisition, and product performance.

# Data Analysis Using SQL
1. Show all customer records:<br>
```SELECT * FROM customers;```
2. Show total number of customers:<br>
```SELECT count(*) FROM customers;```
3. Show transactions forn chennai city market (market code for chennai is Mark001):<br>
```SELECT * FROM transactions where market_code='Mark001';```
4. Show distrincvt propduct codes that were sold in chennai:<br>
```SELECT distinct product_code FROM transactions where marketr_code='Mark001';```
5. Show transactions where currency is US dollars:<br>
```SELECT * FROM transactions where currency='USD';```
6. Show transactions in 2020 join by date table:<br>
```SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;```
7. show totoal revenue in year 2020:<br>
```SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.yera=2020 and transactions.currency="INR\r" or transactyions.currency="USD\r";```
8. Show total revenue in year 2020, January Month:<br>
```SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r")```
9.Show total revenue in year 2020 in Chennai
```SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";```

# Data Analysis Using Power BI
1. Formula to create norm_amount column:<br>
```= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)```
