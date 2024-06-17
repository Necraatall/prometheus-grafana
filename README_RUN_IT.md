# Define the path to the README file
readme_file_path = os.path.join(extraction_dir, 'prometheus-grafana', 'README_RUN_IT.md')

## Introduction

This project contains configurations for running Prometheus, Grafana, Node Exporter, and the ELK stack (Elasticsearch, Logstash, Kibana) using Docker Compose. This guide will help you set up and run all the services locally.

## Requirements

- Git
- Docker
- Docker Compose

## Steps to Run

### Cloning the Repository

First, clone the repository to your local machine:

```sh
git clone <URL_TO_YOUR_REPOSITORY>
cd <REPOSITORY_NAME>
```

## Running the Services with Docker Compose

In the repository directory, run all services using Docker Compose:
```sh
docker-compose up -d
```

## Verifying the Running Services

Verify that all services are running correctly:

- **Prometheus**: Open a browser and go to `http://localhost:9090`
- **Grafana**: Open a browser and go to `http://localhost:3000`
  - Log in with the username `admin` and password `grafana`
- **Elasticsearch**: Open a browser and go to `http://localhost:9200`
- **Kibana**: Open a browser and go to `http://localhost:5601`

## Test Data

To upload test data to Logstash, create a file `test-log.json` with the following content:

```json
{"message": "Test log entry 1", "@timestamp": "2024-06-16T18:00:00Z"}
{"message": "Test log entry 2", "@timestamp": "2024-06-16T19:00:00Z"}
{"message": "Test log entry 3", "@timestamp": "2024-06-16T20:00:00Z"}
```

Send the test data to Logstash using the following command:

```sh
cat test-log.json | nc localhost 5000
```

## Creating a Visualization and Dashboard

1. Go to the **Dashboard** section and click on **Create dashboard**.
2. Click on **Create new visualization** and select the **TSVB (Time Series Visual Builder)** visualization type.
3. Select the `logstash-*` index pattern.
4. On the X-axis, select **Date Histogram** and choose `@timestamp` as the field.
5. On the Y-axis, add metrics such as **Count** to show the number of logs.
6. Save the visualization and add it to the dashboard.
7. Save the dashboard and take a screenshot.

## Verifying Data in Elasticsearch and Kibana

### Verifying Data in Elasticsearch

1. Open a browser and go to `http://localhost:9200/logstash-*/_search?q=*&pretty`.
2. Ensure you see the ingested records.

### Viewing Data in Kibana

1. Go to the **Discover** section.
2. Select the created `logstash-*` index pattern.
3. Ensure you see the ingested records.

## Author

Milan "Necraatall" Zlamal

## License

"THE BEER-WARE LICENSE" (Revision 42):
Milan "Necraatall" Zlamal wrote this code. As long as you retain this notice, you can do whatever you want with this stuff. If we meet some day, and you think this stuff is worth it, you can buy me a beer in return.
