# Ex.05 Design a Website for Server Side Processing
## Date: 15.12.2025

## AIM:
 To design a website to calculate the Body Mass Index(BMI) in the server side. 


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
~~~
urls.py
from django.contrib import admin
from django.urls import path
from bmiapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.calculate_bmi, name='calculate_bmi'),
]

views.py
from django.shortcuts import render

def calculate_bmi(request):
    bmi = None   # Default value

    if request.method == "POST":
        height = float(request.POST.get("height"))
        weight = float(request.POST.get("weight"))
        bmi = weight / (height * height)

        # Print to server console for debugging
        print("Height:", height)
        print("Weight:", weight)
        print("BMI calculated:", bmi)

    return render(request, "bmiapp/web.html", {"BMI": bmi})

template.html
<!DOCTYPE html>
<html>
<head>
    <title>BMI Calculator</title>
</head>
<body bgcolor="blue">
    <center>
        <h2>BMI Calculator</h2>
        <form method="POST">
            {% csrf_token %}
            <label>Height (m):</label><br>
            <input type="text" name="height"><br><br>
            <label>Weight (kg):</label><br>
            <input type="text" name="weight"><br><br>
            <button type="submit">Calculate</button>
        </form>

        

        {% if BMI %}
            <h3>Your BMI is: {{ BMI }}</h3>
        {% endif %}
    </center>
</body>
</html>
~~~
## SERVER SIDE PROCESSING:

<img width="1919" height="1078" alt="Screenshot 2025-12-15 141707" src="https://github.com/user-attachments/assets/0029d1d6-9794-418c-9e7c-18327372ee50" />

## HOMEPAGE:

<img width="1911" height="1079" alt="Screenshot 2025-12-15 141652" src="https://github.com/user-attachments/assets/e6cda7de-2890-4e52-9e2c-81439c89871f" />

## RESULT:

The program for performing server side processing is completed successfully.
