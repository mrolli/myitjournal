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

## Understanding the Database Itself

The data about our world is now store in a database. That makes it possible to
use the SQL languages to query the data and therefore ask questions that we
want answers for. To able to ask questions we first need to know what we can
ask for.

!!! abstract "Exercise 1 - What do we know about the world?"

    Try to answer the following questions:

    * What tables do we have to select data from? What might be their role?
    * Which data do we know about a single country?
    * What do we know about a single city?

    ??? hint "Hint"
        These questions can be answered using `SHOW` and `DESCRIBE` queries.

Now that you have inspected the individual tables, it's time to investigate
their relationships. From the real world we know that the world is composed
from continents and the continents are divided in countries.  
Every country has population and the people live in cities of different
sizes. Also people are talking different languages, sometimes more than one
within the same country.

!!! abstract "Exercise 2 - Relationships and ERDs"

    Try to draw a so called [Entity Relationship Diagram (ERD)][ERD] that shows
    all entities with some of their attributes especially those that are used
    to build relationships between the entities.

    [ERD]: https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model

## Journey Around the World

!!! abstract "Exercise 2 - Relationships and ERDs"

Let's move on start our journey around the world by investigating some fact and
getting the numbers. From counting simply counting countries to finding nifty
facts. The possibilities are endless and you are invited to create further
questions after you have solved all of mine.  
Talking about mine, the difficulty increased from question to question while new
feature of SQL are gradually introduced.


## Solutions

??? hint "Exercise 1"

??? hint "Exercise 2"

??? hint "Exercise 3"

    ```sql
    SELECT Name FROM country WHERE Name like 'M%';
    ```
