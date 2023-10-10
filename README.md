# Homework 1 README

## Project Goal
The primary goal of this project is to conduct an in-depth analysis of Wikipedia article traffic patterns spanning from 2015 to 2023. To achieve this objective, we leverage the capabilities of the Wikimedia REST API. The API provides a wealth of information, including article view counts, article titles, access methods (mobile or desktop), and more. Our aim is to store this data in JSON files and subsequently perform comprehensive data visualization and analysis.

## Data Acquistion and API Documentation
The section below details the steps for data acquistion. We have:

1. An excel [sheet](https://docs.google.com/spreadsheets/d/1A1h_7KAo7KXaVxdScJmIVPTvjb3IuY9oZhNV4ZHxrxw/edit?usp=sharing) defining the subset of the English Wikipedia that represents a large number of articles about academy award winning movies. 
2. The Pageviews API which provides access to desktop, mobile web, and mobile app traffic data from July 2015 through the previous complete month. There is also available [documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews) and information about the [endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end) for this API can be found at: 

A sample request template of the API looks like:
```
ARTICLE_PAGEVIEWS_DESKTOP_PARAMS_TEMPLATE = {
    "project":     "en.wikipedia.org",
    "access":      "desktop",      
    "agent":       "user",
    "article":     "",             
    "granularity": "monthly",
    "start":       "2015070100",   
    "end":         "2023093000"    
}
```


A sample response of the API looks like:
```
{'project': 'en.wikipedia',
  'article': '12_Years_a_Slave_(film)',
  'granularity': 'monthly',
  'timestamp': '2015070100',
  'agent': 'user',
  'views': 75458}
````

**Note**
A code snippet is used in the Data Acquistion phase from [notebook](https://drive.google.com/file/d/1XjFhd3eXx704tcdfQ4Q1OQn0LWKCRNJm/view?usp=sharing) and this sample code is licensed [CC-BY](https://creativecommons.org/licenses/by/4.0/)

## Platform
This project was run on jupyter notebook on localhost. 

## Data Preprocessing and Analysis
Data Acquistion, Data Preparation, and Data Analysis are key phases within this project:

Data Acquisition: Pageview counts for specific Wikipedia articles are obtained through the Pageviews API.

Data Preparation: The Pageview count data is further preprocessed and transformed using python data structures to prepare it for analysis and visualization

Dataset Creation: This project yields three distinctive datasets:

Monthly Mobile Access: Aggregating pageviews from both mobile apps and mobile web.

Monthly Desktop Access: Focusing on pageviews originating from desktop devices.

Monthly Cumulative: Combining total pageview traffic for each article, encompassing both desktop and mobile sources via the "all-access" access type.

## Documentation
This project adheres to recommended best practices for replication and documentation:

Jupyter Notebook: detailed comments for data acquistion, processing, and analysis.

README File: Offers a general overview of the project, outlining its objectives, data sources, data processing procedures, and standards for reproducibility.

LICENSE File: Contains the MIT LICENSE for the project's code, ensuring it is freely usable.

## License
This project is open-source and follows the MIT License. You are free to use and modify the code according to the terms of the MIT License.

## Reproducibility
* Import and if necessary pip install the python libraries into your notebook.
* Run the Jupyter Notebook cells which call the API and read the Excel File that needs to present in the same directory as the notebook to run successful.
* Store fetched data in the form of a list of dictionaries in Python. Combine data for mobile website and app access.
* Create three lists representing views on mobile, desktop, and cumulative (mobile + desktop).
* Write these lists of dictionaries into three separate JSON files:

academy_monthly_desktop_start201501-end202309.json
academy_monthly_mobile_start201501-end202309.json
academy_monthly_cumulative_start201501-end202309.json
Create Dataframes from the list of dictionaries generated in the previous step.

Utilize these DataFrames to create and plot three visualizations:

* Maximum Average and Minimum Average: Time series for articles with the highest and lowest average monthly page requests for desktop and mobile access.
* Top 10 Peak Page Views: Time series for the top 10 article pages by largest (peak) page views over the entire time, categorized by access type.
* Fewest Months of Data: Display articles with the fewest months of available data for desktop and mobile access.

## Output Files
The project generates three JSON files:

* academy_monthly_mobile_201507-202312.json: Monthly mobile access data.
* academy_monthly_desktop_201507-202312.json: Monthly desktop access data.
* academy_monthly_cumulative_201507-202312.json: Monthly cumulative data.
