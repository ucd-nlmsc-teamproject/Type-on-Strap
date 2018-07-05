#  Interim Report

#                  Team Name: JobMap

#

#











## **User Scenario: The Characters**

Searching for jobs after graduating or relocating from other country can be really very difficult and time consuming. Identifying jobs based on skill set and accommodation in near proximity of job location can be very tiring. While there is a lot of information about various jobs and accommodation they are held in disparate sources and they are relatively time consuming in identifying and searching for the related set of information required.

Out target users for the ideation that we generated are

1. College graduates looking for jobs and accommodation in close proximity
2. People relocating to Ireland from various part of the world.

For instance, Mariam started her job search and is actively looking for available jobs that matches her skill sets and at the same time she wishes to have an accommodation in close proximity to her job location. The set of information that she may be interested could vary from

- Job trend in that particular county
- List of jobs county wise and more flexibility in being able to drill down to a particular region in the county.
- Accommodation in close proximity of her job location
- Commutation distance and means to and fro from her place of stay to work.

A 2017 report by Indecon found that employment was the 3rd biggest barrier to returning emigrants after housing and motor related issues.

In another report, Growing Great Teams in Ireland, American Chamber of Commerce warned that the availability of quality and affordable accommodation would have a direct impact on jobs.

Reports as such intended us in developing a web based application which could assist people in their search of jobs and accommodation by allowing them to have required information easily all aggregated at one destined application.  The data for this is pulled from various resources. By using such application users would be able to able to sort out their job search along with an accommodation of close proximity to their place of work. This application could save time and aid users in being more organised in their plan of job search and relocation.

## **Technical Problem: The Setting**

