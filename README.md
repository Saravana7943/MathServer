# Ex.03 Design a Website for Server Side Processing
## Date:10.11.2026

## AIM:
To create a web page to calculate Churn Rate using server-side scripts.

## FORMULA:
Churn Rate = (CustLost / InitCust) * 100
<br> InitCust --> Initial Customers Count
<br> CustLost --> Customers Lost Count

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create a HTML file to implement form based input and output.

### Step 5:
Create python programs for views and urls to perform server side processing.

### Step 6:
Receive input values from the form using request.POST.get().

### Step 7:
Calculate the Result using the given formula.

### Step 8:
Display the calculated result in the server console.

### Step 9:
Render the result to the HTML template.

### Step 10:
Publish the website in Localhost.

## PROGRAM:
```

math.html

<html>
    <head>
        <title>webpage</title>
    </head>

    <body style="background-color: #073B3A;">

        <h1 align="center" style="color: lime">
            CHURN RATE CALCULATOR
        </h1>

        <h2 align="center" style="color: lime">
            SARAVANAKUMAR-(26011394)
        </h2>

        <form method="POST">

            {% csrf_token %}
            <br>

            <label style="color: lime">INITCUST</label>
            <input type="text" name="inital" value="{{h}}" style="color:limegreen">
            <br><br>

            <label style="color: lime">CUSTLOST</label>
            <input type="text" name="lost" value="{{a}}" style="color:limegreen">
            <br><br>

            <input type="submit" value="CALCULATE">
            <br><br>

            <label style="color: lime">CUSTRATE</label>
            <input type="text" value="{{ChurnRate}}" style="color:limegreen">
            <br>

        </form>

    </body>
</html>

views.py
from django.shortcuts import render
def churn_rate(request):
    h = float(request.POST.get('inital', '0'))
    a = float(request.POST.get('lost', '0'))
    ChurnRate = (a / h) * 100 if request.method == 'POST' else 0
    print("inital =",h)
    print("lost =",a)
    print("Churn Rate=",ChurnRate)
    return render(request, 'mathapp/math.html',{'h': h, 'a': a, 'ChurnRate': ChurnRate})

urls.py
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [path('', views.churn_rate, name='churn_rate'),]

```

## OUTPUT - SERVER SIDE:
![alt text](<Screenshot 2026-11-17 113657.png>)

## OUTPUT - WEBPAGE:
![alt text](<Screenshot 2026-11-17 113552.png>)


## RESULT:
The the web page to calculate Churn Rate using server-side scripts is created successfully.
