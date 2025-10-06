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
power.html
<!DOCTYPE html>
<html>
<head>
    <title>Lamp Power Calculator</title>
    <style>
        body { font-family: Arial; background: #f0f0f0; text-align: center; padding: 50px; }
        form { background: #fff; padding: 20px; border-radius: 10px; display: inline-block; }
        input { margin: 5px; padding: 8px; }
        button { padding: 10px 20px; background: #4CAF50; color: white; border: none; border-radius: 5px; }
    </style>
</head>
<body>
    <h2>💡 Lamp Power Calculator</h2>
    <form method="post">
        {% csrf_token %}
        <label>Intensity (I in Amperes):</label><br>
        <input type="number" step="any" name="intensity" required><br>
        <label>Resistance (R in Ohms):</label><br>
        <input type="number" step="any" name="resistance" required><br>
        <button type="submit">Calculate Power</button>
    </form>

    {% if result %}
        <h3>Power (P) = {{ result }} Watts</h3>
    {% endif %}
</body>
</html>

view.py
from django.shortcuts import render

def power(request):
    result = None
    if request.method == 'POST':
        try:
            intensity = float(request.POST.get('intensity'))
            resistance = float(request.POST.get('resistance'))
            result = intensity ** 2 * resistance
        except:
            result = "Invalid input!"
    return render(request, 'lampapp/power.html', {'result': result})

    urls.py

    from django.urls import path
from lampapp import views

urlpatterns = [
    path('', views.power, name='power'),
]






~~~

## SERVER SIDE PROCESSING:
![screenshot1](https://github.com/user-attachments/assets/6c8254fb-26a0-4b15-9330-41622c21f063)



## HOMEPAGE:
<img width="1424" height="443" alt="Screenshot 2025-10-06 144422" src="https://github.com/user-attachments/assets/551f37c0-4e92-4011-8f88-40a011b3b5e5" />




## RESULT:
The program for performing server side processing is completed successfully.
