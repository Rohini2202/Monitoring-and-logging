# Python App Monitoring with Prometheus and Grafana

This project sets up a simple Python application and uses **Prometheus** and **Grafana** to monitor its performance.

## What’s Inside?

- A basic **Flask** web app that exposes custom metrics.
- **Prometheus** to scrape and collect metrics from the app.
- **Grafana** to visualize metrics using dashboards.
- **Docker Compose** to run Prometheus and Grafana easily.

## How It Works

1. The Python app runs on `http://localhost:5000`.
2. The app exposes metrics like request duration at `http://localhost:8000/metrics`.
3. Prometheus collects these metrics every 5 seconds.
4. Grafana reads this data and shows it in real-time dashboards.

## File Structure
project/ ├── app.py # Simple Python app with Prometheus metrics 
         ├── prometheus.yml # Prometheus configuration 
         └── docker-compose.yml # Docker setup for Prometheus and Grafana

## Requirements
1. Python 3
2. Docker + Docker Compose
3. Flask and Prometheus Client (Python libs)

   
## How to Run

### 1. Start the Python App
```bash
pip install flask prometheus_client
python app.py
```
### 2. Run Prometheus and Grafana
```bash
docker-compose up
```

## Access the Services
- App: http://localhost:5000
- Metrics: http://localhost:8000/metrics
- Prometheus UI: http://localhost:9090
- Grafana Dashboard: http://localhost:3000
- Login: admin / admin (change after first login)

## Setting Up Grafana
- Go to http://localhost:3000
- Add Prometheus as a data source (http://prometheus:9090)
- Create a new dashboard using the metric:
```nginx
request_processing_seconds_sum
```
## Example Metric 
### HELP request_processing_seconds Time spent processing request
### TYPE request_processing_seconds summary
request_processing_seconds_sum{...} 0.356

## Clean Up
To stop and remove containers:
```bash
docker-compose down
```