A major impediment to the movement of people is the availability of jobs. As an example, a 2017 report by Indecon found that employment was the 3rd biggest barrier to returning emigrants after housing and motor related issues ( [https://www.dfa.ie/media/dfa-2017/globalirish/Report-on-Returning-Emigrants-2018.pdf](https://www.dfa.ie/media/dfa-2017/globalirish/Report-on-Returning-Emigrants-2018.pdf))

For people looking out for jobs and accommodation in close proximity of work location, determining the set of sources required for getting information, analysing it and making informed decisions between place of work and stay can be difficult.  The web application being designed aims in addressing these issues by providing informed decisions in a friendly user manner through visualization.

The set of information that can be obtained from the web application includes but not restricted to :

- Job Trend on a county level
- Indicating the number of jobs per county
- Accommodations in close proximity of jobs availability
- Map that shows the distance between place of work and nearest stay.

**Core Problem**

The core technical problems faced by us revolve around data, i.e data collection, data transformation, data integration, visualizing the information obtained.

**Data Collection**

The data required for this application to function are scraped from various resources but not limited to jobs.ie, CSO, myhome.ie. We obtained an API Key from CSO for scraping the data from that particular website. With the effect of GDPR in place we had to go through the Terms and Conditions to be able to scrape the data from other sites as we do not have their API. From the terms and conditions we learnt that jobs.ie and myhome.ie allow people in scraping the data.

**Data Transformation**

In order to make efficient use of the data collected from various sources, operations such as preprocessing of data, restructuring of data, feature extraction of required information were performed.

**Data Integration**

The information presented to the user would be a visualised map having both the jobs and accommodation data, so the integration of both data would go around geo-location and the integration method chosen would depend on this.



**Visualization**

The interface would have a trend graph which indicates the showcases the job trends, this is complemented with a map of Ireland which contains the information on jobs and accommodation. The visualizing of the map would be achieved through heat maps and google maps

**Competitors**

From our research, there are existing solutions that address various aspects of our solution but in isolation. There is no solution that provides the breadth of our solution. Broadly, the existing solutions fall into the following categories :

- Visual point in time snapshots of jobs data. These provide a visualisation similar to what we intend to use but are based purely on historical data. An example is the visualisation on [http://www.robertmanduca.com/projects/jobs.html](http://www.robertmanduca.com/projects/jobs.html)

- Jobs sites showing job listings at a county level but without the drilldown to a more detailed map representation. An example from jobs.ie is shown in the image below. Clicking on a county simply provides job listings for the county.

 ![](data:image/*;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAAC0lEQVR42mNgAAIAAAUAAen63NgAAAAASUVORK5CYII=)

- Another category is  interactive maps (generally based on Google maps API) to show information about properties. This captures one aspect of what our application would provide.

The key distinctions of our propositions are :

- Aggregating all of the above information from multiple sources that are of interest when relocating: Jobs, housing
- Enabling users to drilldown to the location of a listed job using the interactive Google maps API. The power of this approach is that the user gets the flexibility to examine the location in some more precise manner

## **Technical Solution: The Plot**

The jobmap web application assists people in looking for jobs and their trend over the past years along with the accommodation information within close proximity of place of work.

As the website gets loaded in the browser it displays two text fields and a button where in one of  the field is for the job sector that the user is interested to look into along with the location, as in county.

Based on user search the following actions are performed

- Load the related information from database and display to user.
- Show a statistical graph of the particular industry over the past years that the user searched for
- Set of jobs in the location that user searched for in a map
- Users can drill down(zoom in/out) of map for even precise information

The infrastructure used can be easily extended to add any additional features over time.

For implementing this application the following technologies have been used

- D3
- Google Maps API
- Django
- MySQL Database
- MySQL Client Connector for Django
- Redis
- Celery



**System Diagram comes here**

**Front End**

Our front-end is mix of Google map API and D3js with TopoJson library for our maps to show the trends amongst industries as a heatmap.  JS is the primary scripting language being utilised in the design of the front end.

**Heatmap**
Primary reason behind using D3js library and not the other equivalent option P5js is that it has a plethora of work done in terms of map designs, the Json generated files give way too much control to the developer to perform any aspect of design ranging from displaying data to animate individual parts of the map to make user experience as pleasant as possible. P5 on the other hand can do many of these things but lacks map support in general and is more useful for things which use art work rather. The design surrounding the map would be a material design library with a sliding bar which would give some options for the user to change data to what they require. It is a CSS library to use with web development.

**Maps**

We have come across many options in terms of maps to use for our second step where we more detail to the user about the map, there is mapbox, google Maps and Leaflet Javascript library. Our best option is at the moment google maps as it provides us with the geolocation which is hard to set up in terms of Leaflet as it uses third party services for the same and needs configuration. Mapbox is very similar to google maps and being familiar to google maps we simply couldn&#39;t find a really good reason to use mapbox. The main advantage about Leaflet is that its natively a Js library which helps our project since its in JS and the open source nature gives us the flexibility we require but at the same time google map api is more than enough for our requirements so going through both the options we found out it makes more sense to just simply employ the more efficient option.

**Libraries used for the projects:  **

- Css material design library
- D3js Library
- Google map API

**Back End**

**Website**

Django is a free and open-source web framework, written in Python, follows the model-view-controller architectural pattern.This framework has templates, libraries and APIs designed to work together for natural growth and connectivity. Django uses Python which is one of the most popular programming languages. It includes a layer between the developer and the database called an ORM (Object Relational Mapper) which makes it possible to move whole project between most major databases by changing just 1 line of a code.

**Web Server (Nana need your part)**

**Data Gathering**

Python programming is used for scraping the information from multiple sources including Web APIs, web sites etc... Data obtained is then processed, cleaned, transformed and then dumped into database which would serve as an input to the website based on the query.

** **

**Database**

MySQL is chosen database tool for our system as it is fast, reliable and open source database management system (RDMS – Relational Database Management System). SQL interpreter, GUI database viewers, stored procedures, cross-platform support, multiple CPU usage, client server system, session monitoring tools all helps in working and receiving of data in an efficient, stable and organized manner. MySQL can also be easily managed using visual web tools such as phpMyAdmin.

**Database Connector -  MySQL Client**

Programs communicating with servers are termed as a client software, this program communicates with the MySQL server, it&#39;s a client. When you enter SQL queries in this client, the response is returned to the client and displayed onscreen. The monitor program can send queries across a network; it doesn&#39;t have to be running on the machine where the database is stored.

**Redis**

Redis provides a structured way of storing the websites sessions and to implement sticky sessions across many different servers. By this a user&#39;s login is kept in store even if he connects to a different server of the same website, like Facebook: their load balancer tries to keep the user assigned to the same server on each session. By this the users won&#39;t lose their session as the session store would be shared across various instances.

**Celery**

Celery is a task queue and is the first choice we had for handling any background tasks in the Python/Django environment. It is available with a simple API and integrates completely with Django. This needs to be paired to other services which are called brokers for sharing and exchanging the information between web application and celery. The periodic tasks we would be handling with celery are :

- Scraping of data from websites once every month to have updated information
- Reminders to certain actions like activating the account.
- Activity notifications for users (notification on new job postings etc...)

**Data Sources**

With the GDPR in place scraping data from websites without their prior permission could lead to criminal offences, so we had to seek permission from companies to allow us in accessing their data. We couldn&#39;t get permission from the major companies but after researching and reading the Terms and Conditions of the companies websites for data collection we identified few likely websites where-in we can get the data for implementation of our application.

Design of the trend map requires relevant historical data of at least around 5 to 6 years old. CSO(Central Statistics Office) provides a huge amount of data ranging from various industries to sectors within the particular industry. They provide data of the past 8 years. The data obtained from their website is very attractive, rich and apt for our requirement. Data Sources are available in CSV, json formats. The data in these formats can be easily populated to the MySql database by running python scripts.

**GeoLocation**

** Information on how are we indetifying the co-ordinates some small information would do, be it vague but somehing to tell them**

**Jobs.ie**

This website is used for getting the list of jobs that are available in the market. This is considered as a probable website for getting jobs data as it permits in scraping the data from their site and moreover it is most likely used website from the employers posting their vacancies to users looking out for jobs.

**UCD Careers Connect**

UCD Careers team has permitted us in scraping the data from the careers portal of the university. As it is a university maintained website may roles ranging from graduate role to senior experienced roles can be obtained. As our primary focus of this application is a graduate student so identifying of the graduate roles along with accommodation information would be pretty easy.

**Myhome.ie**

Myhome.ie provides rich amount of accommodation information. So this website is considered as a viable resource for getting the accommodation data.

**CSO(Central Statistics Office)**

The information obtained from this website is used for providing statistical view of the jobs industry over the past years as it provide data of the past 8 years.

**Key Issues ---- Nana need your information here**

**Data Formats**

**API Limits**

**Data Challenges**

During the process of downloading the data from websites many problems were encountered like  transformation of the data, understanding data formats, incorrect data being obtained, missing data points,  geocoding errors, API limits etc.., they are all discussed briefly :

- Data Collection
- Transformation
- Integration
- Visualization

**Data Collection**

Data required for this application to function are scraped from various sources like jobs.ie, myhome.ie, cso (for historical data). The data obtained from these sources are all in different formats. Each data format required some understanding of the structure of the obtained data so as to easily identify the erroneous data like missing values, duplicated information etc.. the data obtained was all analysed, parsed, checked and then transferred to the database. The entire flow of this process was developed on python scripts.

**Data Transformation**

To make better use of the obtained data pre-processing techniques, restructuring of data, data extraction were performed. Each data source obtained a thorough check and parsing of the information.

**Data Integration**

The information presented to the user would be a visualised map having both the jobs and accommodation data, so the integration of both data would go around geo-location and the integration method chosen would depend on this.

**Data Visualization**

The interface of the system is divided to three parts of the system screen, wherein one piece of the screen would be showing the trend graph of the industries in county level, this information is complemented with the heat map of Ireland which displays the information of jobs and accommodation. A user can modify his search option with the help of the search options available.

**Evaluation**

Our system aims at providing users with an aggregated information of jobs and accommodations for users to have more organised planning and time saving. Our system is targeted at being able provide a stable platform wherein users can navigate to the location place of work and at the same time get information on suitable accommodations and other sources around. The visualization which envelops the data helps the users to cut through the visual information overload and provides a better picture of what they actually are intending for. If the user is able to navigate through the website and narrow down through their requirements without any hindrance, then we could consider our system to be on track of being success.

There is no direct competitor in the market at the moment to compare and evaluate, so we had to evaluate our application against the current process of looking for information through various sources and websites.  The evaluation of our system for now is done focussing on two aspects

- Time taken to obtain information
- Independent user evaluation through surveys

**Time Analysis :**

To determine the time saved while using our application we offered a set of users (college grads and people opting for relocation) with some set of predetermined addresses and asked them to perform a set of tasks :

- Finding accommodations around a specific job location
- Distance between place of work and place of stay(accommodation)
- Determining the number of accommodations that they could find around their place of work.

A separate set of users would be asked to complete the same set of actions but following the general approach of browsing different websites for information.

**User Surveys :**

In the later stages of development we intend to evaluate the system by asking users to test it and provide feedback through surveys in google forms. The survey would focus on how relevant and accurate the information is being presented, the functionality of the system, user experience and feedback. Based on the obtained information further updates and analysis and design of the system would be carried out. Reason for opting google form is that it gives good analysis on the information and generates real time responses info and charts.

## **References and Key Resources**

1. 1)Indecon International Economic Consultants (for Department of Foreign Affairs and Trade) (2018).
2. 2)Indecon Economic Report on Addressing Challenges Faced by Returning Irish Emigrants. Dublin:
3. 3)Department of Foreign Affairs and Trade.
4. 4)Manduca, R (2014). Employment in America 2014. Where are the Jobs?. Retrieved from  http://www.robertmanduca.com/projects/jobs.html.
5. 5)Browse our Locations. Jobs.ie – Jobs in Ireland – Irish Jobs. Retrieved 17th June, 2018 from     [http://www.jobs.ie](http://www.jobs.ie)
6. 6) [https://www.nationalgeographic.com/environment/habitats/urban-threats/](https://www.nationalgeographic.com/environment/habitats/urban-threats/)
7. 7) [https://www.conserve-energy-future.com/causes-effects-solutions-urbanization.php](https://www.conserve-energy-future.com/causes-effects-solutions-urbanization.php)
8. 8) [http://www.technologystudent.com/designpro/system1.htm](http://www.technologystudent.com/designpro/system1.htm)
9. 9) [https://www.siliconrepublic.com/companies/accommodation-ireland-brexit](https://www.siliconrepublic.com/companies/accommodation-ireland-brexit)
10. 10) [https://www.siliconrepublic.com/companies/accommodation-crisis-dublin-san-francisco](https://www.siliconrepublic.com/companies/accommodation-crisis-dublin-san-francisco)
11. 11) [https://www.dublinlive.ie/news/dublin-news/dublins-housing-crisis-could-putting-13705263](https://www.dublinlive.ie/news/dublin-news/dublins-housing-crisis-could-putting-13705263)
12. 12) [https://materializecss.com/](https://materializecss.com/)
13. 13) [https://d3js.org/](https://d3js.org/)
14. 14) [https://developers.google.com/maps/documentation/javascript](https://developers.google.com/maps/documentation/javascript/tutorial)
15. 15)



        **Team         Name: JobMap**
