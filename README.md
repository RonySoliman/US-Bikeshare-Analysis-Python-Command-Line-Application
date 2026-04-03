# 🚲 US Bikeshare Analysis — Python Command-Line Application

An interactive command-line application that lets users explore **US bikeshare trip data** across three cities — Chicago, New York City, and Washington. Users filter data by city, month, and day of the week, and the program computes and displays a rich set of descriptive statistics in real time.

---

## 📌 Project Overview

This project is built around a single Python script that loads city-specific CSV datasets, applies user-defined filters, and outputs key statistics about travel patterns, station usage, trip durations, and rider demographics. All inputs are validated interactively with clear error messages and retry prompts.

Built as part of the **Udacity Programming for Data Science with Python** Nanodegree.

---

## 📁 Project Structure

```
├── Project.ipynb                # Main notebook / script
├── chicago.csv                  # Chicago bikeshare data
├── new_york_city.csv            # New York City bikeshare data
├── washington.csv               # Washington bikeshare data (no Gender/Birth Year)
└── README.md
```

---

## ▶️ How to Run

**Requirements:** Python 3.x with `pandas`, `numpy`, and `matplotlib`

```bash
pip install pandas numpy matplotlib
jupyter notebook Project.ipynb
```

Or run as a standalone script if exported:

```bash
python bikeshare.py
```

---

## 🖥️ Usage

The program guides the user through three sequential input prompts:

**1. Choose a city:**
```
- chicago
- new york city
- washington
```

**2. Choose a month (or all):**
```
- All, January, February, March, April, May, June
```

**3. Choose a day of the week (or all):**
```
- All, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday
```

All inputs are **case-insensitive** — `CHICAGO`, `chicago`, and `cHicAgo` are all accepted. Invalid inputs trigger a descriptive error and re-prompt the user.

---

## 📊 Statistics Computed

### ⏱️ Time Statistics (`time_stats`)
- Most common **month** of travel
- Most common **day of the week**
- Most common **start hour**

### 🚉 Station Statistics (`station_stats`)
- Most commonly used **start station**
- Most commonly used **end station**
- Most frequent **start → end station combination**

### 🕐 Trip Duration Statistics (`trip_duration_stats`)
- **Total travel time** — displayed in hours, minutes, and seconds
- **Mean travel time** — displayed in hours, minutes, and seconds

### 👤 User Statistics (`user_stats`)
- Count breakdown by **user type** (Subscriber / Customer) with bar chart
- Count breakdown by **gender** *(Chicago & NYC only)*
- **Earliest**, **most recent**, and **most common birth year** *(Chicago & NYC only)*

> Washington's dataset does not include `Gender` or `Birth Year` columns — the program handles this gracefully with `try/except` blocks and informs the user.

---

## ⚙️ Key Functions

| Function | Description |
|---|---|
| `get_filters()` | Collects and validates city, month, and day inputs from the user |
| `load_data(city, month, day)` | Loads the appropriate CSV and applies the chosen filters |
| `time_stats(df)` | Computes most frequent travel times |
| `station_stats(df)` | Computes most popular stations and trip routes |
| `trip_duration_stats(df)` | Computes total and average trip duration |
| `user_stats(df)` | Computes user type, gender, and birth year stats |
| `main()` | Orchestrates the full pipeline with a restart loop |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| `pandas` | Data loading, filtering, and aggregation |
| `numpy` | Numerical operations |
| `matplotlib` | Bar chart for user type distribution |
| `time` | Execution time tracking per analysis step |

---

## 📝 Notes & Limitations

- Data is limited to **January–June** for all three cities
- Washington does not include `Gender` or `Birth Year` — stats for these fields are skipped with a user-friendly message
- The restart loop at the end of each session allows repeated queries without re-running the script
- Navigation direction for the arrow buttons is detected at page load — resizing mid-session won't affect scroll behavior

---

## 👤 Author

Built as a submission for the **Udacity Programming for Data Science with Python** Nanodegree — Python Fundamentals & Data Exploration module.
