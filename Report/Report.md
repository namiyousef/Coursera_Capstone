**What is the best neighbourhood to live in as a student at Imperial
College London?**

\

**Abstract[ ]{.Apple-tab-span}3**

**Introduction[ ]{.Apple-tab-span}4**

1.  **Background[ ]{.Apple-tab-span}4**
2.  **Literature Review[ ]{.Apple-tab-span}4**
3.  **Scope[ ]{.Apple-tab-span}4**

**Data[ ]{.Apple-tab-span}5**

1.  **Foursquare[ ]{.Apple-tab-span}5**
2.  **Rent Barometer[ ]{.Apple-tab-span}5**
3.  **Office of National Statistics (Population)[ ]{.Apple-tab-span}5**
4.  **UK Crime Stats[ ]{.Apple-tab-span}6**
5.  **Google Maps[ ]{.Apple-tab-span}6**

**Methodology[ ]{.Apple-tab-span}7**

**Results[ ]{.Apple-tab-span}8**

**Discussion[ ]{.Apple-tab-span}9**

**Conclusion[ ]{.Apple-tab-span}10**

**Further Work[ ]{.Apple-tab-span}11**

**Resources[ ]{.Apple-tab-span}12**

1.  **Data Sources[ ]{.Apple-tab-span}12**
2.  **Other[ ]{.Apple-tab-span}12**

\

**Abstract**

**Introduction**

1.  **Background**

Imperial College London is a STEM university situated in South
Kensington: a cultural area full of museums, parks, restaurants, shops
and hotels. As such, the university's campus is fairly small, and has
minimal accommodation to offer students after their first year at
university. This results in the vast majority finding private
accommodation, typically a couple of miles away from South Kensington,
due to the high flat prices (per meter squared) in the
area.[ ]{.Apple-converted-space}

With this, commute to university becomes much longer, with many opting
to cycle, use the bus or the tube (underground train) instead, while
student safety decreases due to increased crime rates further away from
university. Of course, other areas have their own positives, as they
typically have younger demographics, are more diverse, can be more
'trendy' and offer access to other amenities, such as
nightclubs.[ ]{.Apple-converted-space}

