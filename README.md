# Lau Bermudez Tutorials

A comprehensive Python tutorial project demonstrating data management, database operations, and data analysis using pandas and SQLModel.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Usage](#usage)
  - [Download Penguin Dataset](#download-penguin-dataset)
  - [Create and Populate Database](#create-and-populate-database)
  - [Query Database with Pandas](#query-database-with-pandas)
- [Database Schema](#database-schema)
- [Dataset Information](#dataset-information)
- [Contributing](#contributing)

## 🎯 Overview

This project serves as a tutorial for working with Python data science tools, specifically focusing on:
- Downloading datasets from remote sources
- Creating and managing SQLite databases using SQLModel
- Reading and analyzing data with pandas
- Bridging SQL databases and pandas DataFrames

## ✨ Features

- **Data Download**: Automated download of the Palmer Penguins dataset
- **Database Management**: SQLModel-based ORM for creating and managing SQLite databases
- **Data Analysis**: Integration between SQLite and pandas for data analysis workflows
- **Multiple Examples**: Demonstrates both Hero/Villain database examples and real-world penguin dataset

## 📦 Prerequisites

Before running this project, ensure you have the following installed:

- Python 3.10 or higher (requires `|` union type syntax)
  - **Note**: For Python versions < 3.10, you'll need to use `Union[int, None]` from the `typing` module instead of `int | None`
- pip (Python package manager)

### Required Python Packages

- `pandas` - Data manipulation and analysis
- `sqlmodel` - SQL database ORM based on SQLAlchemy and Pydantic
- `requests` - HTTP library for downloading datasets
- `sqlite3` - Built-in Python SQLite interface (included with Python)

## 🚀 Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Davidnet/lau_bermudez_tutorials.git
   cd lau_bermudez_tutorials
   ```

2. **Create a virtual environment** (recommended):
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install pandas sqlmodel requests
   ```

## 📁 Project Structure

```
lau_bermudez_tutorials/
├── assets/
│   └── penguins.csv          # Palmer Penguins dataset (downloaded)
├── Download.py               # Script to download the penguin dataset
├── Interactive.py            # Create Hero/Villain database with SQLModel
├── Read_pandas.py            # Query database and return DataFrame
├── read_pandas.py            # Query database and print results
├── database.db              # SQLite database (generated)
├── .gitignore
└── README.md
```

## 💻 Usage

### Download Penguin Dataset

The `Download.py` script downloads the Palmer Penguins dataset from a GitHub Gist and saves it to the `assets/` folder.

```bash
python Download.py
```

**What it does**:
- Creates an `assets/` directory if it doesn't exist
- Downloads the penguins.csv file from the specified URL
- Saves the dataset locally for further analysis

### Create and Populate Database

The `Interactive.py` script demonstrates SQLModel usage by creating a SQLite database with Hero and Villain tables.

```bash
python Interactive.py
```

**What it does**:
- Defines `Hero` and `Villain` table models using SQLModel
- Creates a SQLite database (`database.db`)
- Populates the database with sample hero and villain data
- Demonstrates ORM usage with SQLModel's session management

**Example Models**:
```python
class Hero(SQLModel, table=True):
    id: int | None = Field(default=None, primary_key=True)
    name: str
    secret_name: str
    age: int | None = None
```

### Query Database with Pandas

Two scripts demonstrate reading data from the SQLite database into pandas DataFrames:

#### 1. Read and Print Results (`read_pandas.py`)

```bash
python read_pandas.py
```

Queries the `villano` table and prints the results to the console.

#### 2. Read and Return DataFrame (`Read_pandas.py`)

```bash
python Read_pandas.py
```

Queries the `villano` table and returns a pandas DataFrame (prints the type of the DataFrame head).

**Example Usage**:
```python
import pandas as pd
import sqlite3

# Connect to the database
conn = sqlite3.connect('database.db')

# Query data
query = "SELECT * FROM villano;"
df = pd.read_sql_query(query, conn)

# Close connection
conn.close()

# Analyze data
print(df.head())
```

## 🗄️ Database Schema

### Hero Table

| Column       | Type      | Description                    |
|-------------|-----------|--------------------------------|
| id          | INTEGER   | Primary key (auto-increment)   |
| name        | TEXT      | Hero's public name             |
| secret_name | TEXT      | Hero's secret identity         |
| age         | INTEGER   | Hero's age (nullable)          |

**Sample Data**:
- Deadpond (Dive Wilson)
- Spider-Boy (Pedro Parqueador)
- Rusty-Man (Tommy Sharp, age 48)

### Villano Table

| Column       | Type      | Description                    |
|-------------|-----------|--------------------------------|
| id          | INTEGER   | Primary key (auto-increment)   |
| name        | TEXT      | Villain's public name          |
| secret_name | TEXT      | Villain's secret identity      |
| age         | INTEGER   | Villain's age (nullable)       |

**Sample Data**:
- Joker (Arthur Fleck)
- Thanos (The Mad Titan)
- Voldemort (Tom Riddle)

## 🐧 Dataset Information

### Palmer Penguins Dataset

The project uses the Palmer Archipelago (Antarctica) penguin dataset, which includes measurements for penguin species.

**Columns**:
- `rowid` - Row identifier
- `species` - Penguin species (Adelie, Chinstrap, Gentoo)
- `island` - Island in Palmer Archipelago
- `bill_length_mm` - Bill length (millimeters)
- `bill_depth_mm` - Bill depth (millimeters)
- `flipper_length_mm` - Flipper length (millimeters)
- `body_mass_g` - Body mass (grams)
- `sex` - Penguin sex
- `year` - Year of observation

**Source**: [Palmer Penguins GitHub Gist](https://gist.github.com/slopp/ce3b90b9168f2f921784de84fa445651)

## 🤝 Contributing

This is a tutorial project. Feel free to:
- Fork the repository
- Create feature branches
- Submit pull requests with improvements
- Report issues or suggest enhancements

## 📝 Notes

- The database file (`database.db`) is generated when running `Interactive.py`
- The `.venv` directory is excluded from version control (see `.gitignore`)
- Python 3.10+ is required due to the use of modern type union syntax (`int | None`)

## 📚 Learning Resources

This project is ideal for learning:
- **SQLModel**: Type-safe SQL database interactions
- **Pandas**: Data analysis and manipulation
- **SQLite**: Lightweight database management
- **Data Pipeline**: From download to database to analysis

---

**Happy Learning! 🚀**
