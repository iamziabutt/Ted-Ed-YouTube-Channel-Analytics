## TED-ED YouTubee Channel Analytics in MongoDB

This project helps to understand YouTube Channel videos by processing the API data in MongoDB and AWS S3.

### ✨Goals

- To gain hands-on experience with:
- API ingestion with error handling
- MongoDB CRUD operations
- Basic ETL pipeline design
- Cloud storage integration
- Data analysis/visualization

### ✨Plan

1. I shall be extracting data from the YouTube Data API (for TED-ED channel) by using `Google Development Console`. I created a project called `TED-ED YouTube Analytics` and requested an API key
2. I shall then load the data into MongoDB collection. Database name shall be `ted_ed_analytics` and I will create a collection `vidoes` in this database. This collection will store results from YouTube API response called `documents`. Each document will be unique in `json` format.
3. Transforming the data (apply business logic) in MongoDB using Python
4. Writes the transformed data to `AWS S3`, partitioned by year and month (based on the published date of the video)
5. Analyzing and visualizing the data in a `Jupyter Notebook` by reading from S3

### ✨System Configurations
- Python 3.12.0
- MongoDB 8.0.11 (with MongoDB Compass installed on windows 11)

### ✨Project Structure

```
text
Teded-Youtube-Analytics /
├── .venv/                # virtual environment to install required pythyon packages
├── scripts/              # juyper notebooks for ETL and analysis
|   ├── 1.extract.ipynb
|   ├── 2.transform.ipynb
|   ├── 3.load.ipynb
|   ├── 4.analysis.ipynb
├── credentials.ini       # for storing secrets
├── settings              # for storing common parameters for YouTube and MongoDB
├── resources             # storing Markdown file resources
```

### ✨Virtual ennvironment setup in Powershell

```
powershell

# Create project dir:
mkdir ted-ed-analytics;
cd ted-ed-analytics

# Create virtual env:
python -m venv .ven

# change the execution policy persistently for your user account:
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser -Force

# Activate env:
.\.venv\Scripts\Activate.ps1

# Install packages
pip install pymongo pandas requests configparser boto3 textblob
```

### ✨MongoDB Settings

- Hosting on URI `mongodb://localhost:27017` and this could be tested in `MongoDB Compass`
- In Compass, I have established a connection called 'TedEd-Youtube-Analytics' that have below databases:
    - admin
    - config
    - local
    - ted_ed_analytics (available in `settings.py`)

In `ted_ed_analytics` database, we have a collection called `videos` which have total 1774 `documents` in `json` format.

- Also downloaded `MongoDB` shell and ran below commands:

![Reference Image](/resources/MongoDB%20-%20Compass%20-%20Connection.png)

![Reference Image](/resources/MongoSH%20-%20Session%20launch.png)


## ✨AWS S3 Settings

Data was uploaded successfully from `load.ipynb` and we could see `csv` files that are partitioned by the month and year

![Reference Image](/resources/S3-bucket.png)

## ✨Execute Workflow

- Configure credentials.ini with your keys
- Activate virtual environment: `.\venv\Scripts\Activate.ps1`