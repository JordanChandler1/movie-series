
# Movie Series Database Project

## Challenge

The objective of this project is to design a hypothetical relational database that portrays some aspect of your favorite TV show or movie. This database should contain at least 4 tables, 3 primary keys, and 2 foreign keys. Other database artifacts are encouraged if appropriate. Each table should serve a clear distinct purpose that adds value to another table or the database as a whole.  Produce an ER diagram and explain how you would populate the database via web scraping from IMDB.

## Design Approach

My design is centered around my love of movie trilogies or other extended series. My design approach as both the product owner and product manager is to:

1. Define a preliminary elevator pitch given the challenge requirements.
1. Research the field, existing products, and competitive landscape.
1. Identify key sources of inspiration and information.
1. Propose preliminary user stories.
1. Story map the stories.
1. Review the story map and stories with the product owner.
1. Choose as the initial story the story that will provide the most customer value.
1. Design to the initial story.
1. Verify design outcomes with prototypical end users.

## Elevator Pitch

ILOVEMOVIES is a freemium subscription searchable movie database for people that love movie trilogies.  Unlike IMDB, users can use ILOVEMOVIES to easily find movies that are a part of an extended movie series and know that the movie they are watch has much more to offer.

## Research

The most obvious starting point is the well known [IMDB](www.imdb.com).  As shown below the site has a basic search function that allows simple searches on Titles, TV Episodes, Celebs, Companies, and Keywords.

![IBDB search bar](/assets/imdb_search_bar.png)

An "Advanced Search" dialog (shown below) is also able to query by Plot, Quotes, Trivia, Goofs, Crazy Credits, Filming Locations, Soundtracks, and Biographies.

![IMDB advanced search dialog](/assets/imdb_advanced_search_dialog.png)

There is no search mechanism for finding extended movie series.  That said, IMDB has have static web pages dedicated to movies meeting specific criteria including movies that have 2 or more sequels but these appear not to be based on static rather than dynamic searches and are thus dated and therefore more and more inaccurate as time progresses.

## Sources of inspirations and information

We will use one of these [IMDB movies with 2 or more sequels (circa 2013)](https://www.imdb.com/list/ls051309584/) to populate our database as the project progress dedicate additional time to finding more recent movie lists.  

## User Stories

### Story 1

As a fan of movie trilogies and other extended movie series such as the original Star Wars trilogy and later related movies, I want to find movie series that with movies produced within a given date range, of a certain genre, that received an award or certain awards, that have a least a given number of sequels so that I can learn of movie series that match my interests or requirements.

### Story 2

As a fan of movie trilogies and other extended movie series such as the original Star Wars trilogy and other later movies, I want to find information about the series, the series' titles, casts, crews, awards. 

## Story Map

1. User searches Google for movie trilogies and finds links (at the top of the page of course) to ILUV3S.
1. Clicking on the link, the ILUV3s home page is displayed with a montage of clickable images of movie trilogies selected to most engage the first time visitor.
1. The user sees a movie series of interest and clicks.  The system displays a movie series dashboard page which shows information about the movie series, its titles, casts, crews, and awards.
1. After exploring this page and its subpages for a while, the user returns to the home page and notices the ILUV3s search bar.  Clicking on this search bar displays a page that allows the user to search for movie series  or sequels within a movie series made within a given date range, of a certain genre, that received an award or certain awards, and/or that have a least a given number of sequels within the series.  On a successful search the user see a list of matching movie series.
Click one of these links displays the movie series dashboard as described above.

## Design

We will use the noun of the search result in the user stories as the basis for our relational tables.  These include:

- Series
- Titles
- Casts
- Crews
- Awards

We will also consider the nouns of the IMDB search when evaluating or extending our design These include:

- Titles
- Episodes
- Celebs,
- Companies
- Keywords
- Plot
- Quotes
- Trivia  
- Goofs
- Crazy Credits
- Filming Locations
- Soundtracks
- Biographies

For attributes, we will use as a starting point the IMDB movie page and related pages for a specific movie (shown below) and note in addition to attributes such as description, genre, etc., people and the roles within the movie such as directors, writers, and cast are a big part of any movie.

![The Godfather(1972)](/assets/imdb_movie_godfather.png)

The design must allow for people, factor out their commonalities (i.e. by normalizing),  and constrain their roles.

The proposed database will include the following entities:

- Series: A system created entity that represents a group of related movies.
- Sequel: A movie that belongs to a series
- Genre: A type of movie
- People: A person that helped create the movie
- PeopleRole: The roles of the people when creating the movie
- Award:
- Organization:
- OrganizationRole

Our tables will consist of:

Series
SeriesProductions
Productions
ProductionWorkers
ProductionAwards
Genres
Workers
WorkerAwards
WorkRoles
WorkTypes
Awards
AwardTypes

## Entity Relationship Diagram

The entity-relationship diagram for the database is shown below.

![Entity Relationship Diagram](/assets/movie-series-entity-relationship-diagram.svg)

## Database ETL

My proposed steps to populate the Movie Series database with 100 movies, their IMDb IDs, and their release years is as follows:
1.	Identify sources of IMDb data available via the Internet.  Of course, the primary source is IMDb but we should consider whether there are other sources available which might be easier to access or provide better legal terms.
1. Understand the copyright claims made by the source over the IMDb data.  If the data can be legally obtained and used for the intended purpose without any contractual terms with the source, proceed to extract the data as outlined below.
1.	If the data, needs to be licensed from the source, do so.  In the case of IMDB this web scraping will not be allowed so this discuss is hypothetical only.
1.	Decide the extraction strategy.  If possible, extract the data using a source provided API.
1.	If not possible, decide which web scraping strategy to use from the list below:
    1.	Use a web scraping vendor such as Agenty (https://www.agenty.com), Mozenda (http://www.mozenda.com), etc. to configure and perform web scraping in the cloud.
    1.	Use desktop web scraping tools such as:
        1.	Web Scraper
        1.	ParseHub
    1.	Use a web scraping browser extension such as Apify
    1.	Use a web scrapping software library callable from a high-performance language such as C/C++/Rust.
    1.	Use a web scrapping software library callable from a high-level language such as Python, Java,
    1.	Performing local level web requests that return HTML and parse the data with RegEx, grep, or other generalized text search libraries.
1.	The data will be obtain from IMDb and stored in a relation database such as PostGreSQL, MySQL, or SQL Server in the cloud or on premise is required.