At the moment, students are able to find correct properties (in terms of
price and location) through trial and error (on website such as
[[rightmove.co.uk]{.s1}](http://rightmove.co.uk) and
[[zoopla.co.uk]{.s1}](http://zoopla.co.uk)) or by consulting with
real-estate agencies, such as Foxtons or Dexters. However, there exists
no mechanism by which students can *understand* the type of
neighbourhood or area wherein they look for housing. Ideally, students
would be able to answer a couple of questions regarding what they
consider to be important features in a neighbourhood, and get answers in
the form of 'suitable' neighbourhoods for
them.[ ]{.Apple-converted-space}

This report aims to explore this problem in more detail and finding a
solution.

1.  **Literature Review**

Definitions:

a neighbourhood is referred to as a London postcode district.

Parameters to consider:

-   []{.s2}Average house price per unit area in the area
-   []{.s2}Trendiness in the areas
-   []{.s2}Availability of restaurants / nightlife
-   []{.s2}Distance from uni (accounting for walk vs. cycle vs. bus vs.
    train)
-   []{.s2}Average age in the area
-   []{.s2}Crime rate
-   []{.s2}Closeness of supermarkets

1.  **Scope**

This project has two objectives:

1.  Cluster the neighbourhoods to find any that are similar, and thus
    'appropriate' for students
2.  Create a model that quantifies neighbourhoods, giving them a score
    for how suitable they are for students. This model should be
    deployable such that a student could enter an address that they are
    considering, and it would give them a score, as well as highlight
    the key parameters affecting that score (for example, high crime
    rate).

```{=html}
<!-- -->
```
1.  []{.s3}Note that this project is partly motivated by the final
    assignment (Capstone Project) on the IBM Professional Data Science
    Certificate. **For peer assessors, please only consider Objective 1
    (Clustering) as a submission for the Capstone.**[**Data**]{.s3}

\

This project requires more data than that available from
Foursquare.[ ]{.Apple-converted-space}

A description of the data required for this project will be given here,
as well as links. Note that the methodology for how the data will be
used is given under **Methodology**.

-   []{.s2}**Foursquare:** will be used for exploring venues in postal
    districts, as well as trendiness
-   []{.s2}**Rent Barometer:** includes data on average rent prices
    ([![equation.pdf](file:///equation.pdf)]{.s4}) in London by postcode
    districts for different property types (Studios, 1---5
    beds)[ ]{.Apple-converted-space}
-   []{.s2}**Office of National Statistics (Population):** includes age
    data (male and female) by districts for different years
-   []{.s2}**Police Crime Data:** includes crimes (of different types)
    per district, as well as information on districts (such as
    population and land area)
-   []{.s2}**Google Maps:** will be used to explore distances and
    durations from locations to Imperial College

Note that links tot he datasets of Rent Barometer, Office of National
Statistics and UK Crime Stats are given under **Data Sources**. Both
Google Maps and Foursquare data are accessed through API's, and as such
have no 'datasets'.[ ]{.Apple-converted-space}

\

The next subsections will discuss the datasets in more detail in terms
of the parameters that they contain and how they will be used to achieve
the objectives of the project.

\

1.  **Foursquare**

Foursquare gives developers a certain number of calls (cite Alex Akklson
from IBM) to retrieve information regarding
venues.[ ]{.Apple-converted-space}

This project will use the following approaches:

-   []{.s2}Postcode districts will be explored for specific venues
    relevant to students, these include: nightclubs, bars, pubs,
    restaurants, coffee shops and grocery stores.
-   []{.s2}The 'trending' feature in Foursquare will be used to gather
    information about the trendiness of a postcode district at different
    times of the day.

The data described above will be used to create 'metrics', for example
how 'trendy' the area is, or what the 'nightlife' score is. This is
described in more detail under the
methodology.[ ]{.Apple-converted-space}

1.  **Rent Barometer**

The rent barometer dataset is a webpage containing tables which present
information on weekly rent for different property types in each postcode
district.[ ]{.Apple-converted-space}

Webscraping will be used to extract this information. There are some
missing values in the datasets, and these will be approximated by
suitable models.

The data collected here would also be converted to a metric relevant to
students.

1.  **Office of National Statistics (Population)**

This dataset is a .CSV file, and thus easily accessible.

It's important to note that the data is outdated, containing data from
2008.

This data will be used to create a metric for the average age in each
postcode district.

1.  **UK Crime Stats**

The UK crime statistics can be exported as a .XLS file. It will be used
to determine a 'safety score' for each postcode district.

1.  **Google Maps**

Google gives developers access to Map data.[ ]{.Apple-converted-space}

Google maps will be used to determine average durations from postcode
districts to Imperial College London (bus, tube, walk and cycle).

This data will be used to create a 'closeness score' for each postcode
district.

\

**NOTE:** DATA WRITTEN HERE IS OUTDATED. MUCH OF IT CANNOT BE USED.
WORTH FINDING NEW DATASETS.

\

[]{.s5}**[ ]{.Apple-tab-span}3.[ ]{.Apple-tab-span}Methodology**

**[ ]{.Apple-tab-span}4.[ ]{.Apple-tab-span}Results**

**[ ]{.Apple-tab-span}5.[ ]{.Apple-tab-span}Discussion**

**[ ]{.Apple-tab-span}6.[ ]{.Apple-tab-span}ConclusionFurther Work**

\

\

[]{.s5}**[ ]{.Apple-tab-span}8.[ ]{.Apple-tab-span}Resources**

1.  **Data Sources**

[<https://www.rentbarometer.com/london/all-prices/by-postcode.html#BR>]{.s1}

[<https://data.london.gov.uk/dataset/office-national-statistics-ons-population-estimates-borough>]{.s1}

[<https://data.police.uk/data/fetch/159fe36a-b26d-4bb4-882a-803f490a7b2b/>]{.s1}

[<https://developers.google.com/maps/documentation/distance-matrix/overview>]{.s1}[ ]{.Apple-converted-space}

\

1.  **Other**

\

\
