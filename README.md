# Ex.05 Design a Website for Server Side Processing
## Date:29-09-2025

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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
math.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Rectangle Area</title>
</head>
<body>
    <h2>Calculate Rectangle Area</h2>

    <form method="POST">
        {% csrf_token %}
        <label for="length">Length:</label>
        <input type="text" id="length" name="length" value="{{ l }}">
        <br><br>

        <label for="breadth">Breadth:</label>
        <input type="text" id="breadth" name="breadth" value="{{ b }}">
        <br><br>

        <button type="submit">Calculate</button>
    </form>

    <hr>

    <p><strong>Length:</strong> {{ l }}</p>
    <p><strong>Breadth:</strong> {{ b }}</p>
    <p><strong>Area:</strong> {{ area }}</p>

</body>
</html>

views.py

from django.shortcuts import render

def rectarea(request):
    context = {}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"

    if request.method == "POST":
        print("POST method is used")
        l = request.POST.get('length', '0')
        b = request.POST.get('breadth', '0')

        print("request:", request)
        print("length:", l)
        print("breadth:", b)

        area = int(l) * int(b)

        context['area'] = area
        context['l'] = l
        context['b'] = b

        print("Area:", area)

    return render(request, "mathapp/math.html", context)


urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/', views.rectarea, name="areaofrectangle"),
    path('',views.rectarea,name="areaofrectangleroot"),
]

~~~

## SERVER SIDE PROCESSING:
<img width="1029" height="484" alt="Screenshot 2025-09-29 155230" src="https://github.com/user-attachments/assets/765b2aac-e765-4e3a-a93b-ee0e4722af3b" />


## HOMEPAGE:
<img width="1339" height="478" alt="Screenshot 2025-09-29 154320" src="https://github.com/user-attachments/assets/13720278-c400-43fa-93fb-f1ca0695ac35" />


## RESULT:
The program for performing server side processing is completed successfully.
