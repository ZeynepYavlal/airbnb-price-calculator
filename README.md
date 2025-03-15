# Airbnb - How Much Can You Make?
This project estimates how the different characteristics of an Airbnb affect the listing price. We created a tool to accurately predict the rental property's annual revenue. This tool helps investors/home owners make a good investment or avoid loss. 

## Research motivationn

Investors looking for a second and potentially passive source of income may consider buying and renting a property. In traditional real estate investing, the objective is purchasing a home with the intention of leasing it out permanently (usually for a period of six months and longer). However, as Airbnb and other platforms for vacation rentals have recently grown in popularity, there are more chances for property owners to create a passive income stream. Yet, this does not imply that it will turn out to be a valid investment for everyone. Depending on specific characteristics (e.g., demographics, accommodation and reviews) investing on a short-term rental may not be wise. For this reason, we created an estimation tool that future Airbnb owners can use to forecast their profits.

### Research question
_How do the characteristics of an Airbnb affect the listing price to accurately predict the rental property's annual revenue?_ 

## Research method
Firstly, to collect the required data, a web scraper was built for InsideAirbnb. Data for western EU (for a total of 25 cities) are used to conduct the regression analysis. The rationale is based on the fact that when considering Airbnb listings by region, Europe ends up being the one with the highest number of listings, for a total of 4,840,487 in 2021. 

The estimation tool will be accessible to everyone in an app. The visitor must select specific information about their accommodation. The data used to determine the estimated yearly income are:

- average daily price for different listings 
- monthly average occupancy rate for each city taken into account

The average daily price considered is based on competitors that have similar characteristics in terms of: 
- demographics (e.g., neighborhood, nearby facilities) 
- accommodation (e.g., ratings (cleanliness, checkin, communication), amenities, type of accommodation)

See the [original variables](https://github.com/course-dprep/team-assignment-team-4/blob/master/src/README.md) used.

Listed below are the final fourteen variables after cleaning the data and running the regression. 

|Variable                        |Description                                                                                     |
|--------------------------------|------------------------------------------------------------------------------------------------|
|city                            |The city of the listing                                                                         |
|host_is_superhost               |Whether host is superhost                                                                       |
|property_type                   |Self described type of property                                                                 |
|room_type                       |All homes are grouped into three types: Entire place / Shared room / Private room               |
|accommodates                    |The maximum capacity of the listing                                                             |
|bathrooms_text                  |The Number of bathrooms in the listing                                                          |
|price                           |Daily price in local currency                                                                   |
|review_scores_rating            |General review score of the listing                                                             |
|review_scores_cleanliness       |Review score for cleanliness of the listing                                                     |
|review_scores_checkin           |Review score of the check-in at the listing                                                     |
|review_scores_communication     |Review score of the communication by host                                                       |
|review_scores_location          |Review score of the property location                                                           |
|review_scores_value             |Review score of value of the listing                                                            |
|instant_bookable                |Whether the guest can automatically book the listing without the host requiring to accept       |   

To collect the required data a web scraper for [InsideAirbnb](http://insideairbnb.com/get-the-data.html) was built.

## Relevance

This research provides applicable insights for current and potential Airbnb hosts. This research aims to give Airbnb hosts a tool that can help them make an accurate prediction of their rental property's annual revenue. For current hosts, the tool can also help to see if their current price is up to date. In addition, it can also provide an indication of the price if the host wants to make a change to their Airbnb (for example, an extra bed), but also consider the effect of additional reviews. It can be said that the tool created by this research helps the hosts make a good investment or avoid loss. 

## Price prediction tool

In this research, a multiple linear regression was conducted to examine the effect of different characteristics of an Airbnb on its price. These results are displayed in the developed price prediction tool. In this tool, the outcome variable price is multiplied by the average annual bookings per city to get a predicted annual revenue. 

We recommend running the code to see the price prediction tool for yourself. The preview of the app can be seen [here](https://github.com/course-dprep/airbnb-price-calculator/blob/master/src/price-calculator-app/README.md). 

## Repository overview

```
- .github
- src
  - analysis
  - data-preparation
  - price-calculator-app
- .gitignore
- README.md
- makefile
```

## Dependencies

Please follow the installation guides on http://tilburgsciencehub.com/.

- Python. [Installation guide](https://tilburgsciencehub.com/building-blocks/configure-your-computer/statistics-and-computation/python/).
- R. [Installation guide](https://tilburgsciencehub.com/building-blocks/configure-your-computer/statistics-and-computation/r/).
- Make. [Installation guide](https://tilburgsciencehub.com/building-blocks/configure-your-computer/automation-and-workflows/make/).

- To knit RMarkdown documents, make sure you have installed Pandoc using the [installation guide](https://pandoc.org/installing.html) on their website.

- For Python, make sure you have installed the following packages:
```
pip install bs4
pip install selenium
pip install pandas

```

- For R, make sure you have installed the following packages:
```
install.packages("data.table")
install.packages("shiny")
install.packages("shinyWidgets")
install.packages("bslib")
install.packages("shinythemes")
install.packages("yaml")
install.packages("readr")
install.packages("tidypredict")
install.packages("broom")
install.packages("dplyr")
install.packages("ggplot2")
install.packages("ggfortify")
install.packages("tidyverse")
install.packages("readxl")
```

## Running the code
### Step-by-step
To run the code, follow these instructions:
1. Fork this repository
2. Open your command line / terminal and run the following code:
```
git clone https://github.com/{your username}/airbnb-price-calculator.git
```
3. Set your working directory to `airbnb-price-calculator` and run the following command:
```
make
```
4. When make has succesfully run all the code, it will generate a http URL. Copy and paste this URL in your browser to launch the price calculator app. 

5. To clean the data of all raw and unnecessary data files created during the pipeline, run the following code in the command line / terminal: 
```
make clean
```

Note: when the command line/terminal is closed, the website will not be available anymore. 

### Alternative route
An alternative route to run the code would be: 
- ../src/data-preparation -> download_merge_data.R
- ../src/data-preparation -> cleaning_data.R
- ../src/analysis -> regression_analysis.R
- ../src/price-calculator-app -> shiny_app.R

### Running the data collection
The workflow above does not include the data collection step. The output file of this step is shared in a Google Sheet, which gets downloaded in the pipeline. However, if you wish to collect the data yourself, you can by running our web scraper. The code for this scraper can be found [here](https://github.com/course-dprep/airbnb-price-calculator/blob/master/src/data-preparation/webscraper_airbnb_python.py): 
- ../src/data-preparation -> webscraper_airbnb_python.py

## Authors
Team 4: 
- [Cas Rooijackers](https://github.com/casrooij),           e-mail: c.rooijackers@tilburguniversity.edu 
- [Gennaro Santoro](https://github.com/Ginseng-Effect),     e-mail: g.santoro@tilburguniversity.edu 
- [Jesper Krauth](https://github.com/jesperkrauth),         e-mail: j.krauth@tilburguniversity.edu 
- [Ludovica Donatelli](https://github.com/ludoivca),        e-mail: l.donatellli@tilburguniversity.edu 
- [Patrick de Graaf](https://github.com/Patrickdeg),        e-mail: p.w.degraaf@tilburguniversity.edu 
