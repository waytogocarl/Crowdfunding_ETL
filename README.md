# Crowdfunding_ETL

In this project I worked with a partner to complete an ETL pipeline using Python, Pandas, Regex, Numpy, and JSON to extract and transform the data we were given. With our cleaned and transformed data we created four CSV files to create a database in SQL, there we created an ERD diagram and performed several queries to ensure that our database was uploaded properly. 

In the first part of this project we extracted crowdfunding data from a Excel sheet, after reviewing the data types we created two data frames, one for Categories and one for Subcategories. We were able to perform splits, drops, list comprehnsion, and date conversions. We then exported as a CSV.

Here is a screenshot of the Category data we extracted from the original dataset and transformed into a new Dataframe:
<img width="277" alt="Screenshot 2025-01-06 at 9 19 01 PM" src="https://github.com/user-attachments/assets/2dee789c-c49e-466d-8208-93d89f55c37a" />

In the next part of this project, we created a Campaign Dataframe where we renamed several columns, created new columns, and converted some of the datatypes. Next, we merged the campaign dataframe with the two category and subcategory dataframes from the first part of the project. We then cleaned the dataframe by dropping duplicate columns. Finally, we exported as a CSV.

Here is a snapshot of a portion of the Dataframe created in this section (you can't see columns end_date, category_id, or	subcategory_id in this screenshot):
![Screenshot 2025-01-06 at 9 23 44 PM](https://github.com/user-attachments/assets/a2baab09-6394-4a0f-8c87-c5d3064bc247)

Lastly, we extracted data from the contacts excel sheet and used Pandas to create a new dataframe from the JSON data. We slpit the name column into first and last names, and cleaned the dataframe by dropping unnesscessary columns. We exported this to a CSV.


Here's a snapshot of the head of the cleaned Contacts dataframe:

<img width="484" alt="Screenshot 2025-01-06 at 9 28 55 PM" src="https://github.com/user-attachments/assets/b7984eaf-b23d-43ae-8798-d1d1f5cac86a" />



Next, we took all four of our exported CSVs and began to write a schemata in order to create an ERD diagram within PostgresSQL. We created a new database within SQL, then we uploaded our schemata and ran the code to create all four tables, which we then imported our CSV data into. Then we created an ERD, and ran several queries to confirm the data was imported properly.


Here's a bit of code from our schemata:

CREATE TABLE "contacts" (
    "contact_id" INT   NOT NULL,
    "first_name" VARCHAR(50)   NOT NULL,
    "last_name" VARCHAR(50)   NOT NULL,
    "email" VARCHAR   NOT NULL,
    CONSTRAINT "pk_contacts" PRIMARY KEY (
        "contact_id"
     )
);

CREATE TABLE "campaign" (
    "cf_id" INT   NOT NULL,
    "contact_id" INT   NOT NULL,
    "company_name" VARCHAR   NOT NULL,
    "description" TEXT   NOT NULL,
    "goal" NUMERIC(10,2)   NOT NULL,
    "pledged" NUMERIC(10,2)   NOT NULL,
    "outcome" VARCHAR   NOT NULL,
    "backers_count" INT   NOT NULL,
    "country" VARCHAR   NOT NULL,
    "currency" VARCHAR   NOT NULL,
    "launch_date" DATE   NOT NULL,
    "end_date" DATE   NOT NULL,
    "category_id" VARCHAR   NOT NULL,
    "subcategory_id" VARCHAR   NOT NULL,
    CONSTRAINT "pk_campaign" PRIMARY KEY (
        "cf_id"
     )
);


Here's a screenshot of our ERD diagram:

![crowdfunding_db_schema_erd](https://github.com/user-attachments/assets/3cc98c4c-67b7-4493-8fa6-a24842cc72b0)


We saved all our files to our repository and pushed the updates and changes to GitHub.


