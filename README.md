# Ex.05 Design a Website for Server Side Processing
## Date:4/10/25

## AIM:
 To design a website to calculate the Body Mass Index (BMI) in the server side. 
 

## FORMULA:
BMI=W/H<sup>2</sup>
<br> BMI--> Body Mass Index
<br> W --> Weight
<br> H --> Height

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
rithvik.html

<html>
    <head>
    <title>Body Mass Index</title>
    <style>
        body{
            background-color:purple;
            font-family:Georgia,Helvetica, sans-serif;
        }
        .Calculation {
            border:3px dotted white;
            width:500px;
            margin:250px auto;
            background-color:rgba(6, 148, 30, 0.332);
            color:green;
            padding:5px 10px 10px 10px;
            font-size:20px;
        }
        .Calculation h1,h3{
            color:pink;
            text-align:center;
        }
        .Calculation h3{
            font-size:20px;
        }
        .Calculation label{
            display:block;
        }
        .input input{
            border:3px dotted white;
            margin:10px 0px 15px;
            font-size:20px;
            width:98%;        
        }
        .cal{
            text-align:center;
            padding:auto;
            margin-top:8px;
            margin-bottom:8px;
        }
        button{
            padding:10px;
            background:cyan;
        }
    </style>
    </head>
<body>
    <div class=" Calculation">
         <h1><b>BMI Calculation</b></h1>
         <h3 >AANCY AKSHARESHA A (25015773)</h3>
         <form method="post">
         {% csrf_token %}
         <div class="input">
            <label for="Weight">Weight in kg:</label>
            <input type="number" name="weight" required value="{{weight}}">
        </div>
        <div class="input">
        <label for="Height">Height in cm:</label>
        <input type="number" name="height" required value="{{height}}">
    </div>
        <div class="cal">
            <button type="submit"><b>Calculate</b></button>
        </div>
        </form>
        {% if bmi %}
        <div class="input">
             <label for="bmi">BMI: </label>
            <input type="text" required value="{{bmi}}">
        </div>
        {% endif %}
    </div>
</body>
</html>


views.py

from django.shortcuts import render
def calculate_bmi(request):
    bmi=None
    catagory=None
    height=None
    weight=None
    if request.method=="POST":
        height=float(request.POST.get("height"))
        weight=float(request.POST.get("weight"))
        bmi=weight/((height/100)**2)
        print(f"Weight: {weight}kg \nHeight: {height}cm \nBMI: {bmi}")
    return render(request, "myapp/rithvik.html",{"bmi": bmi, "height": height, "weight": weight})


urls.py

from django.contrib import admin
from django.urls import path
from myapp import views
urlpatterns=[
    path('admin/', admin.site.urls),
    path('',views.calculate_bmi,name='calculate_bmi'),
]

```

## SERVER SIDE PROCESSING :
![alt text](<Screenshot (18).png>)
![alt text](<Screenshot (22).png>)


## HOMEPAGE:
![alt text](<Screenshot (16).png>)


## RESULT:
The program for performing server side processing is completed successfully.
