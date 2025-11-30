# Korean Portal Weather Crawler

A small, production-style Python example built with **Selenium** to scrape basic weather information from a Korean weather portal (example: Naver Weather).

This project is **unofficial** and not affiliated with Naver.  
It is intended for learning, demonstration, and portfolio purposes.

---

## 1. Overview

This project is intentionally simple but demonstrates several professional engineering practices:

- Structured, maintainable code layout  
- Dataclass-based result model  
- Stable scraping using `WebDriverWait`  
- Fallback selector strategy  
- Configurable logging  
- CLI + programmatic interfaces  
- Example test included  
- Demo video provided

---

## 2. Demo Video

YouTube Demo:  
https://youtu.be/PpjXFMnaGWA

---

## 3. Features

- Scrapes:
  - Location
  - Temperature
  - Weather status  
- Works in both headless and visible mode  
- JSON-like output from CLI  
- Graceful timeout handling  
- Includes fallback selector logic for UI changes

---

## 4. Why This Project Exists

This crawler was created as a **clean and structured portfolio project** to demonstrate:

- Maintainable Python automation practices  
- Design of resilient web scrapers  
- Separation between CLI and module usage  
- Logging, fallback logic, and safe selectors  
- Delivering a complete project with tests and documentation  

The goal is clarity and engineering quality rather than complexity.

---

## 5. Requirements

- Python 3.9+  
- Google Chrome installed  
- Dependencies inside `requirements.txt`  
  (selenium, webdriver-manager)

---

## 6. Installation

```bash
git clone https://github.com/sydsyd0310/korean_portal_weather_crawler.git
cd korean_portal_weather_crawler

python -m venv venv
source venv/bin/activate           # macOS / Linux
.\venv\Scripts\Activate.ps1        # Windows PowerShell
venv\Scripts\activate              # Windows cmd.exe

pip install -r requirements.txt
```

---

## 7. CLI Usage

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

## 8. Programmatic Usage

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

## 9. Test Example

```python
from korean_portal_weather_crawler import run_crawler

def test_run_crawler_basic():
    url = "https://weather.naver.com/today/09140104"
    data = run_crawler(url=url, headless=True, timeout=10)
    assert data.location is not None
```

---

## 10. Project Structure

```bash
korean_portal_weather_crawler.py        # Main crawler module
example_run.py                          # Example script
test_korean_portal_weather_crawler.py   # Simple test
README.md
requirements.txt
```

---

## 11. Notes

- Weather portals frequently update their HTML structure.
This project includes fallback selectors to reduce breakage.

- Update the selector configuration if the site layout changes.

- Respect website policies; avoid high-frequency automated scraping.

---

## 12. License

This project is provided for demonstration and portfolio use.
You may reference or adapt the code, but avoid high-volume automated scraping.