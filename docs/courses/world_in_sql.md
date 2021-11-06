## Preparations

Fetch the [world database](https://dev.mysql.com/doc/world-setup/en/world-setup-installation.html) to the
database server and import the schema and data. Just follow the guide provided
by the fore-mentioned page.

## Understanding the Database Itself

The data about our world is now store in a database. That makes it possible to
use the SQL languages to query the data and therefore ask questions that we
want answers for. To able to ask questions we first need to know what we can
ask for.

!!! abstract "Excercise 1 - What do we know about the world?"

    Try to answer the following questions:

    * What tables do we have to select data from?
    * What do we know about a country?
    * What do we know about a city?

    ??? hint "Hint"
        These questions can be answered using `SHOW` and `DESCRIBE` queries.

Now that you have inspected the individual tables, it's time to investigate
their relationships. From the real world we know that the worls is compsed
from continents and the continents are divided in contries.  
Every country has popuation and the the poeple live in cities of different
sizes. Also people are talking different languages, sometimes more than one
within the same country.

!!! abstract "Excersie 2 - Relationships and ERDs"

    Try to draw a so called [Entity Relationship Diagram (ERD)][ERD] that shows
    all entities with some of their attributes especially those that are used
    to build relationships between the entities.

    [ERD]: https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model

## Journey Around the World

## Solutions

??? hint "Excercise 1"

??? hint "Excercise 2"

??? hint "Excercise 3"

    ```sql
    SELECT Name FROM country WHERE Name like 'M%';
    ```
