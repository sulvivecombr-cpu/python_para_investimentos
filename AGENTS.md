# Base44 Dev Environment

## What this repo is
A collection of Jupyter notebooks (`.ipynb`) for a "Python para Investimentos" course. There is no web app, no server, no `package.json` — only notebooks and a CSV data file. Designed to run in Google Colab originally.

## How it runs here
A JupyterLab server (from `jupyter/scipy-notebook` image) serves the notebooks on host port 3000. The repo is bind-mounted at `/home/jovyan/work`. Token auth is disabled so the preview iframe loads directly.

## Start / verify
```
docker compose -f docker-compose.base44.yml up -d
curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/lab   # expect 200
```

## Extra Python packages installed at startup
`yfinance`, `pandas-datareader`, `plotly`, `investpy`, `pyfolio`, `bt` — installed via pip in the compose command before Jupyter starts.

## Notes
- Some notebooks call external APIs (Yahoo Finance, Alpha Vantage, Banco Central, CVM, Investing.com). Those may require API keys or network access at run time, but none are needed to boot the server.
- Language-server permission warnings in logs are non-fatal.
