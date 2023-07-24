# Tutorial: Connecting Python and SQL

This tutorial provides step-by-step instructions on how to connect Python and SQL (with a PostgreSQL database), allowing you to interact with databases using Python. By the end of this tutorial, you'll be able to establish connections, execute SQL queries, and retrieve data from a SQL database using Python.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Python and SQL Integration](#python-and-sql-integration)

<!-- - [Contributing](#contributing)
- [License](#license) -->

## Prerequisites

Before you begin, ensure you have the following prerequisites in place:

- Python (version X.X or higher) installed. You can download Python from [here](https://www.python.org/downloads/).
- SQL database (PostgreSQL) installed and running tutorial [here](#PostgreSQL).

## Installation

### Repo

1. Clone this repository: `git clone https://github.com/camilasbraz/python-sql.git`

2. Change to the tutorial directory: `cd your-repo`

4. Create a new virtual environment for the notebook with this [tutorial](https://github.com/camilasbraz/virtual-envs-ands-notebooks) and activate it

5. Install the required dependencies using pip: `pip install -r requirements.txt`

### PostgreSQL

PostgreSQL is an open-source relational database management system. This guide will help you get started with PostgreSQL and use it for your projects.

#### Installation

1. Download the PostgreSQL installer suitable for your operating system from the official website [here](https://www.postgresql.org/download/).
2. Follow the installation instructions for your specific platform.

#### Set Up PostgreSQL

1. During installation, you'll be prompted to set a password for the default PostgreSQL user, 'postgres.' Remember this password as you'll need it later.

#### Start/Stop the PostgreSQL Server

1. After installation, the PostgreSQL server should start automatically. If not, you can start it from the Services or System Preferences panel, depending on your operating system.
2. To stop the server, use the corresponding service management tools.

#### Access PostgreSQL

1. PostgreSQL includes a powerful command-line tool called `psql`, which allows you to interact with the database.
2. Open the `SQL Shell (psql program)`:

<!-- ```terminal
psql -U postgres
``` -->

3. You will be prompted to enter the password you set for the 'postgres' user during installation.

#### Create a Database and User

1. By default, PostgreSQL comes with a user named 'postgres' with administrative privileges. It's recommended not to use this user for regular application purposes. Instead, create a new user and database for your application.
2. In the `psql` prompt, you can create a new database and user with the following SQL commands:

```sql
-- Create a new user (replace 'your_user' and 'your_password' with your desired values):
CREATE USER your_user WITH PASSWORD 'your_password';

-- Create a new database (replace 'your_database' and 'your_user' with your desired values):
CREATE DATABASE your_database OWNER your_user;
```

#### Connect to a Database

1. To connect to a specific database using the newly created user, use the following command:

```terminal
psql -U your_user -d your_database
```
<!-- psql -U camilabraz -d starwars; -->

#### Execute SQL Commands

1. Once connected to the database, you can execute SQL commands to create tables, insert data, query data, and perform other database operations.
2. Here's an example of creating a simple table and inserting some data:

```sql
-- Create a new table:
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

-- Insert data into the table:
INSERT INTO users (name, age) VALUES ('John Doe', 30), ('Jane Smith', 25);
```
3. It is possible to use a `.sql` file with SQL commands inside it like `database.sql`. To do that in Windows, you have to use the `\i <file_name>`
command in the command line tool. The `file_name` should be tha file path in single quotes and forward slashes such as `\i 'C:/path/createdatabase.sql'`

<!-- #### Exit psql

1. To exit the psql command-line tool, type:

```terminal
\q 
```-->

## Usage

1. Create a `.env` file with your database connection details:

```python
# Database configuration
DB_HOST = 'your-database-host' # Localhost
DB_PORT = 'your-database-port' # Default: 5432
DB_NAME = 'your-database-name'
DB_USER = 'your-database-username'
DB_PASSWORD = 'your-database-password'
```
 
2. Run the `python-sql.ipynb` notebook

## Python and SQL Integration

Python and SQL integration is a powerful combination that allows developers to leverage the strengths of both technologies. Python provides a versatile programming language with a rich ecosystem of libraries and tools, while SQL (Structured Query Language) is a standard language for managing and manipulating relational databases. Here are some key points on integrating Python and SQL:

### Database Connectivity

Python provides various libraries and drivers that enable connecting to SQL databases, such as MySQL, PostgreSQL, SQLite, and more. These libraries offer functions and classes to establish connections, execute SQL statements, and handle database transactions. Some popular libraries for Python and SQL integration include:

- **`sqlite3`**: The `sqlite3` module comes built-in with Python and provides a lightweight and efficient way to interact with SQLite databases.
- **`psycopg2`**: `psycopg2` is a PostgreSQL adapter for Python, allowing you to connect and interact with PostgreSQL databases.
- **`mysql-connector-python`**: This library enables Python applications to connect to MySQL databases and execute SQL queries.
- **`pyodbc`**: `pyodbc` is an open-source Python module that enables connections to a wide range of databases using ODBC (Open Database Connectivity).

### Data Manipulation

With Python's flexibility and SQL's querying capabilities, you can perform a wide range of data manipulation tasks. Python allows you to fetch data from a SQL database, process it using Python's built-in functions or external libraries, and then update or insert the processed data back into the database. Some common data manipulation tasks include:

- **Data Retrieval**: You can execute SQL SELECT statements to retrieve data from the database. Python libraries provide functions to fetch the data into Python data structures, such as lists or DataFrames, making it easy to work with the retrieved data.

- **Data Modification**: SQL UPDATE and INSERT statements can be executed through Python to modify the data stored in the database. Python variables or data structures can be used to provide values for the SQL statements, allowing for dynamic and parameterized queries.

- **Data Transformation**: Python provides extensive libraries for data manipulation, such as Pandas, NumPy, and SciPy. You can retrieve data from a SQL database and utilize these libraries to perform complex transformations, calculations, and data cleaning tasks.

### Automation and Scripting

Integrating Python and SQL enables you to automate database-related tasks. You can write Python scripts that perform routine operations like data migration, data extraction, data cleaning, or generating reports, using SQL queries and Python logic. Some examples of automation and scripting tasks include:

- **Data Migration**: Python can be used to migrate data between different databases. By connecting to the source and destination databases, you can retrieve data from the source database using SQL queries and insert it into the destination database.

- **Scheduled Jobs**: Using Python's scheduling libraries like `cron` or `schedule`, you can automate the execution of SQL queries or scripts at specific intervals. This allows you to perform tasks such as data backups, data updates, or running periodic reports.

- **Data Extraction**: Python can be used to extract data from various sources, including SQL databases, and transform it into a desired format. You can automate the extraction process by writing Python scripts that execute SQL queries and save the results in a specific format or location.

### Data Analysis and Visualization

Python's extensive data analysis and visualization libraries can be seamlessly integrated with SQL databases. This integration allows you to retrieve data from a SQL database, analyze it, perform statistical calculations, and visualize the results using Python's plotting capabilities. Here are some popular libraries for data analysis and visualization in Python:

- **Pandas**: Pandas provides powerful data structures and data analysis tools. You can retrieve data from SQL databases into Pandas DataFrames and perform various data manipulations, aggregations, filtering, and calculations.

- **NumPy**: NumPy is a fundamental library for numerical computing in Python. It provides support for large, multi-dimensional arrays and mathematical functions. You can use NumPy in conjunction with SQL data to perform advanced calculations and statistical analysis.

- **Matplotlib**: Matplotlib is a widely-used plotting library in Python. It allows you to create various types of visualizations, including line plots, bar charts, histograms, scatter plots, and more. You can plot data retrieved from a SQL database to gain insights and communicate your findings effectively.

- **Seaborn**: Seaborn is a statistical data visualization library that is built on top of Matplotlib. It provides a high-level interface for creating informative and attractive statistical graphics. With Seaborn, you can easily create advanced visualizations such as distribution plots, regression plots, categorical plots, and more.

- **Bokeh**: Bokeh is a powerful interactive visualization library that targets modern web browsers. It provides elegant and interactive visualizations for displaying large and complex datasets. With Bokeh, you can create interactive plots, dashboards, and applications that allow users to explore and interact with the data.

- **TensorFlow**: TensorFlow is a powerful library for machine learning and deep learning. It includes tools for building and training machine learning models, including neural networks. You can integrate TensorFlow with SQL databases to retrieve training data, preprocess it, and use it for model training and evaluation.

- **scikit-learn**: scikit-learn is a popular machine learning library in Python. It provides a wide range of machine learning algorithms and tools for tasks such as classification, regression, clustering, and dimensionality reduction. By combining scikit-learn with SQL databases, you can leverage the data stored in the database for training and evaluating machine learning models.

- **PyTorch**: PyTorch is another popular library for deep learning. It provides a flexible and efficient framework for building neural networks and performing deep learning tasks. You can integrate PyTorch with SQL databases to fetch data for model training, preprocess it, and use it to train and evaluate deep learning models.

These libraries offer a wide range of capabilities for data analysis, statistical modeling, and machine learning. By integrating them with SQL databases, you can leverage the data stored in the database to gain insights, make data-driven decisions and build advanced machine learning models.
