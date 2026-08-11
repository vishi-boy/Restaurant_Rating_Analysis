# 🍽️ Restaurant Ratings Analysis

A data analytics project focused on analyzing **restaurant ratings, consumer preferences, restaurant characteristics, and dining behavior in Mexico** using **Power BI, Power Query, and DAX**.

The project explores consumer demographics, restaurant pricing, parking availability, cuisine preferences, hospitality services, customer behavior, and restaurant ratings to generate meaningful business insights.

---

## 📌 Table of Contents

- [Case Study](#-case-study)
- [Dataset Description](#-dataset-description)
- [ER Diagram](#-er-diagram)
- [Data Cleaning](#-data-cleaning)
- [Data Analysis](#-data-analysis)
- [Dashboard](#-dashboard)
- [Key Insights](#-key-insights)

---

## 📖 Case Study

The dataset contains **restaurant ratings in Mexico collected from real consumers in 2012**, along with additional information about restaurants, cuisines, consumers, and consumer preferences.

The objective of this project is to analyze:

- Consumer demographics and preferences
- Restaurant characteristics
- Food, service, and overall ratings
- Dining and hospitality behavior
- Restaurant pricing and parking availability
- Cuisine preferences
- Consumer behavior across different states

---

## 📊 Dataset Description

The dataset consists of the following tables:

### 👥 Consumers

| Column | Description |
|---|---|
| **Consumer_ID** | Unique identifier for each consumer |
| **City** | City where the consumer lives |
| **State** | State where the consumer lives |
| **Country** | Country where the consumer lives |
| **Latitude** | Consumer's latitude |
| **Longitude** | Consumer's longitude |
| **Smoker** | Whether the consumer smokes |
| **Drink_Level** | Consumer's drinking level: abstemious, casual, or social |
| **Transportation_Method** | Transportation method: walking, public transport, or car |
| **Marital_Status** | Consumer's marital status |
| **Children** | Whether the consumer has dependent/independent children |
| **Age** | Consumer's age |
| **Occupation** | Consumer's occupation |
| **Budget** | Consumer's budget level: low, medium, or high |

### 🍴 Consumer Preferences

| Column | Description |
|---|---|
| **Consumer_ID** | Unique identifier for each consumer |
| **Preferred_Cuisine** | Type of cuisine preferred by the consumer |

### ⭐ Ratings

| Column | Description |
|---|---|
| **Consumer_ID** | Unique identifier for each consumer |
| **Restaurant_ID** | Unique identifier for each restaurant |
| **Overall_Rating** | Overall restaurant rating: 0 = Unsatisfactory, 1 = Satisfactory, 2 = Highly Satisfactory |
| **Food_Rating** | Food rating: 0 = Unsatisfactory, 1 = Satisfactory, 2 = Highly Satisfactory |
| **Service_Rating** | Service rating: 0 = Unsatisfactory, 1 = Satisfactory, 2 = Highly Satisfactory |

### 🏪 Restaurants

| Column | Description |
|---|---|
| **Restaurant_ID** | Unique identifier for each restaurant |
| **Name** | Restaurant name |
| **City** | Restaurant city |
| **State** | Restaurant state |
| **Country** | Restaurant country |
| **Zip_Code** | Restaurant ZIP code |
| **Latitude** | Restaurant latitude |
| **Longitude** | Restaurant longitude |
| **Alcohol_Service** | Alcohol service type |
| **Smoking_Allowed** | Whether smoking is allowed |
| **Price** | Restaurant price level: low, medium, or high |
| **Franchise** | Whether the restaurant is a franchise |
| **Area** | Whether the restaurant is in an open or closed area |
| **Parking** | Parking availability/type |

### 🍜 Restaurant Cuisines

| Column | Description |
|---|---|
| **Restaurant_ID** | Unique identifier for each restaurant |
| **Cuisine** | Type of cuisine served by the restaurant |

---

## 🔗 ER Diagram

The data model connects consumers, consumer preferences, ratings, restaurants, and restaurant cuisines to enable comprehensive analysis across multiple dimensions.

<img width="1391" height="636" alt="image" src="https://github.com/user-attachments/assets/5706239d-a4ec-48bb-acd7-365c1380fc9d" />


---

# 🧹 Data Cleaning

Data preparation and transformation were performed using **Power Query**.

### Steps to Import Data from a Folder

1. Go to **Get Data → More → All → Folder**.
2. Select the folder containing the dataset.
3. Click **Connect** and then **Transform Data**.
4. Duplicate the required files and expand the binary data.
5. Repeat the process for the required datasets.
6. Create calculated fields required for analysis.

### Calculated Fields

#### Age Group

```DAX
AgeGroup =
SWITCH(
    TRUE(),
    consumers[Age] <= 18, "Children and Adolescents",
    consumers[Age] <= 30, "Young Adults",
    consumers[Age] <= 45, "Adults",
    consumers[Age] <= 60, "Middle-aged Adults",
    "Seniors"
)
