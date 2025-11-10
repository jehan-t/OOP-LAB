# City Data Processing Project

This project demonstrates how to load and process city data from a CSV file using two custom classes: `DataLoader` and `Table`. The program filters cities by conditions, performs aggregations such as averages and maximum values, and counts unique country entries.

## Project Structure

project_folder/
- Cities.csv (data file that contains city information)
- main.py (main program code)
- README.md (this documentation)

## How It Works

1. **DataLoader Class**
   The `DataLoader` class loads data from a CSV file and returns it as a list of dictionaries. Each dictionary represents one row from the CSV.

2. **Table Class**
   The `Table` class stores a dataset and provides tools for:
   - `filter(condition)` — Returns a new `Table` containing only rows that satisfy the provided condition.
   - `aggregate(function, key)` — Applies an aggregation function (such as calculating average or maximum) to values associated with a given key.

## Operations Performed in the Program

The program prints:
1. The average temperature of all cities.
2. All cities located in Germany.
3. All cities located in Spain with a temperature above 12°C.
4. The total number of unique countries present in the dataset.
5. The average temperature of cities in Germany.
6. The maximum temperature among cities in Italy.

## Example CSV Format (Cities.csv)

city,country,temperature
Berlin,Germany,10
Munich,Germany,8
Madrid,Spain,14
Barcelona,Spain,13
Rome,Italy,18
Milan,Italy,15

## Requirements

- Python 3.8 or higher
- No external libraries required (only built-in modules)

## How to Run

Make sure you are in the project directory, then run:

python main.py