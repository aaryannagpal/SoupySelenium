# Global Incident Map

Global Incident Map is an online platform and repository that keeps collects real-time incidents and emergencies happening across the world. It visually presents events like natural disasters, terrorist activities, and disease outbreaks on interactive maps. 

The data for the events is collected from various reliable sources, including government agencies, news outlets, official reports, and other trusted organizations and displayed on the website as tables.

The link is [https://www.globalincidentmap.com/](https://www.globalincidentmap.com/)

For this instance, I will only access the **Outbreaks** part of the website, although with some modifications, it should work for the whole thing. 

The link for the same is here: [https://outbreaks.globalincidentmap.com/](https://outbreaks.globalincidentmap.com/)
## Issues Faced
Despite being a huge repository of data, the website has three main limitations in accessing them.
### 1. Indirect Datapoints
The data we desire is not stored in rows of the tables we see on the website, but as seperate webpages. The links to those webpages are stored in the table, along with some other metadata.
### 2. Limited Homepage Data
Only a few data points, out of thousands, are available on the homepage. To access more, we need to specify particular filters and then extract the data.
### 3. Poor Date Filter
No matter what range of dates are provided as filters, the website, at max, will only display data approximately 3 months prior to the end date in the filter. 
I do not know if it is a limitation purposely kept by the website or not, but it creates problem in scraping data.

## Current Solutions
### Solution for the Indirection
Since all the rows have the links to the data webpages stored in the same column, some loops can fix this. However, the time taken to access all the data points from their individual pages increases significantly.

### Solution for the Homepage Data
Since the homepage did not have enough data (only 75 data points when I last checked), we will have to use filters (date filter in this case) to access all the data and collect.

### Solution for the Filter
This is the interesting part. Whenever we apply a filter, the website link is modified by adding something like ```startdate = dd-mm-yyyy``` for start and end dates to it so the filters are implemented.

We would modify that link by first picking our start date and choosing end date as start date + 90 days (month and year adjusted) and keep adding 90 days to both start date and end date until we reach our desired end date. 

Using this, we would produce our own set of filtered links, which we would individually visit and collect the metadata and then, from the metadata, we would access individual data links and collect them individually.

## Comments
- Why the buggy date filter? Seems the most reliable despite being buggy. Plus, easy to iterate over.
- My code nearly ran for 4 days on a system with "medium" speed on just the 'Outbreaks' part. Use a really fast computer.

