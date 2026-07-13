# NYC AirBnB Exploratory Data Analysis and Power Bi Rental Analysis

## Project Overview:
This project entails an EDA of a 2024 New York City airbnb dataset as well as a power Bi dashboard for renters to find the right price to rent at. The dashboard also goes on to present additional analysis for finding potential opportunities in the market.

## Data Source:
The dataset contains 20,765 entries and 22 features, including:
- id: Unique identifier for each listing
- name: Title of the Airbnb listing
- host_name: Name of the host
- neighborhood_group: Group (borough) where the listing is located
- latitude/longitude: Geolocation of listings
- price: Nightly rental price
- room_type: Type of accommodation (e.g., entire home, private room)
- reviews_per_month: Average monthly reviews for the listing
- availability_365: Number of available days in the year

The ArcGIS map was made by joining the dataset to the 2020 Neighborhood Tabulation Areas (NTAs).
- BoroCode: Borough of census tract.
- BoroName: Borough Name.
- CountyFIPS: The Census Bureau defined County FIPS code
- NTA2020: 2020 Neighborhood Tabulation Area Code.
- NTAName: 2020 Neighborhood Tabulation Area Name
- NTAAbbrev: An abbreviation of the 2020 Neighborhood Tabulation Area name.
- NTAType: Type of Neighborhood Tabulation Area. One digit code assigned to an NTA to distinguish if it is residential or a non-residential area like a park, airport, cemetery, or other special area.
- CDTA2020: 2020 Community District Tabulation Area code.
- CDTAName: 2020 Community District Tabulation Area name.
- Shape_Length: Length of feature in internal units.
- ShapeArea: Area of feature in internal units squared.

## Process Summary:
1. Data cleaning
   1. Handled missing data by removing columns with null values.
   2. Dropped duplicate rows.
   3. Some listings did not have a number of baths, these were dropped (13/20736 listings after cleaning).
   4. Two listings had a list price of $100,000. These were removed as they pricing was implausable. 
  
## Exploratory Data Analysis
- First Glaces at the data show a range of prices from ~$30 - $10,000. The huge scale makes the visualization fairly useless.
- <img width="515" height="451" alt="image" src="https://github.com/user-attachments/assets/49625dd0-2351-4231-b22b-f28a92490e6e" />
- Out of fear of excluding meaningful data, these values up to $10,000 were included but charts were done on a Log scale to aid visualization. This was done with all price visualizations.
- <img width="515" height="454" alt="image" src="https://github.com/user-attachments/assets/db60e1e3-d08c-461e-a865-de9f1cfd153e" />
- Histograms of price per listing and availability 365 days a year were plotted.
- Data of Mean, median, minimum, and maximum price per borough / per room type in each borough were also included.
- An interesting insight when plotting the Log of price on the number of reviews was the "funnel" pattern that forms. We can see a large grouping around ~$100 a night that leads to higher number of reviews.
- <img width="566" height="451" alt="image" src="https://github.com/user-attachments/assets/5bd5f5a4-172a-495f-880b-44525f9afc8d" />

## Power Bi Dashboard
- The map visual was not able to be created on this dataset alone, it had to be joined with the 2020 Neighborhood Tabulation Areas (NTAs) so that the neighborhood boundaries could be mapped.
  - First attempt was to fuzzy join the dataset neighborhood names to the NTA boundary names, this didnt have a high match rate.
  - Second attempt was to use ArcGIS to create a join on the two datasets via a point-in-polygon spatial join. This had a 100% match rate with the dataset. This new joined dataset was then used to build a map in power bi showing median price per neighborhood. 
- Page 1 of the dashboard is meant to help Airbnb owners to find median prices of similar listings to them in their area. Renters can filter down to their location and number of beds / baths to help them see possible listing prices. The following GIf shows filtering down to 2 bedroom entire homes in the Coney Island-Sea Gate neighborhood of Brooklyn.
- <img width="2498" height="1440" alt="Map_of_Median_Prices" src="https://github.com/user-attachments/assets/e4ad4ee8-8f43-4882-9290-7cb0208c73ba" />
- Page 2 then goes onto a deeper dive into pricing and demand specifically in their area. They can use all this information to find the optimal price of their individual listing. The same filter of 2 bedroom entire homes in the Coney Island-Sea Gate neighborhood of Brooklyn pulled over from the previous page.
- <img width="2498" height="1440" alt="Pricing_and_demand_1" src="https://github.com/user-attachments/assets/7b8257d5-e412-4011-8572-72bed5217b6f" />
- Lastly, there is a market overview page. Here further market research can be conducted on the different boroughs of NYC. The availability 365 by neighborhood chart highlights possibly opportunity neighborhoods with the bottom right hand corner having the highest opportunity as its above the median price and booked out more than the median listing. The GIF drills down into Brooklyn and finds a possible opportunity neighborhood. Canarsie Park & Pier has an above average price and number of bookings per year.
- <img width="2498" height="1440" alt="Market_Overview" src="https://github.com/user-attachments/assets/53f8a9ff-6286-4e56-8524-9c9c78e24dfc" />

## Key Findings:
1. Pricing Trends
   1. Manhattan and Brooklyn have the highest prices
   2. Entire homes drive pricing in room types
   3. Number of beds/baths drive pricing in entire homes
   4. Price overall follows a "funnel" pattern. Listings of all types tend to gain the most reviews when priced around $100
2. Host Concentrations
   1. Hosts with 6+ listings take up about a quarter of the data.
   2. Manhattan specifically has 40% of its listings from hosts with 6+ listings. This shows Manhattan might be a tough market to break into and is fairly saturated with commercial properties.
3. Price Vs Demand
   1. We can still find neighborhoods with above median price and demand. These neighborhoods would be potentially attractive to invest in. Drilling into Brooklyn, we can find Brooklyn Heights. This neighborhood has a median price $25 above the median of Brooklyn, a median of 90 unbooked nights a year vs the median 182 of Brooklyn as a whole (Showing listings here are in high demand), and is made up of ~56% single listing hosts.
  
## How to Run This Project:
1. Clone the repo
2. Install necessary libraries for python EDA / Install Power Bi for .pbix file.
3. Run the Jupyter notebook for EDA and/or .pbix file for the Power Bi dashboard.

## Tools Used:
- Python / Pandas for EDA
- Power Bi + ArcGIS for dashboarding
