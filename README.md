# Titanic Dataset - Exploratory Data Analysis (EDA)

This project is an Exploratory Data Analysis (EDA) on the Titanic passenger dataset using Python and Pandas. The goal is to clean the data, analyze demographic patterns, uncover key survival factors, and provide a production-ready interactive web application deployable on **Vercel**.

---

## 🌐 Live Web Application & Vercel Deployment
The repository includes a production-ready static web application (`index.html` & `vercel.json`) that provides:
- **Interactive KPI Dashboard & Charts:** Visualizing survival rates by sex, class, age, and family cohorts using Chart.js.
- **Deep Dives into Hidden Patterns:** Detailed breakdown of the steerage penalty, family size sweet spot, and child survival.
- **Interactive Survival Probability Estimator:** Live calculator tool allowing users to enter custom passenger attributes and get historical survival estimates.
- **Embedded Jupyter Notebook Viewer:** Instant access to the rendered `titanic_eda.html` without leaving the page.

### Deploy to Vercel in 1 Minute:
1. Go to [vercel.com](https://vercel.com) and log in with your GitHub account.
2. Click **"Add New Project"** > **"Import Git Repository"**.
3. Select `EDA-on-Titanic-` from your repository list.
4. Leave all build settings as default (Framework: **Other**, Build Command: empty, Output Directory: empty).
5. Click **"Deploy"** — Vercel will deploy it in seconds and provide a live URL (e.g. `https://eda-on-titanic-ashish.vercel.app`)!

---

## 📌 Questions to Answer
Before exploring the data, three main questions were defined:
1. **Did women have a higher survival rate than men?**
2. **Did ticket class (1st, 2nd, 3rd) matter for survival?**
3. **Was age related to survival (did children have priority)?**

**Extra patterns investigated:**
- Did the "women first" rule work equally well in 3rd class compared to 1st class?
- How did family size and traveling alone impact survival?

---

## 🛠️ Data Cleaning Steps & Justifications

1. **Age (177 missing values):**  
   Filled missing ages with the median age of passengers in the same class and gender (`pclass` and `sex`).  
   *Reason:* Age differed significantly across passenger classes, and median is resistant to extreme outliers.

2. **Deck (688 missing values):**  
   Dropped the `deck` column entirely.  
   *Reason:* Over 77% of values were missing, so keeping or filling it would introduce artificial noise.

3. **Embarked (2 missing values):**  
   Filled the 2 missing values with the most common port (`'S'` - Southampton).  
   *Reason:* Southampton represents more than 72% of all boardings, so filling with mode does not distort the data.

4. **Duplicate Rows (107 rows):**  
   Kept all duplicate rows.  
   *Reason:* In this dataset, names and ticket numbers are omitted. These rows represent real, separate passengers who paid the same fare and traveled in the same class.

---

## 📊 Key Findings & Hidden Patterns

### 1. Survival by Sex
- **Women:** **74.20%** survived (233 out of 314)
- **Men:** **18.89%** survived (109 out of 577)
- *Takeaway:* Women were nearly 4 times more likely to survive than men due to the "women and children first" protocol.

### 2. Survival by Ticket Class
- **1st Class:** **62.96%** survived
- **2nd Class:** **47.28%** survived
- **3rd Class:** **24.24%** survived
- *Takeaway:* Higher ticket class gave significantly better access to lifeboats.

### 3. Survival by Age Group
- **Children (0–12 years):** **57.97%** survived
- **Teens (12–18 years):** **42.86%** survived
- **Adults (18–40 years):** **36.05%** survived
- **Middle-aged (40–60 years):** **39.06%** survived
- **Seniors (60+ years):** **22.73%** survived
- *Takeaway:* Children had the highest survival priority, while seniors had the lowest.

### 4. Hidden Pattern 1: Class × Sex (The Steerage Penalty)
- **1st Class Women:** **96.81%** survived
- **2nd Class Women:** **92.11%** survived
- **3rd Class Women:** **50.00%** survived
- *Takeaway:* While almost all upper-class women survived, half of all women in 3rd class died. Ticket class played a massive role even for female passengers.

### 5. Hidden Pattern 2: Family Size & Traveling Alone
- **Solo Travelers (Family size = 1):** **30.35%** survived
- **Small Families (Family size = 2 to 4):** **57.88%** survived (peaked at **72.41%** for families of 4)
- **Large Families (Family size = 5+):** **14.75%** survived (0% for family size 8 and 11)
- *Takeaway:* Having 1 to 3 relatives helped passengers alert and assist each other. But large families suffered heavy losses because gathering everyone in crowded steerage was extremely difficult during the evacuation.

---

## 🎯 Direct Answers to the Questions

1. **Did women survive more than men?**  
   Women survived at about **74 percent** compared with about **19 percent** for men.

2. **Did ticket class matter?**  
   Passengers in 1st class survived at **63 percent**, 2nd class at **47 percent**, and 3rd class at only **24 percent**.

3. **Was age related to survival?**  
   Children under 12 survived at **58 percent**, whereas seniors aged 60 and above had the lowest survival rate at **23 percent**.

4. **Did ticket class affect female survival?**  
   Over **92 percent** of women in 1st and 2nd class survived, but in 3rd class, female survival dropped to **50 percent**.

5. **Did family size make a difference?**  
   Passengers in small families (2–4 members) had the highest survival rate at **58 percent**, while solo travelers had **30 percent** and large families of 5 or more dropped to **15 percent**.

---

## 📁 Files Included
- `index.html` — Interactive production dashboard & survival estimator for Vercel.
- `vercel.json` — Vercel deployment configuration.
- `titanic_eda.ipynb` — The complete Jupyter Notebook with clean code, comments, tables, and charts.
- `titanic_eda.html` — The exported HTML report of the notebook.
- `titanic.csv` — Titanic passenger dataset.
- `README.md` — Project summary, findings, and deployment guide.

---

## 💻 How to Run Locally
1. Run local web server:
   ```bash
   python -m http.server 3000
   ```
   Open `http://localhost:3000` in your browser.
2. Or run the Jupyter notebook:
   ```bash
   pip install -r requirements-dev.txt
   jupyter notebook titanic_eda.ipynb
   ```

## Author 
   Ashish Balodia 
