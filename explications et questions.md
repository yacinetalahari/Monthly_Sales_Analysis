**part 1**

first we created dataframe

randint to generate random integers we pass a min value and a max value and size so we limit how many integers we want to generate

**part 2**

we load csv file we geneated in part 1

Nan for the first month because basically it's firts month

quarters are used to split the year into 4 parts thats simplify our analysis just like tnhis example

Pandas Quarter

1

2

3

In pandas, you can easily extract the quarter of a date using the dt.quarter attribute. This is useful for time series analysis where you need to group data by quarters.



Example



import pandas as pd



\# Create a Series of dates

s = pd.Series(\["2020-01-01", "2020-04-01", "2020-07-01", "2020-10-01"])

s = pd.to\_datetime(s)



\# Extract the quarter

quarters = s.dt.quarter

print(quarters)

Copier

Output:



0 1

1 2

2 3

3 4

dtype: int64



**part 3**



so pivot table is used to aggregate data from a long data to an easy understandable report and pivot table needs 4 elements to work



index is rows basically



columns

values : the data we want to calculate in our example are productts

calculation : the aggregation function we used here is mean that calculates the average of all sales values





**part 4**





the idxmax gives us the indexlabel of the highest value in the total\_sales column



the df.loc uses that index to retrive the entire row with all columns







sum calculates the sum of all values of products A B . . . .



max gives maximum



strftime is just a formatter used to tell python how to display time or date (only usable with dates and time)

last 2 parts by MESBAHI
Part 5 – Visualization with Seaborn and Matplotlib:



This part shows how to visualize monthly sales data using different types of plots to better understand trends and sales distribution by product.



1)Prepare the data for trend plots



&nbsp;   Select the Month column and the product columns (Product\_A, Product\_B, etc.) for       individual sales plotting.



&nbsp;   Convert the DataFrame to long format using melt().



&nbsp;     id\_vars=\['Month'] → columns to keep fixed (here, months).



&nbsp;     value\_vars=products → columns to transform into a single Sales column.



&nbsp;     var\_name='Product' and value\_name='Sales' → names for the new columns.



&nbsp;  This is necessary because Seaborn works better with long-form DataFrames.



2)Plot monthly trends per product (Lineplot)



&nbsp;  sns.lineplot plots sales over months for each product.



&nbsp;  hue='Product' → separates lines by product with different colors.



&nbsp;  marker='o' adds a marker at each month for visibility.



&nbsp;  plt.xticks(rotation=45) → rotates x-axis labels to avoid overlap.



3)Stacked bar chart



&nbsp;  Use df.set\_index('Month')\[products] to prepare data.



&nbsp;  kind='bar', stacked=True → shows each product’s contribution to total monthly sales.



&nbsp;  Annotate the best month (identified in Part 4) with plt.text() using       best\_month\_sales and best\_month\_name.



4)Heatmap of sales (Product vs Month)



&nbsp;  sns.heatmap visualizes the density and volume of sales.



&nbsp;  .T transposes the DataFrame so products are on the vertical axis and months on the      horizontal axis.



&nbsp;  annot=True displays the sales numbers on the heatmap.



&nbsp;  cmap='YlGnBu' sets a color palette for visual clarity.



5)Sales distribution per product (Boxplot + Swarmplot)



&nbsp; Boxplot → shows median, interquartile range (IQR), and outliers.



&nbsp; Swarmplot → overlays individual sales points to see actual distribution.



&nbsp; This combination helps identify:



&nbsp; Consistency of sales (small spread = stable sales).



&nbsp;  Outliers (points far from the median).



6)Final Insight



&nbsp; Using print(), we extract information from the visualization:



&nbsp; Median sales per product.



&nbsp; Product with the highest median, indicating stable and strong performance.

