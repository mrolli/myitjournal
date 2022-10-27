There are many relational databases out there and all of them have the **SQL - the
Structured Query Langauge** - in common though different dialects exist. Knowing
SQL at least on a basic to intermediate level is beneficial for the every day
life of an IT guy as you never know where you'll encounter it and it empowers
you to use something better than Excel when solving a more complex task around
data.

The course here is built on exercises that get gradually more difficult. You are
encouraged to solve the exercises by yourself! Believe me, the best way to learn
SQL is by starting with basic queries and then add up the restrictions you have.
While you then and when land in a dead end, you still learned a lot, at least a
way not to do it! You then start a new approach to question and try to make the
query more complex again until you have the solution you want. If all fails, you
can find the solutions at the end of the page. Keep in mind, three is often more
than one solution.

## Preparations

Fetch the [world
database](https://dev.mysql.com/doc/world-setup/en/world-setup-installation.html)
to the database server and import the schema and data. Just follow the guide
provided by the fore-mentioned page. If you do not have an SQL server yet, you
might want to follow the [webappstack course](webappstack.md) or fetch a
pre-built VM from the internet featuring MariaDB or any other relational
database that speaks SQL.

## Journey Around the World

### Understanding the Database

The data about our world is now store in a database. That makes it possible to
use the SQL languages to query the data and therefore ask questions that we
want answers for. To able to ask questions we first need to know what we can
ask for.

!!! abstract "Exercise 1 - What do we know about the world?"
    Try to answer the following questions:

    - What tables do we have to select data from? What might be their role?
    - Which data do we know about a single country?
    - What do we know about a single city?


Now that you have inspected the individual tables, it's time to investigate
their relationships. From the real world we know that the world is composed
from continents and the continents are divided in countries.  
Every country has population and the people live in cities of different
sizes. Also people are talking different languages, sometimes more than one
within the same country.

!!! abstract "Exercise 2 - Relationships and ERD"
    Try to draw an [Entity Relationship Diagram (ERD)][ERD] that shows all
    entities with some of their attributes especially those that are used to
    build relationships between the entities.

    [ERD]: https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model

Let's start our journey around the world by investigating some facts and
getting the numbers. From counting simply counting countries to finding nifty
facts. The possibilities are endless and you are invited to create further
questions after you have solved all of mine.  
Talking about mine, the difficulty increased from question to question while new
feature of SQL are gradually introduced.

### Basic Data Selection

!!! abstract "Exercise 3 - Countries in the World"
    - Create a list of all countries and their country code.
    - How many countries are known to the database.
    - Which countries start with the letter M?
    - What's the population of Switzerland?

Aren't you surprised? Are there really only 7.1 millions of people in
Switzerland. Shouldn't there be more than 8 millions already? Yes, the data we
are dealing with is quite old! We will see this at other places too!

Let's talk about continents and regions now. We know that there are the columns
continent and region. That means, every country belongs to a region and a
continent. Some countries are in the same region or on the same continent.

!!! abstract "Exercise 4 - Relationships, anyone? - an excursion"
    Attribute continent as well as attribute region are modeled as columns here.
    Is this a good choice? Are there other, better possibilities to model these
    relationships? How would you model the relationships between continents,
    regions and countries? Draw a better ERD for these relationships.

Now back to selecting data in our country table. As regions and continents are
not normalized we have to select a little different and have to use special
select flavors.

!!! abstract "Exercise 5 - From continents and regions"
    - Can you fetch a list of all continents and their regions ordered first by
      continent and then by region?
    - Can you fetch the list of countries that belong to Europe but not to the
      following regions:
        - Western Europe
        - British Islands
        - Nordic Countries
    - How many of the above are known to the database?


## Hints and Solutions

### Understanding the Database

??? hint "Hints ex 1 - What do we know about the world?"
    These questions can be answered using [DESCRIBE] statement, [SHOW TABLES ]
    statement or [SHOW COLUMNS] statement. Then examine the output carefully
    and try to figure out what data is stored in these columns.
    Bonus question: What is the difference between the [DESCRIBE] and [SHOW
    COLUMNS]?
    ??? hint "Solution"
        ```sql
        USE world;
        SHOW TABLES;
        DESCRIBE country;
        DESCRIBE countrylanguage;
        DESCRIBE city;
        SHOW COLUMNS FROM city;
        ```


??? hint "Hints ex 2 - Relationships and ERD"
    An entity relationship diagram show things with the attributes and the
    relationships between the things. In our case we have the countries, cities
    that belong to countries and languages that are spoken in these countries.  
    The cities are matched to their countries by the country code. The same
    goes for the languages. Therefore the countrycode is a foreign key of
    cities and languages to build a relationship to the countries.

    You can draw an ERD on paper or any tool you like. The following solution
    is done by using Mermaid.js that is thankfully already built-in in
    mkdocs-material.
    ??? hint "Solution"
        ```mermaid
        erDiagram
            COUNTRY {
                string Code PK "The country code"
                string Name
                enum Continent "'Asia','Europe','North America','Africa','Oceania','Antarctica','South America'"
                string Region
                decimal SurfaceArea
            }
            COUNTRY ||--o{ CITY : has
            CITY {
                int ID PK "The primary Key"
                string Name
                string CountryCode FK "The country code"
                string District
                int Population "default: 0"
            }
            COUNTRY ||--o{ COUNTRYLANGUAGE : has
            COUNTRYLANGUAGE {
                string CountryCode FK "The country code"
                string
                Language
                enum IsOfficial "T, F default: F"
                decimal Percentage
            }
        ```

### Basic Data Selection

??? hint "Hints ex 3 - Countries in the world"
    - To answer the first exercise select only the columns name and country code
    - For the second question you have to use the [COUNT] function.
    - To answer the last question you have to narfrow down the results using a
    [WHERE] clause with a [LIKE] operator
    ??? hint "Solution"
        ```sql
        SELECT Name, Code FROM country;
        SELECT count(Code) FROM country;
        SELECT Name FROM country WHERE Name like 'M%';
        SELECT Population FROM country WHERE Name = 'Switzerland';
        ```

??? hint "Hints ex 4 - Relationships, anyone?"
    Both attributes are not normalized, which means their string values occurr
    multiple times in the column. When adding new country there's a chance for
    typos, i.e. 'Europ' instead of 'Europe' and this country would then not bei on
    the content. Therefore we would normally normalize both to their own tables
    and add primary and foreign key to reference the data. Can you come up with
    a solution for a fully normalized country, region, continent relationship?
    ??? hint "Solution"
        ```mermaid
        erDiagram
            CONTINENT {
                int ID PK "The identifier of the continent"
                string Name
            }
            CONTINENT ||--|{ REGION : divded_in
            REGION {
                int ID PK "The identifier of the region"
                string Name
                int Continent FK "The identifier of the continent"
            }
            COUNTRY {
                string Code PK "The country code"
                string Name
                int Region FK "The identifier to the Region"
            }
            REGION ||--|{ COUNTRY : has
        ```

??? hint "Hints ex 5 - From continents and regions"
    If you use a standard [SELECT] statement, you will have way too many row in
    your output, namely one for each country. So there must be a way to sort out
    doubles to only have a distinct set of results.
    For the second and third question, there are many solutions. Try to find at
    least two. One of them should use the given regions and state that the
    countries should not be in these regions.
    ??? hint "Solution"
        ```sql
            SELECT DISTINCT Continent, Region FROM country ORDER BY Continent, Region;
            SELECT Name, Region FROM country WHERE Continent='Europe' AND Region NOT IN ('Western Europe', 'British Islands', 'Nordic Countries');
            a) SELECT count(Name) FROM country WHERE Continent='Europe' AND Region NOT IN ('Western Europe', 'British Islands', 'Nordic Countries');
            b) SELECT count(Name) FROM country WHERE Continent='Europe' AND (Region = 'Baltic Countries' OR Region = 'Southern Europe' OR Region = 'Eastern Europe');
        ```
        !!! warning ""
            The WHERE clause "Continent='Europe'" is not necessary as
            the selected regions are in Europe anyway.  
            The above two queries only lead to the same result if there are no
            countries not belonging to these regions in both queries.

??? hint "Hints ex X"
    ??? hint "Solution"
        ```sql
        ```

[COUNT]: https://mariadb.com/kb/en/count/
[DESCRIBE]: https://mariadb.com/kb/en/describe/
<!-- [LIKE]: https://www.w3schools.blog/like-operator-mariadb -->
[LIKE]: https://mariadb.com/kb/en/like/
<!-- [WHERE]: https://www.w3schools.blog/where-clause-mariadb -->
[SELECT]: https://mariadb.com/kb/en/select/
[SHOW COLUMNS]: https://mariadb.com/kb/en/show-columns/
[SHOW TABLES]: https://mariadb.com/kb/en/show-tables/
[WHERE]: https://mariadb.com/kb/en/select/
