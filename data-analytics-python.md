# Data Analytics for Beginners

## Table of Contents

- [1. Set up Python in Google Colab](#1-set-up-python-in-google-colab)
  - [1.1 Create a notebook](#11-create-a-notebook)
  - [1.2 Run your first cell](#12-run-your-first-cell)
  - [1.3 Return to your notebook](#13-return-to-your-notebook)
  - [1.4 Fix common errors](#14-fix-common-errors)
- [2. Introduction to Python](#2-introduction-to-python)
  - [2.1 Store values and do a calculation](#21-store-values-and-do-a-calculation)
  - [2.2 Work with lists and dictionaries](#22-work-with-lists-and-dictionaries)
  - [2.3 Make a decision with if](#23-make-a-decision-with-if)
  - [2.4 Put it together with pandas](#24-put-it-together-with-pandas)
- [3. Prepare and summarize data with pandas](#3-prepare-and-summarize-data-with-pandas)
  - [3.1 Create a table with pandas](#31-create-a-table-with-pandas)
  - [3.2 Check and clean the data](#32-check-and-clean-the-data)
  - [3.3 Group sessions by topic](#33-group-sessions-by-topic)
  - [3.4 Explore a table: statistics, filters, sorting, and counts](#34-explore-a-table-statistics-filters-sorting-and-counts)
  - [3.5 Combine tables with merge()](#35-combine-tables-with-merge)
  - [3.6 Work with dates](#36-work-with-dates)
  - [3.7 Save your results](#37-save-your-results)
- [4. Visualize data with pandas](#4-visualize-data-with-pandas)
  - [4.1 Bar chart: Compare workshop fill rates](#41-bar-chart-compare-workshop-fill-rates)
  - [4.2 Line chart: Compare trends over time](#42-line-chart-compare-trends-over-time)
  - [4.3 Grouped bar chart: Test a simple prediction](#43-grouped-bar-chart-test-a-simple-prediction)
  - [4.4 Stacked bar chart: Filled and empty seats](#44-stacked-bar-chart-filled-and-empty-seats)
  - [4.5 Scatter plot: Capacity and attendance](#45-scatter-plot-capacity-and-attendance)
  - [4.6 Bubble chart: Add a third number with size](#46-bubble-chart-add-a-third-number-with-size)
  - [4.7 Histogram: Distribution of session fill rates](#47-histogram-distribution-of-session-fill-rates)
  - [4.8 Box plot: Compare spread across groups](#48-box-plot-compare-spread-across-groups)
  - [4.9 Pie chart: Share of total attendance](#49-pie-chart-share-of-total-attendance)
  - [4.10 Heatmap: Compare two categories at once](#410-heatmap-compare-two-categories-at-once)
  - [4.11 Dot map: Show where observations were made](#411-dot-map-show-where-observations-were-made)
  - [4.12 Bubble map: Show size by location](#412-bubble-map-show-size-by-location)
  - [4.13 Choropleth map: Shade areas by a rate](#413-choropleth-map-shade-areas-by-a-rate)
  - [4.14 Color-coded table: Show direction and size of change](#414-color-coded-table-show-direction-and-size-of-change)
  - [4.15 Area chart: Show the combined trend](#415-area-chart-show-the-combined-trend)
  - [4.16 Slope chart: Compare two points in time](#416-slope-chart-compare-two-points-in-time)
  - [4.17 Small multiples: One panel per group](#417-small-multiples-one-panel-per-group)
  - [4.18 Annotated chart: Point out what matters](#418-annotated-chart-point-out-what-matters)
  - [4.19 Practice loading a CSV](#419-practice-loading-a-csv)
- [5. Try it yourself](#5-try-it-yourself)
  - [5.1 Fill in the missing attendance](#51-fill-in-the-missing-attendance)
  - [5.2 Challenge: Analyze an unfamiliar CSV](#52-challenge-analyze-an-unfamiliar-csv)
  - [5.3 Worked answer](#53-worked-answer)
- [6. Sample CSV data](#6-sample-csv-data)

Data analytics means asking a question, preparing data, finding the answer, and showing it clearly. In this tutorial, you’ll practice that process with Python, one of the most widely used languages for working with data. You don’t need any experience with Python, pandas, or notebooks.

You will:

- Set up Python in your browser with Google Colab
- Learn basic Python, then use the pandas library to clean, explore, combine, and summarize tables
- Choose and make charts that fit your question
- Load data from CSV files
- Write a short caption that states a result and its limitations

All the datasets are fictional and made up for practice, so you can try things freely. Run the examples in order, and rerun them if you come back later.

## 1. Set up Python in Google Colab

Google Colab runs Python on a computer hosted by Google, and you control it through your browser. A **notebook** keeps your code, notes, tables, and charts together. You can run one block of code, called a **cell**, and see its result below it.

### 1.1 Create a notebook

1. Open [Google Colab](https://colab.research.google.com/) and sign in to your Google account.
2. Choose **New notebook**, or open **File → New notebook**.
3. Click the notebook name at the top and rename it **workshop-analysis.ipynb**.

### 1.2 Run your first cell

Click the first code cell, paste the following code, and press **Shift+Enter** or click the play button next to the cell. Colab may take a moment to connect.

```python
import pandas as pd
import matplotlib.pyplot as plt

print("Setup complete!")
```

Look for **Setup complete!** below the cell. Click **+ Code** to add a cell for each new Python block and run the examples in order. When an example asks for a CSV, follow [Section 6](#6-sample-csv-data) to create it in Colab.

### 1.3 Return to your notebook

Open the notebook again from Google Drive. Colab saves the notebook there, but a new session starts with fresh memory and temporary files. Rerun the cells that create any sample CSVs you need, then rerun the analysis cells in order.

[Google Colab FAQ](https://research.google.com/colaboratory/faq.html)

### 1.4 Fix common errors

When Python can't run a cell, it prints an error below the cell. Read the last line first, because it names the problem. Colab runs cells in the order you run them, not the order they appear on the page, so many errors come from a skipped cell.

| If you see | It usually means | Try this |
|---|---|---|
| `NameError: name 'pd' is not defined` (or `summary`, `reported`, `daily_use`, and so on) | The cell that creates that name has not run in this session. | Run the earlier cells first, in order. After a reset, rerun the import cell and the cells that create your data. |
| `FileNotFoundError: ... 'workshops.csv'` (or another CSV) | The file does not exist in this session, or the name is misspelled. | Rerun the `%%writefile` cell from [Section 6](#6-sample-csv-data). Look for `Writing workshops.csv` below it, and check the filename. |
| `ModuleNotFoundError` or `ImportError` naming `plotly` or `jinja2` | A library is not installed. | Run `%pip install plotly` or `%pip install jinja2` in a cell, then rerun the example. |
| `SyntaxError` or `IndentationError` | A quote, bracket, parenthesis, or indent was lost while copying. | Delete the cell's contents and paste the whole block again. |
| `KeyError: 'topic'` (or another column name) | The column name is misspelled, or the table was changed by an earlier cell. | Run `print(workshops.columns)` to see the exact names, including capital letters. |
| Your numbers differ from the tutorial | Cells ran out of order, or you applied the fix in [Section 5](#5-try-it-yourself). | Rerun the cells from the top in order. To rerun everything, choose **Runtime → Restart session and run all**. Keep the cells that create CSV files above the cells that read them. |

## 2. Introduction to Python

Run each example in a separate Colab code cell. These exercises use workshop attendance to practice topics from the [W3Schools Python tutorial](https://www.w3schools.com/python/).

### 2.1 Store values and do a calculation

```python
# Count the seats and attendees for one workshop.
topic = "Brain Basics"
seats = 25
attended = 20
fill_rate = attended / seats * 100

print(topic, fill_rate)
```

A line starting with `#` is a comment for the reader. The code prints `Brain Basics 80.0`. The name `fill_rate` stores the result so you can use it again.

### 2.2 Work with lists and dictionaries

```python
topics = ["Brain Basics", "Memory Games"]
workshop = {"topic": topics[0], "seats": 25, "attended": 20}

print(workshop["topic"])
print(workshop["seats"])
```

List positions start at zero, so `topics[0]` gives the first topic. A dictionary lets you look up a value by its key, such as `"seats"`. The next example uses a dictionary of lists to build a table.

### 2.3 Make a decision with `if`

```python
if fill_rate >= 80:
    print("At least 80% full")
else:
    print("Below 80% full")
```

`>=` means “greater than or equal to.” Python uses indentation to tell which lines belong to each branch. Try changing `attended` to `15` in the first cell, then rerun that cell and this one.

### 2.4 Put it together with pandas

Run this short example in a new Colab code cell. It uses the same building blocks you’ll see in the tutorial.

```python
import pandas as pd

practice = pd.DataFrame({
    "topic": ["Brain Basics", "Memory Games"],
    "seats": [25, 15],
    "attended": [20, 12]
})

practice["fill_rate_pct"] = practice["attended"] / practice["seats"] * 100
print(practice.head())
print(practice[["topic", "fill_rate_pct"]])
```

| What you see | How to read it |
|---|---|
| `import pandas as pd` | Load the pandas library and give it the short name `pd`. |
| `practice = ...` | Store the result under the name `practice` so you can use it later. |
| `"Brain Basics"` and `25` | Quotes mark text. Numbers used for calculations are written without quotes. |
| `[25, 15]` and `{"seats": [25, 15]}` | Square brackets can make a **list** of values. Curly braces make a **dictionary** that pairs a name with a value. Here, each name becomes a column in the pandas table. |
| `practice["attended"]` | Select one column by name. To select several columns, put a list of names inside the brackets, as in the last line. |
| `/` and `*` | Divide and multiply. pandas applies the calculation to each row, and the assignment stores the results in a new column. |
| `print(...)` and `practice.head()` | Parentheses call a function or method. `print()` displays a result. The dot in `practice.head()` calls an action on the table that shows its first few rows. |

The first output shows the whole table, and the second shows only the topic and fill rate columns. Both rows should show a fill rate of **80.0%**. Try changing the first attendance value from `20` to `15` and rerunning the cell. The first rate should become **60.0%**.

Python names are case-sensitive, so `practice` and `Practice` are different names. Keep the quotes, brackets, and indentation when you copy a code block. In Colab, run the cell that creates a name before running a later cell that uses it.

## 3. Prepare and summarize data with pandas

### 3.1 Create a table with pandas

**pandas** is a Python library for working with tables. A table in pandas is called a **DataFrame**. Each row below represents one workshop session.

```python
import pandas as pd

workshops = pd.DataFrame({
    "topic": ["Brain Basics", "Optical Illusions", "Brain Basics",
              "Optical Illusions", "Memory Games", "Memory Games"],
    "seats": [25, 20, 25, 20, 15, 15],
    "attended": [18, 16, 20, 19, 12, None]
})

print(workshops)
```

Each name in quotes, such as `"seats"`, becomes a column. `None` means the attendance for the last session is unknown. pandas displays that missing number as `NaN`. Because `NaN` is stored as a decimal number, pandas shows the whole `attended` column with decimals, such as `18.0`. These are still counts of people.

### 3.2 Check and clean the data

Before calculating anything, count the missing values in each column.

```python
print(workshops.isna().sum())
```

You should see **1** missing value in `attended`. For this analysis, leave that session out of the attendance calculations. Entering zero would treat it as a session that nobody attended.

```python
reported = workshops.dropna(subset=["attended"]).copy()

print("Total sessions:", len(workshops))
print("Sessions with reported attendance:", len(reported))
```

The output should be **6 total sessions** and **5 with reported attendance**. `dropna()` removes rows with missing values in the column you specify. `.copy()` gives you a separate table to work with.

### 3.3 Group sessions by topic

Use `groupby()` to put sessions with the same topic together. Then add up the seats and attendance for each topic.

```python
summary = reported.groupby("topic")[["seats", "attended"]].sum()

summary["fill_rate_pct"] = (
    summary["attended"] / summary["seats"] * 100
)

print(summary.round(1))
```

| Topic | Seats in reported sessions | Total attendance | Seats filled |
|---|---:|---:|---:|
| Brain Basics | 50 | 38 | 76.0% |
| Memory Games | 15 | 12 | 80.0% |
| Optical Illusions | 40 | 35 | 87.5% |

Your printed output uses the column names `seats`, `attended`, and `fill_rate_pct`, and it shows attendance as `38.0` and `12.0` because that column holds decimals (see Section 3.1). The table above uses plainer labels and whole numbers for the same values.

**Brain Basics had the highest total attendance** at 38. **Optical Illusions filled the largest share of its seats** at 87.5%. Memory Games has only one session with reported attendance, so its numbers reflect that one session.

### 3.4 Explore a table: statistics, filters, sorting, and counts

Before you chart anything, look at the data in a few simple ways. These examples use `reported` from Section 3.2.

```python
print(reported["attended"].mean())
print(reported["attended"].median())
print(reported.describe())
```

The **mean** adds the values and divides by how many there are. Here it is `17.0`. The **median** is the middle value when the numbers are sorted. Here it is `18.0`. `describe()` summarizes every number column at once. It shows the count, mean, standard deviation (`std`, a measure of spread), minimum, quartiles (`25%`, `50%`, `75%`), and maximum. The `50%` row is the median.

To keep only some rows, put a comparison inside square brackets. pandas checks each row, then keeps the rows where the answer is `True`.

```python
large_rooms = reported[reported["seats"] >= 20]
print(large_rooms)

busy_large = reported[(reported["seats"] >= 20) & (reported["attended"] >= 19)]
print(busy_large)
```

The first table keeps the four sessions with 20 or more seats. The second keeps two sessions that meet both conditions. Use `&` for “and” and `|` for “or”, and put parentheses around each comparison.

Sorting and counting are two more ways to see the data.

```python
print(reported.sort_values("attended", ascending=False))
print(reported["topic"].value_counts())
```

`sort_values()` orders the rows. `ascending=False` puts the largest attendance first. `value_counts()` counts how many rows have each value. Brain Basics and Optical Illusions each appear twice, and Memory Games appears once because one of its sessions was left out in Section 3.2.

### 3.5 Combine tables with `merge()`

Often the information you need is split across two tables. `merge()` matches rows from both tables using a column they share. This example adds the room for each topic.

```python
rooms = pd.DataFrame({
    "topic": ["Brain Basics", "Optical Illusions", "Memory Games"],
    "room": ["Lab A", "Lab B", "Lab B"]
})

merged = reported.merge(rooms, on="topic")
print(merged)
print("Rows before:", len(reported), "Rows after:", len(merged))

by_room = merged.groupby("room")[["seats", "attended"]].sum()
by_room["fill_rate_pct"] = by_room["attended"] / by_room["seats"] * 100
print(by_room.round(1))
```

Both row counts should be **5**. Lab A filled 76.0% of its seats and Lab B filled 85.5%.

By default, `merge()` keeps only the rows that have a match in both tables. If a topic were missing from `rooms`, its sessions would disappear without an error, so always compare the row counts before and after. Add `how="left"` to keep every row from the first table. Unmatched rows then show `NaN` in the new column. The shared column must match exactly, including spelling and capital letters.

### 3.6 Work with dates

[Save the sample as `school-energy.csv`](#6-sample-csv-data) before running this example. In that file, each month is text such as `2026-02`. Text in this year-month order sorts correctly, but it can’t be used for date calculations. `pd.to_datetime()` converts it to real dates.

```python
energy_dates = pd.read_csv("school-energy.csv")
print(energy_dates["month"].dtype)

energy_dates["month"] = pd.to_datetime(energy_dates["month"])
print(energy_dates["month"].dtype)

energy_dates["month_name"] = energy_dates["month"].dt.month_name()
spring = energy_dates[energy_dates["month"] >= "2026-04-01"]
print(spring[["month", "month_name", "school", "school_days"]])
```

The first line shows that `month` is text (pandas calls it `object` or `str`). The second shows `datetime64`, which means pandas now treats it as a date. A value such as `2026-02` becomes February 1, 2026. With real dates you can compare against a date, such as keeping April and later, and pull out parts of a date with `.dt`, such as the month name. The `spring` table has six rows: April, May, and June for each school.

### 3.7 Save your results

After cleaning and summarizing, you may want to keep the result. `to_csv()` writes a table to a file.

```python
summary.round(1).to_csv("workshop-summary.csv")

saved = pd.read_csv("workshop-summary.csv")
print(saved)
```

The topic names are the row labels of `summary`, so `to_csv()` writes them as the first column. Add `index=False` when the row labels are only `0, 1, 2` and you don’t want them in the file. Reading the file back, as the last two lines do, is a quick check that it saved correctly. To download the file, open Colab’s **Files** sidebar, refresh the list, find `workshop-summary.csv`, and choose **Download** from its menu. Colab deletes files when a session ends, so download anything you want to keep.

## 4. Visualize data with pandas

Run each Python code block in a new Colab code cell. Keep using the same notebook. The workshop examples use `reported` and `summary` from Sections 3.2 and 3.3. For the school energy examples, run both Python cells in the line chart example first to create `daily_use`. The dot map and the other country examples load separate CSVs. The bubble chart, box plot, bubble map, and choropleth map load `country-recycling.csv`. The heatmap, slope chart, small multiples, and annotated chart use `daily_use`.

| When your question is about… | Use |
| --- | --- |
| How a value compares across categories | Bar chart |
| How values change over time | Line chart |
| How several values compare within each group | Grouped bar chart |
| How a total breaks into parts across groups | Stacked bar chart |
| How two numbers vary together | Scatter plot |
| How three numbers vary together | Bubble chart |
| How common different ranges of values are | Histogram |
| How spread out values are within each group | Box plot |
| How each category contributes to one total | Pie chart |
| How a value differs across two categories | Heatmap |
| Where observations were recorded | Dot map |
| Where counts are larger or smaller | Bubble map |
| How a rate differs across areas | Choropleth map |
| Which values rose, fell, or stayed the same | Color-coded table |
| How a combined total changes over time | Area chart |
| How items change between two points in time | Slope chart |
| Whether a pattern repeats in each group | Small multiples |
| What the reader should notice | Annotated chart |

### 4.1 Bar chart: Compare workshop fill rates

Use **Matplotlib** to plot the fill rate. Sorting the values puts the highest rate at the top.

```python
import matplotlib.pyplot as plt

rates = summary["fill_rate_pct"].sort_values()

rates.plot(kind="barh", color="steelblue")
plt.xlabel("Seats filled (%)")
plt.ylabel("")
plt.title("Workshop fill rate by topic")
plt.xlim(0, 100)
plt.tight_layout()
plt.show()
```

You should see three horizontal bars, with Optical Illusions the longest (87.5) and Brain Basics the shortest (76.0). The horizontal axis goes from 0 to 100 because the values are percentages.

### 4.2 Line chart: Compare trends over time

**Question.** How did daily electricity use change at each school from February to June?

[Save the sample as `school-energy.csv`](#6-sample-csv-data) before running this example.

Each row represents one school in one month. The numbers are AI-generated for practice and describe fictional schools.

```python
import pandas as pd
import matplotlib.pyplot as plt

energy = pd.read_csv("school-energy.csv", dtype={"month": str})

print(energy.isna().sum())
print("Duplicate school-month rows:", energy.duplicated(["school", "month"]).sum())

energy["kwh_per_day"] = energy["electricity_kwh"] / energy["school_days"]
```

Check that missing counts and duplicates are all zero. For a new dataset, inspect missing readings, repeated school-month records, and zero or negative school-day counts before calculating daily use. Dividing by school days helps compare months of different lengths. These practice totals represent electricity used during school days.

**Sample data** after dividing monthly electricity use by school days, in kWh per school day

```csv
Month,School A,School B
2026-02,500,600
2026-03,480,580
2026-04,460,570
2026-05,450,560
2026-06,440,560
```

```python
daily_use = energy.pivot(index="month", columns="school", values="kwh_per_day")
daily_use = daily_use.sort_index()

ax = daily_use.plot.line(marker="o", title="School-day electricity use by month")
ax.set_xlabel("Month")
ax.set_ylabel("Electricity use (kWh per school day)")
plt.tight_layout()
ax.figure.savefig("school-energy-trends.png", dpi=300, bbox_inches="tight")
plt.show()
```

`pivot()` puts months on rows and schools in separate columns so pandas draws one line per school. You should see two lines sloping downward, with a dot for each month and School B above School A. School A dropped from 500 to 440 kWh per school day from February to June, a 12% decline. The chart shows when use fell. It takes more information, such as weather, occupancy, or equipment changes, to explain why. To save the PNG to your computer, open Colab’s **Files** sidebar, find `school-energy-trends.png`, and choose **Download** from its menu.

### 4.3 Grouped bar chart: Test a simple prediction

Run the [line chart example](#42-line-chart-compare-trends-over-time) first to create `daily_use`.

**Question.** Which prediction came closest to June’s electricity use?

Pretend you only have data through May. Predict June's daily use by averaging March, April, and May. Then compare the prediction with June's observed value. Also try a baseline that simply repeats May.

**Sample data** the chart compares, in kWh per school day, rounded to one decimal place

```csv
School,Three-month prediction,May-only prediction,Observed June
School A,463.3,450.0,440.0
School B,570.0,560.0,560.0
```

```python
recent_average = daily_use.loc["2026-03":"2026-05"].mean()
may_value = daily_use.loc["2026-05"]
june_actual = daily_use.loc["2026-06"]

comparison = pd.DataFrame({
    "Three-month prediction": recent_average,
    "May-only prediction": may_value,
    "Observed June": june_actual
})

errors = comparison[["Three-month prediction", "May-only prediction"]].sub(
    june_actual, axis="index"
).abs()
print(errors.round(1))

ax = comparison.plot.bar(title="Predicted vs. observed June electricity use")
ax.set_xlabel("School")
ax.set_ylabel("Electricity use (kWh per school day)")
ax.set_ylim(0, 750)
ax.legend(loc="upper left")
ax.tick_params(axis="x", rotation=0)
plt.tight_layout()
plt.show()

ax = errors.plot.bar(title="Prediction error for June electricity use")
ax.set_xlabel("School")
ax.set_ylabel("Absolute error (kWh per school day)")
ax.tick_params(axis="x", rotation=0)
plt.tight_layout()
plt.show()
```

You should see two charts. The first shows three bars for each school. The bars are close in height because the axis starts at zero and the gaps are small next to values near 500. The second chart plots only the gaps, so it answers the question more directly: the shorter the bar, the closer the prediction. School B has no May-only bar because that error is zero.

Absolute error is the size of the gap between prediction and observation. For School A, the three-month prediction missed by 23.3 kWh per day and the May-only prediction missed by 10.0. For School B, the three-month prediction missed by 10.0, and May matched June exactly. This example evaluates one month. Testing more months would show whether the May-only approach tends to perform better.

### 4.4 Stacked bar chart: Filled and empty seats

**Question.** Which topic had the most unused seats across its reported sessions?

```python
seat_counts = pd.DataFrame({
    "Filled": summary["attended"],
    "Empty": summary["seats"] - summary["attended"]
})

ax = seat_counts.plot.barh(
    stacked=True, color=["steelblue", "lightgray"],
    title="Filled and empty seats by workshop topic"
)
ax.set_xlabel("Seats across reported sessions")
ax.set_ylabel("")
plt.tight_layout()
plt.show()
```

You should see three horizontal bars, each split into a blue part for filled seats and a gray part for empty seats. Each bar's full length is the total number of seats offered. Brain Basics had the most empty seats (12). The chart compares counts, so use the fill-rate chart in Section 4.1 if you want to compare percentages.

### 4.5 Scatter plot: Capacity and attendance

**Question.** Did sessions with more available seats also tend to have more attendees?

```python
ax = reported.plot.scatter(
    x="seats", y="attended", color="steelblue",
    title="Workshop capacity and attendance"
)
ax.set_xlabel("Seats available per session")
ax.set_ylabel("Attendees per session")
plt.tight_layout()
plt.show()
```

You should see five dots: one at 15 seats, two at 20 seats, and two at 25 seats. Each dot is one session. The two 20-seat sessions drew 16 and 19 attendees, while the two 25-seat sessions drew 18 and 20. With five sessions and capacity tied to topic in this dataset, it's hard to separate the effects of capacity and topic.

Correlation gives one number for how closely two columns rise and fall together. It runs from −1 to 1. Values near 1 mean the columns tend to rise together, values near −1 mean one tends to fall as the other rises, and values near 0 mean no straight-line pattern.

```python
print(reported["seats"].corr(reported["attended"]))
```

The result is about `0.85`, which is a strong positive relationship. With only five sessions, and with capacity tied to topic, treat this number as a description of these five sessions, not as a rule. **Correlation does not show cause.** More seats may not bring more attendees. Larger rooms may simply be assigned to more popular topics.

### 4.6 Bubble chart: Add a third number with size

**Question.** Do countries that produce more waste per person also recycle more, and how large is each country’s population?

[Save the sample as `country-recycling.csv`](#6-sample-csv-data) before running this example. The numbers are fictional values for real countries, and each row is one country.

**Sample data** first five of 15 rows

```csv
country,iso_alpha,region,population_millions,waste_kg_per_person,recycling_rate_pct
United States,USA,Americas,335,800,32
Canada,CAN,Americas,40,700,28
Mexico,MEX,Americas,128,360,14
Brazil,BRA,Americas,216,380,11
Argentina,ARG,Americas,46,400,9
```

```python
import pandas as pd
import matplotlib.pyplot as plt

countries = pd.read_csv("country-recycling.csv")
print(countries.shape)

ax = countries.plot.scatter(
    x="waste_kg_per_person", y="recycling_rate_pct",
    s=countries["population_millions"] * 3,
    color="steelblue", alpha=0.5, edgecolor="black",
    title="Waste, recycling, and population"
)
for _, row in countries.iterrows():
    ax.annotate(row["iso_alpha"],
                (row["waste_kg_per_person"], row["recycling_rate_pct"]),
                ha="center", va="center", fontsize=8)
ax.set_xlabel("Waste per person (kg per year)")
ax.set_ylabel("Recycling rate (%)")
plt.tight_layout()
plt.show()
```

You should see 15 labeled bubbles. Each bubble is one country. Its position shows waste per person and recycling rate, and its **area** shows population in millions, so compare areas rather than widths. The `s=` setting controls bubble area, and the loop adds each country’s three-letter code. In this fictional data the two measures move together weakly (correlation about 0.45), and there is wide variation. A pattern like this shows an association, not that producing more waste causes more recycling.

### 4.7 Histogram: Distribution of session fill rates

**Question.** Were the reported sessions usually close to full?

```python
session_fill_pct = reported["attended"] / reported["seats"] * 100

ax = session_fill_pct.plot.hist(
    bins=[0, 20, 40, 60, 80, 100],
    color="steelblue", edgecolor="white",
    title="Distribution of workshop session fill rates"
)
ax.set_xlabel("Seats filled per session (%)")
ax.set_ylabel("Number of sessions")
ax.set_xticks([0, 20, 40, 60, 80, 100])
ax.set_yticks(range(len(reported) + 1))
plt.tight_layout()
plt.show()
```

Each bar counts sessions in a percentage range. You should see a bar from 80 to 100 that reaches 4 sessions and a bar from 60 to 80 that reaches 1. A bar includes its left edge, so a session that filled exactly 80% counts in the 80–100 bar. Three of the four sessions in that bar filled exactly 80%. Four of the five reported sessions filled 80% to 100% of their seats. This chart gives each session one count. The topic fill rates in Section 3.3 divide total attendance by total seats.

### 4.8 Box plot: Compare spread across groups

**Question.** How spread out are recycling rates within each region?

[Save the sample as `country-recycling.csv`](#6-sample-csv-data) before running this example.

```python
import pandas as pd
import matplotlib.pyplot as plt

countries = pd.read_csv("country-recycling.csv")
print(countries.groupby("region")["recycling_rate_pct"].median())

ax = countries.boxplot(column="recycling_rate_pct", by="region", grid=False)
plt.suptitle("")
ax.set_title("Recycling rate by region")
ax.set_xlabel("Region")
ax.set_ylabel("Recycling rate (%)")
plt.tight_layout()
plt.show()
```

You should see three boxes. In each box, the **line** is the median, and the **box** covers the middle half of the values, from the 25th to the 75th percentile. The **whiskers** reach toward the smallest and largest typical values, and any dots beyond them are unusual values. Germany (67%) appears as a dot above Europe’s box. The medians are 14 for the Americas, 20 for Asia-Pacific, and 44 for Europe. Asia-Pacific has the widest box and whiskers, so its countries differ most. Each region has only five countries, so treat the boxes as an illustration, not a firm comparison.

### 4.9 Pie chart: Share of total attendance

**Question.** What share of all reported attendance came from each workshop topic?

**Sample data** from `summary`

```csv
Workshop topic,Reported attendance
Brain Basics,38
Memory Games,12
Optical Illusions,35
```

```python
ax = summary["attended"].plot.pie(
    autopct="%1.1f%%", ylabel="", title="Share of reported attendance by topic"
)
plt.tight_layout()
plt.show()
```

You should see a pie with three slices labeled 44.7% (Brain Basics), 14.1% (Memory Games), and 41.2% (Optical Illusions). Brain Basics accounts for 38 of the 85 reported attendances, or 44.7%. Each slice uses the same denominator, total attendance across all topics. For the percentage of seats filled within a topic, see Section 4.1.

### 4.10 Heatmap: Compare two categories at once

Run the [line chart example](#42-line-chart-compare-trends-over-time) first to create `daily_use`.

**Question.** Which school and month used the most electricity per school day?

```python
heat = daily_use.T

fig, ax = plt.subplots(figsize=(7, 2.5))
im = ax.imshow(heat, cmap="Blues", aspect="auto", vmin=300, vmax=800)
ax.set_xticks(range(len(heat.columns)), labels=heat.columns)
ax.set_yticks(range(len(heat.index)), labels=heat.index)

for i in range(heat.shape[0]):
    for j in range(heat.shape[1]):
        ax.text(j, i, f"{heat.iloc[i, j]:.0f}", ha="center", va="center")

fig.colorbar(im, label="kWh per school day")
ax.set_title("School-day electricity use by school and month")
plt.tight_layout()
plt.show()
```

`daily_use.T` flips the table so schools are rows and months are columns. You should see a grid of ten colored cells, each with its value written inside and a color bar at the right. Darker cells mean higher use. School B in February is the darkest cell at 600, and School A in June is the lightest at 440. The settings `vmin` and `vmax` choose the values at the two ends of the color scale. They are set so the colors stay light enough to read the numbers. With only two schools the grid is small. A heatmap becomes more useful as you add more rows, such as 20 schools, because you can spot patterns by color before reading any numbers.

### 4.11 Dot map: Show where observations were made

[Save the sample as `city-temperatures.csv`](#6-sample-csv-data) before running this example.

**Question.** Where were the readings collected, and which locations recorded higher temperatures?

This example uses fictional temperature readings for real cities. Run `%pip install plotly` in a Colab code cell if Plotly is missing, then run the code below. The map may need internet access to load its geographic outlines.

**Sample data** for `readings`. These are the column names in the file, so the code uses them exactly.

```csv
city,latitude,longitude,temperature_c
Seattle,47.61,-122.33,16
Mexico City,19.43,-99.13,24
London,51.51,-0.13,15
Nairobi,-1.29,36.82,22
Tokyo,35.68,139.69,26
```

```python
import pandas as pd
import plotly.express as px

readings = pd.read_csv("city-temperatures.csv")

fig = px.scatter_geo(
    readings, lat="latitude", lon="longitude",
    hover_name="city", color="temperature_c",
    labels={"temperature_c": "Temperature (°C)"},
    title="Example temperature readings by city"
)
fig.show()
```

You should see a world map with five colored dots. Each dot marks a city, and its color represents the example reading. Hover over a dot to see the city name and value. Compare only the marked locations because areas between dots have no readings in this dataset.

### 4.12 Bubble map: Show size by location

[Save the sample as `country-recycling.csv`](#6-sample-csv-data) before running this example. Like the dot map, this example uses Plotly. If you see `ModuleNotFoundError`, run `%pip install plotly` first.

**Question.** Which of the countries in the dataset have the largest populations?

```python
import pandas as pd
import plotly.express as px

countries = pd.read_csv("country-recycling.csv")

fig = px.scatter_geo(
    countries, locations="iso_alpha", hover_name="country",
    size="population_millions", color="region",
    labels={"population_millions": "Population (millions)", "region": "Region"},
    title="Population by country (fictional values)"
)
fig.show()
```

The `locations` setting takes three-letter country codes, so you don’t need latitude and longitude. You should see a world map with 15 bubbles, colored by region. The bubble **area** shows population, and hovering shows the country name and value. Each bubble sits near the center of its country, so its position doesn’t show where people live inside the country. Countries without a bubble aren’t in the dataset. They don’t have zero population. A bubble map suits **counts**, such as population or number of readings. For **rates**, use the shaded map in the next section.

### 4.13 Choropleth map: Shade areas by a rate

[Save the sample as `country-recycling.csv`](#6-sample-csv-data) before running this example.

**Question.** Which countries have the highest recycling rates?

```python
import pandas as pd
import plotly.express as px

countries = pd.read_csv("country-recycling.csv")

fig = px.choropleth(
    countries, locations="iso_alpha", color="recycling_rate_pct",
    hover_name="country", color_continuous_scale="Blues",
    labels={"recycling_rate_pct": "Recycling rate (%)"},
    title="Recycling rate by country (fictional values)"
)
fig.show()
```

A **choropleth map** shades whole areas by a value. You should see a world map with 15 countries shaded from light to dark blue and the rest in plain gray. Darker blue means a higher rate, and Germany (67%) is the darkest. Hover over a country to see its name and value.

Shade **rates or percentages**, not raw totals. Totals mostly follow population or area, so a large country would look important just because it is large. Countries in gray have no data, which is not the same as zero. A single-color scale that goes from light to dark is easier to read than a rainbow. For US states, use `locationmode="USA-states"` and `scope="usa"` with two-letter state codes in the `locations` column. Counties and other regions need a boundary file, which this tutorial doesn’t cover.

### 4.14 Color-coded table: Show direction and size of change

Run the [line chart example](#42-line-chart-compare-trends-over-time) first to create `daily_use`.

**Question.** Which school had the biggest month-to-month drop in daily electricity use?

If pandas reports that Jinja2 is missing, run `%pip install jinja2` in a notebook cell.

**Sample input** from `daily_use`, in kWh per school day

```csv
Month,School A,School B
2026-02,500,600
2026-03,480,580
2026-04,460,570
2026-05,450,560
2026-06,440,560
```

```python
from IPython.display import display  # shows the styled table below the cell

change = daily_use.diff().iloc[1:]
direction = pd.DataFrame("→", index=change.index, columns=change.columns)
direction = direction.mask(change.gt(0), "↑").mask(change.lt(0), "↓")

table = change.add_suffix(" change").join(direction.add_suffix(" direction"))
table = table[["School A change", "School A direction",
               "School B change", "School B direction"]]

display(
    table.style
    .background_gradient(cmap="Blues_r", subset=["School A change", "School B change"],
                         axis=None)
    .format("{:+.0f}", subset=["School A change", "School B change"])
    .set_caption("Monthly change in electricity use (kWh per school day)")
)
```

You should see a table with four rows, March to June. Each row shows the change in each school's daily use, with a ↓, ↑, or → arrow. The shading is darkest for the biggest drops. `diff()` subtracts the previous month from the current month. The first month has no previous month to compare, so `.iloc[1:]` starts the table at March. Darker blue marks larger decreases in this dataset. The biggest drop was 20 kWh per school day. Both schools dropped by that amount in March, and School A did so again in April.

### 4.15 Area chart: Show the combined trend

Run the [line chart example](#42-line-chart-compare-trends-over-time) first to create `daily_use`.

**Question.** How did combined daily electricity use at the two schools change over time?

**Sample data** showing the inputs and the combined values the chart plots, in kWh per school day

```csv
Month,School A,School B,Combined use
2026-02,500,600,1100
2026-03,480,580,1060
2026-04,460,570,1030
2026-05,450,560,1010
2026-06,440,560,1000
```

```python
combined_use = daily_use.sum(axis=1)

ax = combined_use.plot.area(
    color="steelblue", alpha=0.55, ylim=(0, 1200),
    title="Combined school-day electricity use"
)
ax.set_xlabel("Month")
ax.set_ylabel("Electricity use (kWh per school day)")
plt.tight_layout()
plt.show()
```

You should see a shaded area that slopes gently down from 1,100 to 1,000. The vertical axis starts at 0, so the drop looks small. `sum(axis=1)` adds both schools' values for each month. The top of the shaded area shows the combined daily use, which fell from 1,100 in February to 1,000 kWh per school day in June. The shading fills the space between the line and zero.

### 4.16 Slope chart: Compare two points in time

Run the [line chart example](#42-line-chart-compare-trends-over-time) first to create `daily_use`.

**Question.** How much did each school’s daily electricity use change from February to June?

```python
start = daily_use.loc["2026-02"]
end = daily_use.loc["2026-06"]

fig, ax = plt.subplots(figsize=(5, 4))
for school in daily_use.columns:
    ax.plot(["February", "June"], [start[school], end[school]], marker="o")
    ax.text(-0.08, start[school], f"{school}: {start[school]:.0f}",
            ha="right", va="center")
    ax.text(1.08, end[school], f"{end[school]:.0f}", ha="left", va="center")

ax.set_xlim(-0.8, 1.4)
ax.set_ylabel("Electricity use (kWh per school day)")
ax.set_title("Daily electricity use, February to June")
ax.spines[["top", "right"]].set_visible(False)
plt.tight_layout()
plt.show()
```

A slope chart compares only two points, so each item becomes a single line. You should see two downward-sloping lines labeled with their values. School A fell from 500 to 440 kWh per school day (12%), and School B fell from 600 to 560 (about 6.7%). The chart makes the size of each change easy to compare, but it hides everything between the two points. The line chart in Section 4.2 shows that School B was flat from May to June.

### 4.17 Small multiples: One panel per group

Run the [line chart example](#42-line-chart-compare-trends-over-time) first to create `daily_use`.

**Question.** Does each school show its own trend more clearly when it gets its own panel?

```python
fig, axes = plt.subplots(1, 2, sharey=True, figsize=(9, 3.5))

for ax, school in zip(axes, daily_use.columns):
    daily_use[school].plot.line(ax=ax, marker="o", title=school)
    ax.set_xlabel("Month")

axes[0].set_ylabel("Electricity use (kWh per school day)")
fig.suptitle("School-day electricity use by school")
plt.tight_layout()
plt.show()
```

**Small multiples** repeat the same chart for each group. This is useful when one chart would have too many lines. You should see two side-by-side line charts, one per school. The setting `sharey=True` gives both panels the same vertical scale, so the heights compare fairly. Remove it and each panel zooms to its own data. The pattern then looks clearer, but the two schools are harder to compare.

### 4.18 Annotated chart: Point out what matters

Run the [line chart example](#42-line-chart-compare-trends-over-time) first to create `daily_use`.

**Question.** What should a reader notice first in School A’s trend?

```python
school_a = daily_use["School A"]

ax = school_a.plot.line(marker="o", title="School A: daily electricity use fell every month")
ax.set_xlabel("Month")
ax.set_ylabel("Electricity use (kWh per school day)")
ax.annotate(
    "June: 440 kWh,\n12% below February",
    xy=(4, school_a.iloc[-1]), xytext=(2.4, 490),
    arrowprops={"arrowstyle": "->"}
)
plt.tight_layout()
plt.show()
```

`annotate()` adds a note and an arrow. Its `xy` setting is the point the arrow touches, and `xytext` is where the note sits. The months are positions 0 to 4, so the June point is at `4`. You should see the School A line with a note and an arrow pointing to the June point. Annotate only the one or two things you want readers to notice, and write a title that states the finding. Make sure each claim is supported by the data. School A’s use fell every month, so the title is accurate.

### 4.19 Practice loading a CSV

Follow the [steps at the end of the tutorial](#6-sample-csv-data) to create `workshops.csv`. Then run this cell to inspect the file before choosing a question or chart.

```python
import pandas as pd

challenge = pd.read_csv("workshops.csv")
print(challenge.shape)
print(challenge.head())
print(challenge.dtypes)
print(challenge.isna().sum())
```

Check that the shape is `(6, 3)` and that only `attended` has a missing value. Write down what one row represents and what each numeric column counts. Pick one question, choose a chart that answers it, and write a caption with one number from the chart and one limitation of the data. State the unit you counted, such as sessions or seats, and mention the missing attendance when it affects your result.

When sharing your analysis, cite your data source and label simulated data clearly.

## 5. Try it yourself

### 5.1 Fill in the missing attendance

The missing Memory Games session actually had **15 attendees**. Add this line after you create the original table, then rerun the cleaning, grouping, and chart cells.

```python
workshops.loc[5, "attended"] = 15
```

`loc[5, "attended"]` selects the sixth row because the row labels start at zero. **Which topic has the highest fill rate now?**

**Check your answer:** Memory Games now leads at **90%**, with 27 attendees across 30 seats.

After this change, the tables and charts include all six sessions. Numbers in Sections 3 and 4, such as 5 reported sessions and 85 total attendances, describe the original data and will differ from your output. To return to the original data, rerun the notebook from Section 3.1 without the `loc` line, or reload `workshops.csv` as described below.

To repeat the workshop analysis using a file, [save the sample as `workshops.csv`](#6-sample-csv-data). In Section 3.1, keep `import pandas as pd` and replace the table creation and print lines with:

```python
workshops = pd.read_csv("workshops.csv")
print(workshops.head())
```

`head()` shows the first five rows. Rerun Sections 3.2–3.3 and the bar chart in Section 4.1 after loading the file to check that Optical Illusions has the highest fill rate at 87.5%. Reloading the CSV restores the missing attendance value from the original data.

### 5.2 Challenge: Analyze an unfamiliar CSV

Now try a dataset you haven’t seen before. [Save the sample as `library-visits.csv`](#6-sample-csv-data) before you start. Each row is one branch library in one week. The columns are `week_start` (the date the week begins), `branch`, `visitors` (the number of people who visited), and `event_week` (`yes` if the branch held an event that week).

**Question.** Which branch had the highest average weekly visitors, and did weeks with an event draw more visitors?

1. Load the file. Check its shape, column types, and missing values.
2. Check for duplicate rows and decide what to do about them.
3. Convert `week_start` to dates.
4. Calculate the average weekly visitors for each branch.
5. Compare event weeks with other weeks.
6. Make one chart. Write a caption with one number and one limitation.

Try it yourself before you read the worked answer. Real files often have problems, so check the data before you trust a result.

### 5.3 Worked answer

```python
import pandas as pd
import matplotlib.pyplot as plt

library = pd.read_csv("library-visits.csv")

# Step 1: inspect
print(library.shape)
print(library.dtypes)
print(library.isna().sum())

# Step 2: find and remove duplicate rows
print("Duplicate rows:", library.duplicated().sum())
library = library.drop_duplicates()

# Step 3: convert the week to a date
library["week_start"] = pd.to_datetime(library["week_start"])

# Step 4: average visitors per branch (pandas skips the missing value)
by_branch = library.groupby("branch")["visitors"].mean().sort_values(ascending=False)
print(by_branch.round(1))

# Step 5: compare event weeks with other weeks within each branch
by_event = library.groupby(["branch", "event_week"])["visitors"].mean().unstack()
print(by_event.round(1))

# Step 6: chart
ax = by_event.plot.bar(title="Average weekly visitors by branch and week type")
ax.set_xlabel("Branch")
ax.set_ylabel("Average visitors per week")
ax.legend(title="Event week")
ax.tick_params(axis="x", rotation=0)
plt.tight_layout()
plt.show()
```

**What you should find:**

- The shape is `(19, 4)`. One `visitors` value is missing (Riverside, week of 2026-01-12), and there is **1 duplicate row** (Hillcrest, week of 2026-02-02). After `drop_duplicates()` there are 18 rows.
- **Central had the highest average**, about 430.8 visitors a week, compared with 304.0 at Riverside and 234.2 at Hillcrest.
- **Every branch drew more visitors in event weeks.** Central averaged 487.5 in event weeks and 402.5 in other weeks. Riverside averaged 360.0 and 290.0. Hillcrest averaged 285.0 and 224.0.

**Why compare within each branch?** Averaging all event weeks together (405.0) against all other weeks (299.2) would be misleading. Central had two of the four event weeks, and it is also the busiest branch, so the overall gap would mix the effect of events with the difference between branches.

**Example caption:** “Central averaged about 431 visitors a week, compared with 304 at Riverside and 234 at Hillcrest. Every branch drew more visitors in event weeks, but each branch had only one or two event weeks, so the difference may be due to chance. Riverside’s average leaves out one week with no recorded count.”

**Check your thinking.** If you skipped step 2, Hillcrest’s average would be about 241.4, not 234.2, because the duplicate week would be counted twice.

## 6. Sample CSV data

All the datasets are fictional. A **CSV** is a plain text table. Commas separate the columns, and each line after the header is one row. The final line ends with a comma because its attendance value is missing.

For each file you need, click **+ Code** in Colab and paste the entire matching block below, starting with the `%%writefile` line. `%%writefile` must be the first line of the cell. Run the cell, and you should see `Writing workshops.csv` (or the matching filename) below it. Colab saves the CSV in the notebook’s current working folder. To check that a file exists, click the folder icon in Colab’s left sidebar and refresh the list, or run `!ls` in a code cell. Run these cells again after starting a new session.

**workshops.csv**

```text
%%writefile workshops.csv
topic,seats,attended
Brain Basics,25,18
Optical Illusions,20,16
Brain Basics,25,20
Optical Illusions,20,19
Memory Games,15,12
Memory Games,15,
```

Run the [CSV practice cell](#419-practice-loading-a-csv) after creating `workshops.csv`. If you see `FileNotFoundError`, rerun the cell that creates the file and check that the filename matches.

**school-energy.csv**

```text
%%writefile school-energy.csv
month,school,school_days,electricity_kwh
2026-02,School A,18,9000
2026-03,School A,22,10560
2026-04,School A,17,7820
2026-05,School A,20,9000
2026-06,School A,16,7040
2026-02,School B,18,10800
2026-03,School B,22,12760
2026-04,School B,17,9690
2026-05,School B,20,11200
2026-06,School B,16,8960
```

**city-temperatures.csv**

```text
%%writefile city-temperatures.csv
city,latitude,longitude,temperature_c
Seattle,47.61,-122.33,16
Mexico City,19.43,-99.13,24
London,51.51,-0.13,15
Nairobi,-1.29,36.82,22
Tokyo,35.68,139.69,26
```

**country-recycling.csv**

```text
%%writefile country-recycling.csv
country,iso_alpha,region,population_millions,waste_kg_per_person,recycling_rate_pct
United States,USA,Americas,335,800,32
Canada,CAN,Americas,40,700,28
Mexico,MEX,Americas,128,360,14
Brazil,BRA,Americas,216,380,11
Argentina,ARG,Americas,46,400,9
United Kingdom,GBR,Europe,67,480,44
France,FRA,Europe,68,520,42
Germany,DEU,Europe,84,600,67
Spain,ESP,Europe,48,470,33
Italy,ITA,Europe,59,500,51
Japan,JPN,Asia-Pacific,124,340,20
South Korea,KOR,Asia-Pacific,52,400,59
Australia,AUS,Asia-Pacific,26,560,38
Vietnam,VNM,Asia-Pacific,98,250,18
Indonesia,IDN,Asia-Pacific,277,290,12
```

**library-visits.csv**

```text
%%writefile library-visits.csv
week_start,branch,visitors,event_week
2026-01-05,Central,410,no
2026-01-12,Central,395,no
2026-01-19,Central,480,yes
2026-01-26,Central,400,no
2026-02-02,Central,405,no
2026-02-09,Central,495,yes
2026-01-05,Riverside,280,no
2026-01-12,Riverside,,no
2026-01-19,Riverside,285,no
2026-01-26,Riverside,360,yes
2026-02-02,Riverside,295,no
2026-02-09,Riverside,300,no
2026-01-05,Hillcrest,210,no
2026-01-12,Hillcrest,225,no
2026-01-19,Hillcrest,230,no
2026-01-26,Hillcrest,220,no
2026-02-02,Hillcrest,285,yes
2026-02-02,Hillcrest,285,yes
2026-02-09,Hillcrest,235,no
```
