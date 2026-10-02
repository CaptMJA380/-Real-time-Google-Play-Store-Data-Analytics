# Play Store Choropleth Map Analysis - Google Colab Guide

## 📋 Overview
This Jupyter notebook creates an interactive Choropleth map visualization using Plotly to analyze Play Store app data by category, with specific filters and time-based display restrictions.

## ✨ Features Implemented

### 1. **Data Filtering**
- ✅ Excludes categories starting with 'A', 'C', 'G', 'S'
- ✅ Selects only the top 5 categories by total installs
- ✅ Cleans and converts the "Installs" column to numeric format

### 2. **Interactive Choropleth Map**
- ✅ Uses Plotly for interactive geographic visualization
- ✅ Maps each top 5 category to a country
- ✅ Color-coded by total installs (Viridis color scale)
- ✅ Hover information showing:
  - Category name
  - Total installs
  - Number of apps
  - Average rating
  - Whether installs exceed 1 million

### 3. **Time-Based Display Restriction**
- ✅ Displays the Choropleth map only between **6 PM - 8 PM IST**
- ✅ Outside this time window, shows data summary table instead
- ✅ Automatic IST timezone detection

### 4. **Highlighting Categories with >1M Installs**
- ✅ Categories exceeding 1 million installs are highlighted
- ✅ Clearly marked in the visualization and annotations

### 5. **Additional Analysis**
- ✅ Detailed statistics for each category
- ✅ Top apps within each category
- ✅ Summary statistics table
- ✅ CSV export functionality

## 🚀 How to Use in Google Colab

### Step 1: Upload to Google Drive
1. Download the `Play_Store_Choropleth_Analysis.ipynb` file
2. Upload it to your Google Drive
3. Right-click → Open with → Google Colaboratory

### Step 2: Prepare Your Data
1. Have your `Play_Store_Data.csv` file ready
2. When you run **Step 2** (Load Data), you'll be prompted to upload the CSV file
3. Click "Choose Files" and select your CSV

### Step 3: Run All Cells
1. Click **Runtime** → **Run all** (or press Ctrl+F9)
2. Wait for all cells to execute
3. When prompted for file upload, select your Play_Store_Data.csv

### Step 4: View Results
- **Between 6 PM - 8 PM IST**: Interactive Choropleth map will display
- **Outside 6-8 PM IST**: Data summary table and statistics will show
- Both include comprehensive analysis and insights

## 📊 Output Files Generated
The notebook automatically generates:
1. `choropleth_analysis.csv` - Summary of category data for choropleth
2. `top5_categories_detailed.csv` - Detailed data for top 5 categories

Download these from Colab by:
1. Left sidebar → Files folder icon
2. Right-click on file → Download

## 🔍 Data Processing Flow

```
Raw CSV Data
    ↓
Clean Installs Column (convert to numeric)
    ↓
Filter out categories starting with A, C, G, S
    ↓
Calculate total installs per category
    ↓
Select top 5 categories
    ↓
Check if current time is 6-8 PM IST
    ↓
Create Interactive Choropleth Map (if within time window)
    ↓
Generate Statistics & Export CSVs
```

## 📍 Category to Country Mapping (in Choropleth)
The top 5 categories are mapped to countries as follows:
- **1st Category** → United States
- **2nd Category** → India
- **3rd Category** → China
- **4th Category** → Brazil
- **5th Category** → Japan

## ⏰ Time Restriction Logic
- **Display Window**: 6:00 PM - 7:59:59 PM IST
- **IST Timezone**: Asia/Kolkata (UTC+5:30)
- **Automatic Detection**: Script automatically detects IST time
- **Fallback**: Data table shown 24/7, map only 6-8 PM

## 🔧 Customization Tips

### To Change Time Window:
Find this line in **Step 6**:
```python
is_within = 18 <= current_hour < 20  # 6 PM = 18:00, 8 PM = 20:00
```
Change 18 and 20 to your desired hours (24-hour format)

### To Add/Remove Excluded Letters:
In **Step 4**, modify:
```python
excluded_letters = ['A', 'C', 'G', 'S']
```

### To Change Top N Categories:
In **Step 4**, change:
```python
top_5_categories = category_installs.head(5).index.tolist()
```
Replace `5` with desired number

## 📝 Key Metrics Displayed

| Metric | Description |
|--------|-------------|
| Total Installs | Sum of all app installs in category |
| Num Apps | Number of apps in category |
| Avg Rating | Average user rating (0-5 scale) |
| Exceeds 1M | Whether category has >1M total installs |

## ❓ Troubleshooting

### Q: "ModuleNotFoundError: No module named 'plotly'"
**A:** The first cell installs all required packages. Make sure to run it before other cells.

### Q: "FileNotFoundError" when uploading
**A:** Wait for the file upload to complete (progress bar), then continue to next cell.

### Q: Map not displaying
**A:** Check if current time is between 6 PM - 8 PM IST. The script will show the time check result.

### Q: "No data matching the query"
**A:** Ensure your CSV file has the same column names and format as the original Play Store data.

## 📧 Support
If you encounter any issues:
1. Check internet connection (required for Plotly rendering)
2. Restart the Colab kernel: **Runtime** → **Restart runtime**
3. Re-run all cells: **Runtime** → **Run all**

## 📄 License & Notes
- This notebook processes publicly available Play Store data
- Results are for analytical purposes only
- Data visualization created with Plotly
- Time-based features use Python's datetime and pytz libraries

---

**Created for**: Interactive Choropleth Map Analysis Task
**Last Updated**: July 2026
**Python Version**: 3.8+
