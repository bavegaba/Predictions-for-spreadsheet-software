<!-- This is the markdown template for the final project of the Building AI course, 
created by Reaktor Innovations and University of Helsinki. 
Copy the template, paste it to your GitHub README and edit! -->

# Predictions-for-spreadsheet-software

Final project for the Building AI course

## Summary

The objective of this project is to provide an example based on Excel, as it is a soft skill, highly demanded in the workplace, allowing us to get an idea and know the needs of people and the demands of different countries in various possible scenarios.


## Background

My idea addresses market-related problems, which is very useful for public or educational policy. This problem isn't very common, but if we analyze the data, it's crucial because, as a personal motivation, I've observed that in the UK, COVID-19 diagnoses were lost due to a lack of knowledge about Excel or switching to another alternative. Therefore, this topic is interesting because of its implications in the workplace.

* problem 1: Losing medical diagnoses
* problem 2: Supply versus demand: is it reliable?
* problem 3: Invest in Excel education


## How is it used?

The environment in which my solution operates is the educational-work environment and is aimed at audiences ranging from professionals to students, since they will be facing a competitive market with various factors.

![Excel](gente-de-negocios-trabajando-en-una-computadora-portatil-en-una-reunion.jpg)
![Pandemic](persona-que-pone-una-mascarilla-medica-en-la-tierra.jpg)
![U. K](vista-trasera-de-un-joven-mirando-el-rio-tamesis.jpg)

Code example:
```
import numpy as np

countries = [
    "Colombia", "United States", "United Kingdom", "Germany", 
    "France", "Brazil", "Mexico", "India", 
    "China", "Japan", "Australia", "Canada"
]


x_usage = np.array([87.3, 89.7, 91.2, 76.4, 82.1, 84.6, 81.3, 79.8, 88.9, 85.2, 88.1, 90.4])


y_demand = np.array([78.5, 82.1, 85.3, 65.8, 71.4, 73.2, 69.7, 68.4, 76.3, 74.1, 79.6, 83.7])


x_education = np.array([2, 3, 3, 1, 2, 2, 2, 2, 2, 2, 3, 3]) 

def train_model(x, y):
    """
    Calculates slope (m), intercept (b), and R^2 
    for any pair of arrays.
    """
    m, b = np.polyfit(x, y, 1)
    
    correlation_matrix = np.corrcoef(x, y)
    correlation = correlation_matrix[0, 1]
    r_squared = correlation ** 2
    
    return m, b, r_squared

def predict_inverse(target_y, m, b):
    """
    Solves for x in the equation: y = mx + b
    x = (y - b) / m
    Useful for finding the required input to hit a target output.
    """
    predicted_x = (target_y - b) / m
    return predicted_x



m1, b1, r2_1 = train_model(x_usage, y_demand)

print("--- SCENARIO A: Inverse Prediction (Market Targets) ---")
print(f"Model R^2: {r2_1:.4f}")


target_demand = 80.0
required_usage = predict_inverse(target_demand, m1, b1)

print(f"To achieve {target_demand}% labor demand, the country needs approx usage of: {required_usage:.2f}%")
print("")



m2, b2, r2_2 = train_model(x_education, y_demand)

print("--- SCENARIO B: Education Level vs. Demand ---")
print(f"Correlation (R^2): {r2_2:.4f} (If low, the relationship is not strictly linear)")


predicted_demand = m2 * 3 + b2
print(f"If education level is 'Very High' (3), expected demand is: {predicted_demand:.2f}%")
print("")



gap = x_usage - y_demand  
m3, b3, r2_3 = train_model(x_usage, gap)

print("--- SCENARIO C: Talent Gap Evolution ---")

trend = "increases" if m3 > 0 else "decreases"

print(f"Slope of the gap: {m3:.4f}")
print(f"Interpretation: As Excel usage rises, the gap between supply and demand {trend}.")
print(f"Prediction: In a country with 95% usage, the gap would be {(m3 * 95 + b3):.2f} percentage points.")
```


## Data sources and AI methods

[Twitter API](https://developer.twitter.com/en/docs)
[Covid-19](https://www.theguardian.com/politics/2020/oct/05/how-excel-may-have-caused-loss-of-16000-covid-tests-in-england)
[Test and trace](https://www.nytimes.com/2020/10/05/world/europe/uk-testing-johnson-hancock.html)
[Office 365 data](https://www.statista.com/statistics/983321/worldwide-office-365-user-numbers-by-country/?srsltid=AfmBOoqu62cVKTo9TrOO-9OlbVDRHpikq7_7I4EYS5QzSTBlb3kYY__i)
[Company surveys](https://www.enterprisesurveys.org/en/data)
[Global survey by Microsoft](https://www.microsoft.com/en-us/digitalsafety/research/global-online-safety-survey)


## Challenges

My project doesn't address the issue of Excel being used for more complex problems; some people use it simply as a calculator, and this data is ignored by my project. A limitation of my project is that wealthier countries likely have more computers and, therefore, higher demand. Research should also be conducted in smaller, economically disadvantaged countries to mitigate the biases arising from its use.

## What next?

My project should be more widely seen in other regions such as Latin America or Africa so that it can serve as a basis when choosing a tool, but for this to happen, more research is needed from these nations on these labor-educational challenges, in terms of data.

## Acknowledgments

* My family, friends and my university. 
