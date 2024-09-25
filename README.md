# PowerBI-Project-Covid-19-Dashboard

PowerBI Project: Covid – 19 Dashboard
Project description:
Build a suitable Dashboard, to analyse and get insights from the data given.
Choose the visualizations wisely for the type of column and purpose of the chart / graph.
Create reports to perform the below analysis:
Q1. How has the number of COVID-19 cases and deaths evolved over time in different
regions?
To show how the number of COVID-19 cases and deaths has evolved over time in different WHO regions using a Pie Chart in Power BI, follow these steps:
Steps to Create a Pie Chart to Show Cases and Deaths by Region:
1. Ensure You Have the Required Data
•	Your table should already have columns like Date_reported, WHO_region, New_cases, Cumulative_cases, New_deaths, and Cumulative_deaths.
•	The analysis will focus on WHO_region and the Total Cumulative Cases or Total Cumulative Deaths.
2. Create the Necessary Measures (if needed)
•	If you don't have measures for Total Cumulative Cases and Total Cumulative Deaths, create them using DAX.
For Total Cumulative Cases:
DAX
Copy code
TotalCumulativeCases = SUM('Table'[Cumulative_cases])
For Total Cumulative Deaths:
DAX
Copy code
TotalCumulativeDeaths = SUM('Table'[Cumulative_deaths])
3. Insert a Pie Chart Visual
•	In Report View, go to the Visualizations pane and select the Pie Chart visual.
4. Configure the Pie Chart for COVID-19 Data
•	Legend: Drag the WHO_region field into the Legend section. This will categorize the pie chart slices by different regions.
•	Values: Drag the TotalCumulativeCases or TotalCumulativeDeaths measure into the Values section to display the number of cases or deaths for each region.
5. Visualize Cases and Deaths in Separate Pie Charts (Optional)
•	You can create two separate pie charts:
o	One for Cumulative Cases.
o	One for Cumulative Deaths.
•	Use WHO_region in the Legend for both charts, and use TotalCumulativeCases in one and TotalCumulativeDeaths in the other for the Values.
6. Customize the Pie Chart (Optional)
•	Go to the Format pane to change the appearance:
o	Data labels: Turn on data labels to display the total number of cases or deaths within each region slice.
o	Colors: You can change the colors of each region for better distinction.
                     

Q2. Are there any noticeable patterns or trends in the data, such as spikes or declines in
cases?
To identify noticeable patterns or trends, such as spikes or declines in COVID-19 cases, you can use a Stacked Area Chart in Power BI. This visualization will help you analyze the data over time, showing the evolution of cases in different regions and highlighting periods of increases or decreases.
Steps to Create a Stacked Area Chart to Show Trends in Cases:
1. Ensure You Have the Required Data
Your table should already have the following columns:
•	Date_reported
•	WHO_region
•	New_cases or Cumulative_cases (for tracking spikes and trends)
2. Insert a Stacked Area Chart
•	In Report View, go to the Visualizations pane and select the Stacked Area Chart visual.
3. Configure the Stacked Area Chart
•	X-Axis: Drag Date_reported to the X-Axis field to show cases over time.
•	Y-Axis: Drag New_cases (or Cumulative_cases if you want to show cumulative trends) to the Y-Axis field.
•	Legend: Drag WHO_region to the Legend section to stack the areas by region. This will display the contribution of each region to the overall trend.
4. Customize the Stacked Area Chart (Optional)
•	Time Granularity: If the data is daily, but you want to analyze trends weekly or monthly, use Date hierarchies. Right-click on the Date_reported in the X-Axis field and select Drill Down options (e.g., Week, Month).
•	Colors: Go to the Format pane and adjust the colors for each region to better distinguish the areas.
•	Data Labels: You can turn on data labels for more detail, but this may clutter the chart. Use it only if necessary.

                      
Q3. Plot weekly moving average of the cases and deaths.
To plot the weekly moving average of COVID-19 cases and deaths using an Area Chart in Power BI, follow these steps:
Steps to Create a Weekly Moving Average Area Chart for Cases and Deaths:
1. Ensure You Have the Required Data
Your dataset should have the following columns:
•	Date_reported
•	New_cases
•	New_deaths
2. Create Measures for Weekly Moving Averages
To calculate the 7-day (weekly) moving average for new cases and deaths, use the following DAX formulas.
•	Weekly Moving Average for New Cases:
DAX
Copy code
WeeklyMovingAvgCases = 
AVERAGEX(
    DATESINPERIOD(
        'Table'[Date_reported], 
        LASTDATE('Table'[Date_reported]), 
        -7, 
        DAY
    ), 
    'Table'[New_cases]
)
•	Weekly Moving Average for New Deaths:
DAX
Copy code
WeeklyMovingAvgDeaths = 
AVERAGEX(
    DATESINPERIOD(
        'Table'[Date_reported], 
        LASTDATE('Table'[Date_reported]), 
        -7, 
        DAY
    ), 
    'Table'[New_deaths]
)
These measures calculate the 7-day average by looking back over the last 7 days from each date.
3. Insert an Area Chart
•	In Report View, go to the Visualizations pane and select the Area Chart visual.
4. Configure the Area Chart
•	X-Axis: Drag Date_reported to the X-Axis to represent time.
•	Y-Axis: Drag the WeeklyMovingAvgCases measure to the Y-Axis to plot the weekly moving average of cases.
•	Legend: If you want to split the chart by different regions or countries, drag WHO_region or Country to the Legend field. This will create separate lines/areas for each region or country.
5. Create a Second Area Chart for Deaths (Optional)
•	If you want to visualize the weekly moving average of deaths separately, repeat the above steps but use the WeeklyMovingAvgDeaths measure instead of the cases.
•	Alternatively, you can add both the WeeklyMovingAvgCases and WeeklyMovingAvgDeaths measures to the Y-Axis of a single chart, using different colors to differentiate between them.
6. Customize the Chart (Optional)
•	Time Granularity: If needed, right-click the Date_reported field on the X-Axis and choose Drill Down to change the date hierarchy to a more specific level (day, week, month).
•	Format the Chart: Go to the Format pane to customize colors, data labels, and other formatting options for the area chart.
                           
