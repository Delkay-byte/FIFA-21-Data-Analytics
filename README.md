# FIFA 21 Data Cleaning & Strategic Analytics ⚽📊

## Project Overview
This project involves an end-to-end data engineering and analytics pipeline using the FIFA 21 dataset (18,979 players). The primary objective was to transform a highly "dirty" dataset—characterized by inconsistent units, special characters, and structural noise—into a high-integrity analytical asset. 

Beyond cleaning, the project explores the strategic economics of football, identifying trends in player value, development windows, and organizational brand power.


## 🛠️ The Data Cleaning Pipeline
Raw data is rarely ready for a machine learning model or a business report. This project tackled several complex cleaning hurdles using **Python** and **Pandas**:

### 1. Physical Attribute Standardization
* **The Challenge:** `Height` and `Weight` were stored as objects with mixed units (e.g., `6'0"`, `175cm`, `185lbs`, `70kg`).
* **The Solution:** I engineered custom parsing functions to standardize all entries into **Centimeters (cm)** and **Kilograms (kg)**, enabling accurate physical profiling.

### 2. Financial Engineering & Currency Conversion
* **The Challenge:** `Value`, `Wage`, and `Release Clause` contained currency symbols (€) and text suffixes (M, K).
* **The Solution:** Developed a robust logic to strip symbols and multiply values by their respective magnitudes (Millions/Thousands), converting them into **numeric floats** for financial modeling.

### 3. Sanitization of Categorical & Special Data
* **Star Ratings:** Stripped the "★" symbol from `Weak_Foot`, `Skill_Moves`, and `International_Reputation` to convert them into usable integers.
* **Structural Noise:** Removed hidden newline characters (`\n`) from the `Club` column that were causing segmentation errors in data grouping.
* **Integrity Checks:** Handled the `Hits` column by parsing "K" values and filling 15,000+ null entries with `0` to prevent statistical skew.

### 4. Datetime & Feature Engineering
* **Joined Date:** Converted the `Joined` column into **Datetime** objects.
* **Tenure Metric:** Created a new feature, `Years_at_Club`, by calculating the delta between the join date and the dataset year to analyze the correlation between player loyalty and performance.


## 📈 Strategic Insights & Data Storytelling

### I. The "Elite Premium" (Wages vs. Rating)
Using regression analysis, I identified that wages follow an **exponential growth curve**. While player compensation remains relatively flat for ratings 50–80, "Elite" players (85+) command a massive market premium that sits significantly above the standard linear trend line.

### II. The Prime Investment Window (Age vs. Potential)
By visualizing the gap between a player's current `Overall_Rating` and their `Potential`, I identified the **Return on Investment (ROI) Zone**. The data shows that the optimal window for scouts to acquire talent is between **ages 16 and 23**, after which a player's current skill and potential begin to converge.

### III. The "Protection Gap" (Value vs. Release Clause)
Analysis of contract clauses reveals that clubs set release clauses significantly higher than a player's market value—often by **20% to 50%**. This acts as a strategic deterrent, forcing rival clubs to pay a "loyalty tax" to bypass standard negotiations. For superstars (€100M+), this gap becomes astronomical to "lock" the player into the club.

### IV. The "Lefty" Edge (Preferred Foot Distribution)
A boxplot analysis of ratings by preferred foot revealed that **left-footed players** have a slightly higher median overall rating than right-footed players. This suggests a higher "quality floor" for left-footed specialists in the professional ecosystem.

### V. The League of Stars (Organizational Brand Power)
By aggregating `International_Reputation`, I identified the "Heavyweights" of football. **FC Bayern München**, **PSG**, and **Real Madrid** lead the world in "Star Density." The data reveals a distinct "Prestige Gap" between Tier 1 elite brands and Tier 2 contenders, highlighting different recruitment philosophies regarding global marketability.


## 💻 Technologies Used
* **Language:** Python 3.x
* **Data Wrangling:** Pandas, NumPy
* **Visualization:** Seaborn, Matplotlib
* **Environment:** Jupyter Notebook


## 🏁 Conclusion
This project demonstrates that the most valuable insights are hidden behind the messiest columns. By moving beyond basic cleaning and into strategic feature engineering, I was able to quantify the financial and developmental patterns that govern professional football.


**Author:** Saviour Amegayie  
**Date:** February 2026  
**License:** MIT
