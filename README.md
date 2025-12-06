---

## Overview
A production-style crawler that reliably extracts structured weather data with retry logic, logging, and clean outputs for automation pipelines.

---

## What this is for
- Collecting consistent weather datasets for reports and scheduled jobs.
- Serving as a template for resilient scraping workflows.

---

## Key features
- Structured extraction with clear output formats.
- Retry/backoff and logging for real-world stability.
- Easy to integrate into larger data pipelines.

---

## Edge cases handled
- Handles transient network or page load issues with retries.
- Avoids silent data corruption via structured logs and validation points.
- Designed for scheduled re-runs with consistent results.

---

## Maintenance-ready by design
Config-driven design and modular extractors make it safe to update selectors or add new targets over time.

---

## Demo Video

YouTube Demo:  
https://youtu.be/PpjXFMnaGWA

---

## Features

- Scrapes:
  - Location
  - Temperature
  - Weather status  
- Works in both headless and visible mode  
- JSON-like output from CLI  
- Graceful timeout handling  
- Includes fallback selector logic for UI changes

---

## Why This Project Exists

This crawler was created as a **clean and structured portfolio project** to demonstrate:

- Maintainable Python automation practices  
- Design of resilient web scrapers  
- Separation between CLI and module usage  
- Logging, fallback logic, and safe selectors  
- Delivering a complete project with tests and documentation  

The goal is clarity and engineering quality rather than complexity.

---

## Requirements

- Python 3.9+  
- Google Chrome installed  
- Dependencies inside `requirements.txt`  
  (selenium, webdriver-manager)

---

## Installation

```bash
git clone https://github.com/nyongdev0310/korean_portal_weather_crawler.git
cd korean_portal_weather_crawler

python -m venv venv
source venv/bin/activate           # macOS / Linux
.\venv\Scripts\Activate.ps1        # Windows PowerShell
venv\Scripts\activate              # Windows cmd.exe

pip install -r requirements.txt
```

---

## CLI Usage

### Basic use
```bash
python korean_portal_weather_crawler.py --url "https://weather.naver.com/today/09140104"
```

### With visible browser
```bash
python korean_portal_weather_crawler.py --url "https://weather.naver.com/today/09140104" --no-headless
```

### Example output
```json
{
  "location": "Seoul, Jung-gu",
  "temperature": "23°",
  "status": "Sunny"
}
```

---

## Programmatic Usage

```python
from korean_portal_weather_crawler import run_crawler

data = run_crawler(
    url="https://weather.naver.com/today/09140104",
    headless=True,
    timeout=10,
    log_level="INFO",
)

print(data.to_dict())
```

---

## Test Example

```python
from korean_portal_weather_crawler import run_crawler

def test_run_crawler_basic():
    url = "https://weather.naver.com/today/09140104"
    data = run_crawler(url=url, headless=True, timeout=10)
    assert data.location is not None
```

---

## Project Structure

```bash
korean_portal_weather_crawler.py        # Main crawler module
example_run.py                          # Example script
test_korean_portal_weather_crawler.py   # Simple test
README.md
requirements.txt
```

---

## Notes

- Weather portals frequently update their HTML structure.
This project includes fallback selectors to reduce breakage.

- Update the selector configuration if the site layout changes.

- Respect website policies; avoid high-frequency automated scraping. **portfolio-oriented.**

---

## License

This project is provided for demonstration and portfolio use.
You may reference or adapt the code, but avoid high-volume automated scraping.