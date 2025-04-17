# NotionInterface

A simple Python interface for interacting with Notion databases and pages. This library provides utilities to query, manipulate, and export data from Notion databases using the Notion API.

## Features

- Retrieve and manipulate Notion databases and pages.
- Export Notion database records to Excel files.
- Support for various Notion property types (e.g., title, rich text, multi-select, date, people, etc.).
- Recursive retrieval of child databases and pages.

## Installation

To install the library, clone this repository and run:

```bash
pip install .
```

Alternatively, you can install the dependencies manually by running:

```bash
pip install -r requirements.txt
```

## Usage

### Initialization

To use the library, import the relevant classes and initialize them with your Notion API key and database or page ID.

```python
from NotionInterface import NotionDatabase, NotionPage

# Initialize a Notion database
database = NotionDatabase(database_id="your_database_id", notion_key="your_api_key")

# Initialize a Notion page
page = NotionPage(page_id="your_page_id", notion_key="your_api_key")
```

### Retrieve Database Columns

```python
columns = database.getColumns()
print(columns)
```

### Retrieve All Records

```python
records = database.getAllRecords()
print(records)
```

### Export Records to Excel

```python
database.ConvertToExcel(path="output.xlsx")
```

### Retrieve Child Databases from a Page

```python
child_databases = page.getChildDataBase(page_id="your_page_id")
print(child_databases)
```

### Add or Edit Records

To add a new record:

```python
record = {
    "properties": {
        "Name": "New Record",
        "Status": "In Progress"
    }
}
record_id = database.putRecord(record)
print(f"Record added with ID: {record_id}")
```

To edit an existing record:

```python
record = {
    "properties": {
        "Status": "Completed"
    }
}
database.editRecord(pageId="existing_page_id", record=record)
```

## Project Structure

```
NotionInterface/
├── __init__.py
├── constants.py
├── notion_database.py
├── notion_database_types.py
├── notion_header.py
├── notion_page.py
```

- **`notion_database.py`**: Contains the `NotionDatabase` class for interacting with Notion databases.
- **`notion_page.py`**: Contains the `NotionPage` class for interacting with Notion pages.
- **`notion_database_types.py`**: Utility functions for handling Notion property types.
- **`notion_header.py`**: Helper function to generate API headers.
- **`constants.py`**: Contains error messages and constants.

## Requirements

The project requires the following Python packages:

- `requests`
- `pandas`
- `openpyxl`
- `dateutil`

You can install them using:

```bash
pip install -r requirements.txt
```

## Development

To contribute to this project:

1. Clone the repository.
2. Install the dependencies.
3. Make your changes and submit a pull request.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Author

Developed by LukaPedra (Lucca Rocha). For inquiries, contact: `<lucca.v.rocha@gmail.com>`.