Q4. Plot country wise cases count.
To plot country-wise COVID-19 case counts using a Stacked Bar Chart in Power BI, follow these steps:
Steps to Create a Stacked Bar Chart for Country-wise Case Count:
1. Ensure You Have the Required Data
The dataset should have the following columns:
•	Country
•	New_cases (for new case counts) or Cumulative_cases (for total case counts)
2. Insert a Stacked Bar Chart
•	In Report View, go to the Visualizations pane and select the Stacked Bar Chart visual.
3. Configure the Stacked Bar Chart
•	Axis: Drag the Country column to the Axis field. This will categorize the bars by each country.
•	Values: Drag the New_cases (if you want to visualize new cases) or Cumulative_cases (if you want to visualize total cases) to the Values field. This will determine the length of the bars based on the case count for each country.
•	Legend: If you want to further break down the data (e.g., by WHO_region), you can drag the WHO_region column into the Legend field. This will stack the bars by region within each country.
4. Customize the Chart (Optional)
•	Sort the Data: Click on the three dots in the top-right corner of the chart and select Sort by Cumulative_cases (or New_cases) to display the countries with the highest cases at the top or bottom.
•	Colors: Go to the Format pane to change the color scheme of the stacked bars, if needed.
•	Data Labels: Turn on data labels in the Format pane to display the exact case counts on each bar.

             
Q5. Add a monthly filter to the above plot.
To add a monthly filter to the country-wise stacked bar chart in Power BI, you can use a Date Slicer. This will allow you to filter the chart data by specific months, showing only the COVID-19 case counts for the selected month(s).
Steps to Add a Monthly Filter to the Country-wise Cases Plot:
1. Ensure Your Data Has Date Information
Your dataset should have a Date_reported column that contains the date of the reported cases.
2. Insert a Date Slicer
•	In Report View, go to the Visualizations pane and select the Slicer visual.
•	Drag the Date_reported field from your data into the Slicer.
3. Configure the Slicer for Monthly Filtering
•	Once the slicer is added, click the drop-down arrow on the slicer (usually in the top-right corner of the slicer).
•	Choose Date Hierarchy if it's not already applied, and then set the hierarchy to Month and Year.
•	This will allow you to filter the data by months and years in the slicer.
4. Sync the Slicer with the Stacked Bar Chart
•	The slicer should automatically filter the stacked bar chart since it’s based on the same dataset.
•	By selecting specific months (or a range of months) in the slicer, the stacked bar chart will update to show only the case counts for that period.
5. Customize the Slicer (Optional)
•	Go to the Format pane (paint roller icon) to customize the appearance of the slicer:
o	Orientation: You can set it to Horizontal or Vertical depending on your dashboard layout.
o	Date Input: Choose whether you want a slider or a dropdown list for month selection.
o	Formatting: Customize the colors and fonts of the slicer to match your report theme.
                    

                                                                                   OR
                                
