# Ex.05 Design a Website for Server Side Processing
## Date:2 / 09 2025

## AIM:
 To design a website to calculate the Body Mass Index(BMI) in the server side. 


## FORMULA:
BMI=weight/(height*height)
BMI => Body Mass Index
## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
templates.html
<!DOCTYPE html>
<html>
<head>
    <title>BMI Calculator</title>
</head>
<body>
    <form method="POST">
  {% csrf_token %}
  <label>Height (cm):</label>
  <input type="text" name="height"><br>
  <label>Weight (kg):</label>

  <input type="text" name="weight"><br>

  <button type="submit">Calculate</button>
</form>

{% if BMI %}
  <h3>Your BMI is: {{ BMI }}</h3>
{% endif %}
</body>
</html>

views.py
from django.shortcuts import render

def calculate_bmi(request):
    bmi = None

    if request.method == "POST":
        try:
            height_cm = float(request.POST.get("height"))
            weight_kg = float(request.POST.get("weight"))
            height_m = height_cm / 100  # convert cm to meters
            
            bmi = weight_kg / (height_m * height_m)

            print(f"Calculated BMI: {bmi:.2f}")  # Output to console

        except (TypeError, ValueError, ZeroDivisionError):
            bmi = None

    return render(request, "bmiapp/template.html", {"BMI": bmi})

urls.py
from django.contrib import admin
from django.urls import path
from bmiapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.calculate_bmi, name='calculate_bmi'),
]

```



##  BMI SERVER SIDE PROCESSING: 


## HOMEPAGE:
<img width="322" height="247" alt="image" src="https://github.com/user-attachments/assets/131a6305-9f96-4b0f-9676-01a5e3487756" />


## RESULT:
The program for performing server side processing is completed successfully.
![alt text](<Screenshot 2025-09-24 160251.png>)
