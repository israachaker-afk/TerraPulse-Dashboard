# 🌍 TerraPulse Dashboard

[![R](https://img.shields.io/badge/R-4.0+-blue.svg)](https://www. r-project.org/)
[![Shiny](https://img.shields.io/badge/Shiny-Interactive-brightgreen.svg)](https://shiny.rstudio.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

*TerraPulse Dashboard* is an interactive web application for visualizing and analyzing global climate data. Built with R Shiny, it provides comprehensive insights into temperature, solar radiation, wind speed, water vapor pressure, and precipitation patterns worldwide.

---

## 📊 Features

### *5 Climate Variable Categories:*

| Variable | Visualizations | Data Source |
|----------|----------------|-------------|
| 🌡️ *Temperature* | Monthly chart, Grid map (18×36), Country map | WorldClim 2. 1 |
| ☀️ *Solar Radiation* | Monthly chart, Grid map (18×36), Country map | Custom dataset |
| 💨 *Wind Speed* | Monthly chart, Grid map (18×36), Country map | WorldClim 2.1 |
| 💧 *Water Vapor Pressure* | Monthly chart, Grid map (18×36), Country map | WorldClim 2.1 |
| 🌧️ *Precipitation* | Monthly chart, Grid map (18×36), Country map | WorldClim 2.1 |

### *Key Features:*

- ✅ *Interactive Maps* - Zoom, pan, and click for detailed information
- ✅ *Multiple Base Layers* - Light, Satellite, and Street map views
- ✅ *Grid Analysis* - High-resolution 18×36 global grid (648 cells)
- ✅ *Country-Level Statistics* - Mean values for ~245 countries
- ✅ *Monthly Trends* - Time series charts showing seasonal patterns
- ✅ *Responsive Design* - Beautiful gradient UI with theme colors
- ✅ *Fast Loading* - Optimized data extraction with vectorized operations
- ✅ *Percentage Metrics* - Compare values against global maximum

---

### *Prerequisites*

- *R* version 4.0 or higher
- *RStudio* (recommended)
- *Required R Packages:*

install.packages(c(
  "shiny",
  "shinydashboard",
  "leaflet",
  "terra",
  "raster",
  "sf",
  "rnaturalearth",
  "rnaturalearthdata"
))

### *Additional Data Package:*

# For high-resolution country boundaries
install.packages("rnaturalearthhires", 
                 repos = "http://packages.ropensoftware.org",
                 type = "source")

---

## 📥 How to Pull from This Repository

### *Method 1: Using Git (Recommended)*

#### *Step 1: Clone the Repository*

Open your terminal/command prompt and run:

git clone https://github.com/yourusername/terrapulse-dashboard. git
cd terrapulse-dashboard

#### *Step 2: Open in RStudio*

# In R/RStudio:
setwd("path/to/terrapulse-dashboard")

---

### *Method 2: Download ZIP*

1. Go to the repository page: https://github.com/yourusername/terrapulse-dashboard
2. Click the green *"Code"* button
3.  Select *"Download ZIP"*
4. Extract the ZIP file to your desired location
5. Open app.R in RStudio

---

### *Method 3: Using RStudio Git Integration*

1. Open RStudio
2. Go to *File → New Project → Version Control → Git*
3. Enter repository URL: https://github.com/yourusername/terrapulse-dashboard.git
4.  Choose directory location
5. Click *"Create Project"*

---

## 📊 Data Requirements

### *Climate Data Files*

The application requires monthly climate data in *GeoTIFF format* (.tif):

#### *1. Temperature Data*
- Files: 12 monthly TIF files
- Source: [WorldClim](https://www. worldclim.org/)
- Variable: Average temperature (°C)

#### *2. Wind Speed Data*
- Files: 12 monthly TIF files
- Source: [WorldClim](https://www.worldclim. org/)
- Variable: Wind speed at 10m (m/s)

#### *3. Water Vapor Pressure Data*
- Files: 12 monthly TIF files
- Source: [WorldClim](https://www.worldclim.org/)
- Variable: Water vapor pressure (kPa)

#### *4.  Precipitation Data*
- Files: 12 monthly TIF files
- Source: [WorldClim](https://www. worldclim.org/)
- Variable: Precipitation (mm)

#### *5. Solar Radiation Data*
- Files: 12 monthly TIF files
- Variable: Solar radiation (kJ/m²/day)

---

## ⚙️ Configuration

## 🏃 Running the Application

### *Method 1: From RStudio*

1.  Open app.R in RStudio
2. Click the *"Run App"* button at the top-right
3. The dashboard will open in your browser

### *Method 2: From R Console*

library(shiny)
runApp("path/to/terrapulse-dashboard/app.R")

### *Method 3: Run on Custom Port*

runApp("app.R", port = 8080, host = "0. 0.0.0")

---

## 🎨 UI Theme

The dashboard uses a custom color scheme for each climate variable:

| Variable | Primary Color | Status |
|----------|---------------|--------|
| Temperature | 🔴 Red (#FF5252) | info |
| Solar Radiation | 🟠 Orange (#FF9800) | primary |
| Wind Speed | 🔵 Blue (#4facfe) | success |
| Water Vapor | 🟢 Teal (#43e97b) | warning |
| Precipitation | 🟣 Purple (#7C4DFF) | danger |

---

## 📈 Performance Optimizations

### *Implemented Optimizations:*

1.  *Vectorized Extraction* - Uses terra::extract() for batch processing
2. *Pre-allocated Memory* - Efficient data structure initialization
3. *Lazy Loading* - Maps render only when requested
4. *Reactive Values* - Controls when heavy computations run
5. *Optimized Grid* - 18×36 grid balances detail and speed

### *Performance Benchmarks:*

| Operation | Time (Old) | Time (Optimized) | Improvement |
|-----------|------------|------------------|-------------|
| Grid Map (648 cells) | 30-60s | 3-8s | *8-10x faster* |
| Country Map (~245) | 5-10s | 1-2s | *5x faster* |
| Monthly Chart | 2-3s | 1s | *2-3x faster* |

---

## 🔧 Troubleshooting

### *Common Issues:*

#### *1.  "Cannot change working directory" Error*

*Problem:* setwd() fails in Shiny
*Solution:* Use full file paths instead:

# Instead of:
setwd("C:/path/to/data/")
r <- rast(list.files(... ))

# Use:
r <- rast(list.files("C:/path/to/data/", pattern = "\\.tif$", full.names = TRUE))

#### *2.  "File not found" Error*

*Solution:* Check file paths and ensure data files exist:

# Test if files exist:
list.files("C:/Users/chake/Downloads/unzip tavg/", pattern = "\\.tif$")

---

## 🤝 Contributing
Contributions are welcome! Please follow these steps:

1. *Fork the repository*
2. *Create a feature branch:*
   
   git checkout -b feature/YourFeature
   
3.  *Commit your changes:*
   
   git commit -m "Add YourFeature"
   
4. *Push to the branch:*
   
   git push origin feature/YourFeature
   
5.  *Open a Pull Request*

---

## 👤 Author

*Your Name*  
- GitHub: [@israa](https://github.com/yourusername)
- Email: your.email@example.com

---

## 🙏 Acknowledgments

- *WorldClim* - For providing high-quality climate data
- *Natural Earth* - For country boundary data
- *R Shiny Team* - For the amazing Shiny framework
- *Terra/Raster/SF communities* - For geospatial tools

---

## 📚 References

- [WorldClim - Global Climate Data](https://www.worldclim.org/)
- [Natural Earth - Free Vector and Raster Map Data](https://www.naturalearthdata.com/)
- [Shiny Documentation](https://shiny.rstudio.com/)
- [Leaflet for R](https://rstudio.github.io/leaflet/)
- [Terra Package](https://rspatial.github.io/terra/)

---

## 💡 Tips for Users

### *Best Practices:*

1. *Start with Country Maps* - Faster loading for overview
2. *Use Grid Maps* - For detailed regional analysis
3. *Check Monthly Charts* - Understand seasonal patterns first
4. *Compare Variables* - Open multiple browser tabs
5.  *Screenshot Tool* - Use browser's built-in screenshot for reports

### *Keyboard Shortcuts:*

- Ctrl + F - Search within the app
- Ctrl + R - Refresh the dashboard
- F11 - Full screen mode

---


## 🌟 Star History

If you find this project useful, please consider giving it a ⭐! 

---

*Made with ❤️ using R Shiny*
