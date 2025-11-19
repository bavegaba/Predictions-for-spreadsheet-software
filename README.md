# Predictions-for-spreadsheet-software
The objective of this project is to provide an example based on Excel, as it is a soft skill, highly demanded in the workplace, allowing us to get an idea and know the needs of people and the demands of different countries in various possible scenarios.

Background

Which problems does your idea solve?
My idea seeks to provide context to people, based on AI predictions regarding the lifestyles of different countries.
How common or frequent is this problem? 
This problem, although not very common, has the experience they had in the United Kingdom when they lost thousands of records for not using an alternative to Excel.
What is your personal motivation? 
To inform professionals and future professionals through data that in many cases it is convenient to have a mixed alternative or other alternatives for spreadsheets
Why is this topic important or interesting?
This topic is important because we need to keep up with the technological changes that we see every day in our era

How is it used?

This solution is useful in company-employee environments to learn more details about a company's demands and know what training is appropriate, because it is aimed at users who want to emigrate to work in other countries, since the use of Excel, according to the figures, is more necessary in English-speaking countries.

[Excel](https://www.freepik.es/foto-gratis/concepto-estrategia-estadisticas-informe-informacion-datos_17132602.htm#fromView=search&page=1&position=2&uuid=4964b0ac-3402-4ecc-9cb0-efbc3ab10e53&query=excel)
[U.K](https://www.freepik.es/foto-gratis/vista-trasera-joven-mirando-rio-tamesis_903089.htm#fromView=search&page=1&position=3&uuid=92df5ffb-9be1-4c15-bb79-ca7523fdacfe&query=United+Kingdom)
[pandemic](https://www.freepik.es/foto-gratis/persona-que-pone-mascarilla-medica-tierra_14668469.htm#fromView=search&page=1&position=0&uuid=c6d49623-45e9-421e-9458-147c6a17bbd3&query=Covid+19)


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
    
    # Calculate R-squared
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



gap = x_usage - y_demand  # Numpy array subtraction
m3, b3, r2_3 = train_model(x_usage, gap)

print("--- SCENARIO C: Talent Gap Evolution ---")

trend = "increases" if m3 > 0 else "decreases"

print(f"Slope of the gap: {m3:.4f}")
print(f"Interpretation: As Excel usage rises, the gap between supply and demand {trend}.")
print(f"Prediction: In a country with 95% usage, the gap would be {(m3 * 95 + b3):.2f} percentage points.")

Data sources and AI methods
They are part of my own research, but I didn't take them.
https://www.theguardian.com/politics/2020/oct/05/how-excel-may-have-caused-loss-of-16000-covid-tests-in-england
https://www.nytimes.com/2020/10/05/world/europe/uk-testing-johnson-hancock.html
https://www.statista.com/statistics/983321/worldwide-office-365-user-numbers-by-country/?srsltid=AfmBOoqu62cVKTo9TrOO-9OlbVDRHpikq7_7I4EYS5QzSTBlb3kYY__i
https://www.enterprisesurveys.org/en/data
https://www.microsoft.com/en-us/digitalsafety/research/global-online-safety-survey

Challenges

It's a very broad topic that could lead to other research on this subject, so my project needs to seek more sources because my research alone isn't enough, as it doesn't solve the problem: why isn't this office tool taught in my country...?

What next?

My project would grow if this information were more democratized so that people would have more opportunities regardless of the career they choose.
The driving force behind this project is encouraging research and democratizing information, as I've mentioned before.

Acknowledgments

University of Helsinki and MinnaLearn

Linear regression for scenarios when using office tools
