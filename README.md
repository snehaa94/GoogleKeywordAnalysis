# 🔍 Google Keyword Trend Analysis with PyTrends

This project uses the `pytrends` library (an unofficial API for Google Trends) to analyze and visualize keyword popularity across time, regions, and multiple search terms. It helps understand search behavior trends using both static and interactive visualizations.

---

## 📌 Features Covered

- ✅ Setup and usage of **PyTrends** library
- 🔑 Define and track single or multiple **keywords**
- 🌍 Analyze **country-wise interest** and generate heatmaps
- 🗺️ Plot **global interest on world maps**
- 📈 Compare **multiple keyword trends** over time

---

## 📁 Project Structure

```
google-trend-analysis/
├── trend_analysis.ipynb
├── requirements.txt
├── screenshots/
│   ├── interest_over_time.png
│   ├── country_wise_interest.png
│   ├── global_map.png
│   └── keyword_comparison.png
└── README.md
```

---

## ⚙️ Setup Instructions

1. **Clone the repository**

```bash
git clone https://github.com/yourusername/google-trend-analysis.git
cd google-trend-analysis
```

2. **Install dependencies**

```bash
pip install -r requirements.txt
```

> or individually:
```bash
pip install pytrends pandas matplotlib seaborn plotly geopandas
```

3. **Run the notebook**

```bash
jupyter notebook trend_analysis.ipynb
```

---

## 🔧 Step-by-Step Breakdown

### 1. 📦 Setup PyTrends and Define Keywords

```python
from pytrends.request import TrendReq
pytrends = TrendReq(hl='en-US', tz=330)

kw_list = ["cloud computing", "data science", "machine learning"]
pytrends.build_payload(kw_list, cat=0, timeframe='today 12-m', geo='', gprop='')
```

---

### 2. 📥 Fetch Data

- Interest Over Time
- Interest by Region
- Related Queries
- Rising Topics

```python
data = pytrends.interest_over_time()
region_data = pytrends.interest_by_region()
```

---

### 3. 🌍 Country-Wise Interest

Shows which countries/regions have the highest search volume for each keyword.

```python
pytrends.interest_by_region(resolution='COUNTRY', inc_low_vol=True)
```

📸 _Example:_

<img width="1292" height="891" alt="Screenshot (61)" src="https://github.com/user-attachments/assets/15bcd9e1-0c60-4af3-9ebd-f1e370830da8" />

---

### 4. 🗺️ Global Map Visualization

Use Plotly or GeoPandas to plot a world map of keyword interest:

```python
import plotly.express as px

fig = px.choropleth(region_data,
                    locations=region_data.index,
                    locationmode="country names",
                    color=kw_list[0],
                    title=f"Global Interest in '{kw_list[0]}'")
fig.show()
```

📸 _World Map Example:_

<img width="1299" height="894" alt="Screenshot (62)" src="https://github.com/user-attachments/assets/6349109f-469b-4609-b4fd-7fc8e3d9f4a3" />

---

### 5. 📊 Compare Multiple Keywords

Plot all keyword trends together for comparison:

```python
data.drop(columns="isPartial", inplace=True)
data.plot(figsize=(12, 6), title="Keyword Trends Over 12 Months")
```

📸 _Comparison Chart:_

<img width="1296" height="901" alt="Screenshot (63)" src="https://github.com/user-attachments/assets/8aa3ca9f-4629-4bcd-9cfd-77e8bf2af853" />

### 5. 📊 Time wise interest

<img width="1288" height="891" alt="Screenshot (64)" src="https://github.com/user-attachments/assets/30643bb6-472c-4754-aa10-c81494303ef9" />

---

## 📈 Use Cases

- Market research
- Content strategy planning
- Keyword targeting for SEO
- Trend tracking for emerging technologies

---

## 📃 License

This project is for educational and analytical purposes.  
Feel free to modify and use it for your own trend research.

---

## 👩‍💻 Author

**Sneha Kashyap**  
GitHub: [@snehaa94](https://github.com/snehaa94)

