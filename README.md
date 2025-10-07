# BookMyShow Scraper

A Python scraper for extracting movie showtime data, seat availability, and cinema information from BookMyShow India.

## 🎬 Features

- **Movie Search**: Search for movies by name and get detailed information
- **Multi-format Support**: Extracts data for all available formats (2D, 3D, IMAX, etc.) and languages
- **Cinema Information**: Gets top 5 cinemas for each movie format
- **Seat Availability**: Real-time seat availability data for each showtime
- **JSON Export**: Exports all data to a structured JSON format

## 📋 Prerequisites

- Python 3.7+
- Chrome browser (for zendriver automation)


## 📊 Output Format

The scraper generates an `output.json` file with the following structure:

```json
[
  {
    "movie_type": "2D",
    "language": "English",
    "cinemas": [
      {
        "name": "PVR Cinemas",
        "showtimes": [
          {
            "time": "10:30 AM",
            "available_seats": 45,
            "blocked_seats": 15,
            "total_seats": 60
          }
        ]
      }
    ]
  }
]
```

### Data Fields Explanation

- **movie_type**: Format dimension (2D, 3D, IMAX, etc.)
- **language**: Movie language (English, Hindi, etc.)
- **cinemas**: List of cinema complexes
- **showtimes**: Available show timings
- **available_seats**: Currently bookable seats
- **blocked_seats**: Sold/unavailable seats
- **total_seats**: Total capacity

## 🔧 Configuration

### Browser Settings
The scraper runs in headless mode by default. To see the browser in action:
```python
browser = await zd.start(headless=False)  # Change to False
```

### Timing Adjustments
Modify delays if you experience issues:
```python
time.sleep(3)  # Increase for slower connections
```

### Cinema Limit
Change the number of cinemas to scrape:
```python
cinema_containers = soup.find_all("div", class_="sc-e8nk8f-3 hStBrg")[:5]  # Change 5 to desired number
```

