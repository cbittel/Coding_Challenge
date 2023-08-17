# Coding_Challenge - OpenAI ChatGPT / Google BARD - Generated code

# Historical Data CSV Flask Endpoint

The `historical_data_csv` Flask endpoint is designed to process and save historical data from CSV files into an SQLite3 database. This endpoint can handle multiple CSV files, generate column names if headers are missing, and process data in batches. It provides an easy way to save historical data into a structured database for analysis and storage.

## Usage

1. **Endpoint URL:** `/historical_data_csv`
2. **HTTP Method:** POST
3. **Parameters:** List of CSV files

### Request

To use the endpoint, send a POST request with a list of CSV files as parameters. The CSV files should be attached as `files` in the request's `multipart/form-data`.

### Response

The endpoint processes the CSV files, creates an SQLite3 database, and saves the data into separate tables named after the filenames (without the '.csv' extension). If headers are missing in the CSV files, column names will be generated as 'col1', 'col2', etc.

Upon successful processing, the endpoint will respond with a JSON message: `"Data successfully processed and saved"`.

### Example

Below is an example using Python's `requests` library to send a POST request to the endpoint:

```python
import requests

url = "http://your-flask-server/historical_data_csv"

files = [
    ('files', ('file1.csv', open('file1.csv', 'rb'))),
    ('files', ('file2.csv', open('file2.csv', 'rb'))),
    ('files', ('file3.csv', open('file3.csv', 'rb')))
]

The main application module is : 
https://nbviewer.org/github/cbittel/Coding_Challenge/blob/main/Section1_API.ipynb

The test module for the application is :
https://nbviewer.org/github/cbittel/Coding_Challenge/blob/main/test_Section1_API.ipynb
response = requests.post(url, files=files)

if response.status_code == 200:
    print(response.json())
else:
    print("Error:", response.text)
