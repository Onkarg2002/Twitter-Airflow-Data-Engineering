# Twitter Airflow Data Engineering Project

This project implements a data engineering pipeline that extracts, transforms, and loads (ETL) Twitter data using Apache Airflow. The pipeline is designed to automate the process of collecting tweets from specific Twitter accounts, processing the data, and storing it in a CSV file for further analysis.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Setup Instructions](#setup-instructions)
- [Usage](#usage)
- [DAG Details](#dag-details)
- [Contributing](#contributing)
- [License](#license)

## Project Overview

The objective of this project is to create an automated data pipeline using Apache Airflow to ingest Twitter data. The pipeline collects tweets from specified Twitter users (e.g., @elonmusk), processes the data (e.g., cleaning, filtering), and stores the cleaned data into a CSV file for later use.

## Features

- Automated extraction of tweets using the Twitter API.
- Data transformation using Python and Pandas.
- CSV file storage for further analysis.
- ETL process orchestrated and scheduled with Apache Airflow.

## Technologies Used

- **Apache Airflow**: For orchestrating and scheduling the ETL pipeline.
- **Python**: For scripting and data transformation.
- **Tweepy**: To interact with the Twitter API.
- **Pandas**: For data manipulation and transformation.
- **s3fs**: For potential future integration with Amazon S3.

## Setup Instructions

### Prerequisites

- Ubuntu or a compatible Linux distribution.
- Python 3.x installed.
- Twitter Developer Account (for API access).

### Installation

1. **Update your package list:**
    ```bash
    sudo apt-get update
    ```

2. **Install Python pip:**
    ```bash
    sudo apt install python3-pip
    ```

3. **Install Apache Airflow:**
    ```bash
    sudo pip install apache-airflow
    ```

4. **Install required Python packages:**
    ```bash
    sudo pip install pandas
    sudo pip install s3fs
    sudo pip install tweepy
    ```

5. **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/twitter-airflow-data-engineering.git
    cd twitter-airflow-data-engineering
    ```

### Twitter API Setup

1. Obtain your Twitter API credentials by creating an app in the [Twitter Developer Portal](https://developer.twitter.com/).
2. Add your credentials to the `run_twitter_etl` function in the `twitter_etl.py` script:

    ```python
    access_key = "your_access_key" 
    access_secret = "your_access_secret" 
    consumer_key = "your_consumer_key"
    consumer_secret = "your_consumer_secret"
    ```

## Usage

1. **Start the Airflow web server and scheduler:**
    ```bash
    airflow webserver --port 8080
    airflow scheduler
    ```

2. **Access the Airflow web interface:**
    - Open your browser and go to `http://localhost:8080`.
    - Trigger the `twitter_dag` DAG to start the ETL process.

3. **Check the output:**
    - After the DAG runs successfully, you should find the extracted and transformed tweets in the `refined_tweets.csv` file in your project directory.

## DAG Details

- **DAG ID**: `twitter_dag`
- **Description**: ETL pipeline to extract tweets from Twitter, transform the data, and save it as a CSV file.
- **Schedule**: Runs daily.
- **Tasks**:
    - `complete_twitter_etl`: Executes the `run_twitter_etl` function, which handles the entire ETL process.

### Directory Structure

├── dags/
│ └── twitter_etl_dag.py
├── logs/
├── twitter_etl.py
├── refined_tweets.csv (generated after running the DAG)
├── requirements.txt
└── README.md