Q6. Create a map chart to visualize the intensity of covid cases.
To create a Map Chart in Power BI to visualize the intensity of COVID-19 cases across countries, follow these steps:
Steps to Create a Map Chart for Visualizing COVID-19 Case Intensity:
1. Ensure You Have the Required Data
The dataset should contain the following columns:
•	Country (or Country_code)
•	Cumulative_cases (for total case counts) or New_cases (for new daily case counts)
•	Latitude and Longitude (optional, but helpful for more accurate mapping)
2. Insert a Map Chart
•	In Report View, go to the Visualizations pane and select the Map visual (represented by a globe icon).
3. Configure the Map Chart
•	Location: Drag the Country (or Country_code) field to the Location field. Power BI will plot points on the map based on country names or codes.
•	Size: Drag the Cumulative_cases (or New_cases) field to the Size field. This will control the size of the circles on the map, where larger circles represent higher case counts.
•	Color Saturation: Drag the Cumulative_cases or New_cases field to the Color Saturation field to differentiate case intensity using color. Higher case counts will have darker or more intense colors.
4. Optional: Add WHO Region to the Legend
•	If you want to categorize the data by WHO_region, drag the WHO_region field to the Legend section. This will assign different colors to each region on the map, making it easier to see which regions are more affected.
5. Customize the Map Chart (Optional)
•	Go to the Format pane (paint roller icon) to make additional customizations:
o	Map Style: You can change the map theme (e.g., Dark, Light, Grayscale).
o	Bubbles: Adjust the size of the bubbles to ensure they are properly visible for all countries.
o	Data Labels: Enable data labels if you want to show case numbers directly on the map.
6. Filter the Data (Optional)
•	You can add a date slicer or region filter to focus on specific time periods or regions. For example, you could filter the map to show case intensity for a specific month or for a particular WHO region.
Example Output for a Map Chart:
•	Bubbles of different sizes will appear on the map, representing countries.
•	Larger bubbles indicate countries with higher case counts, and smaller bubbles indicate countries with fewer cases.
•	Color intensity can be used to differentiate between countries with high and low case counts.
                              
Q7. Create a hierarchy of WHO region and Country.
To create a hierarchy of WHO region and Country in Power BI and visualize the data, follow these steps:
Steps to Create the Hierarchy
1.	Open the Data View:
o	Go to the Data View in Power BI where you can see the table with the columns WHO_region and Country.
2.	Create a Hierarchy:
o	In the Fields pane, locate your table (e.g., Table).
o	Right-click on the WHO_region field, and select New Hierarchy.
	This will create a hierarchy with the WHO_region as the top level.
o	Next, drag the Country field and drop it onto the newly created hierarchy (under the WHO_region field).
	Now, Country will become the second level of the hierarchy.
You now have a hierarchy where the WHO region is the parent, and Country is the child.
Visualizing the Hierarchy in a Power BI Report
1.	Add a Visual:
o	Go to the Report View.
o	In the Visualizations pane, select a visual type. You can use a Matrix, Table, or Tree Map for hierarchical data visualization.
2.	Add the Hierarchy to the Visual:
o	Drag the hierarchy you just created (from the Fields pane) into the Rows (or Values) section of the selected visual.
For example:
o	In a Matrix visual, place the hierarchy in the Rows section.
o	In a Tree Map, place the hierarchy in the Category section.
3.	Expand the Hierarchy:
o	Once the hierarchy is in the visual, you can click on the expand/collapse icons (down arrows) to drill down into the countries under each WHO region.
Example of How to Set It Up:
•	For a Matrix visual:
o	Rows: Add the WHO_region > Country hierarchy.
o	Values: You can add fields like Cumulative_cases or Cumulative_deaths to display the metrics alongside the regions and countries.
                          
Q8. Use the previous hierarchy and identify which WHO regions are most affected.
To identify which WHO regions are most affected by COVID-19 using the Matrix hierarchy (WHO Region > Country), we will look at the Total Cumulative Cases and/or Total Cumulative Deaths within the Matrix visual. You can use this hierarchy to compare the impact across different regions and their respective countries.
Steps to Create the Matrix Visual with Hierarchy and Identify the Most Affected Regions:
1. Ensure the Hierarchy Exists
If you haven't already created a hierarchy, you can create a hierarchy of WHO Region and Country:
•	In the Fields pane, right-click WHO_region and select New Hierarchy.
•	Drag Country into this hierarchy under WHO_region.
2. Create the Required Measures
To identify the most affected regions, create DAX measures for:
•	Total Cumulative Cases:
DAX
Copy code
TotalCumulativeCases = SUM('Table'[Cumulative_cases])
•	Total Cumulative Deaths:
DAX
Copy code
TotalCumulativeDeaths = SUM('Table'[Cumulative_deaths])
3. Add the Matrix Visual
•	Go to the Report View and from the Visualizations pane, select the Matrix visual.
4. Add the Hierarchy to the Matrix
•	In the Fields pane, locate the hierarchy of WHO_region > Country.
•	Drag the hierarchy into the Rows field of the Matrix visual.
5. Add the Measures to the Matrix
•	Drag the TotalCumulativeCases measure to the Values section of the Matrix.
•	Optionally, add the TotalCumulativeDeaths measure alongside to view the cumulative deaths per region and country.
6. Expand/Collapse Hierarchy
•	The Matrix will now display data grouped by WHO Region and Country. You can use the expand/collapse arrows to drill into the details:
o	WHO Region as the parent.
o	Country as the child, showing specific country-level data under each region.
7. Identify the Most Affected Regions
•	Sort the Matrix by Total Cumulative Cases or Total Cumulative Deaths by clicking on the column header (e.g., TotalCumulativeCases) to see the most affected WHO regions at the top.
•	The WHO regions with the highest total cases and deaths will appear at the top.
                      


