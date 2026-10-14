# Base44 Dev Environment

## Project Overview
Streamlit app displaying World Bank GDP data from `data/gdp_data.csv`. No external services, databases, or secrets required.

## Setup
- **Runtime**: Python 3.11 (via `python:3.11-slim` in `docker-compose.base44.yml`)
- **Dependencies**: `streamlit`, `pandas` (see `requirements.txt`)
- **Start**: `docker compose -f docker-compose.base44.yml up -d --build`
- **Preview**: Port 3000 (Streamlit runs on 3000, not its default 8501)
- **Health check**: HTTP GET on `/` returns 200 when the app is ready

## Notes
- Streamlit is launched with CORS and XSRF protection disabled so the preview proxy can embed it.
- Source is bind-mounted; edits to `streamlit_app.py` or `data/` are picked up on Streamlit's auto-rerun.
- No migrations or seeds needed — all data is in the CSV file.
