# Ex.05 Design a Website for Server Side Processing
## Date:05/11/25

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

```
math.html

<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>POWER OF LAMP IN INCANDESCENT BULB</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <style type="text/css">
        body {
            background-color: #ffffff;
            color: #000000;
            font-family: Arial, sans-serif;
        }
        .box {
            display: block;
            width: 500px;
            min-height: 300px;
            font-size: 20px;
            background: #ffffff;
            border: 2px solid #000000;
            border-radius: 10px;
            box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
            padding: 20px;
        }
        h1 {
            color: #000000;
            text-decoration: underline;
        }
        input[type="text"] {
            border: 1px solid #000000;
            border-radius: 5px;
            padding: 5px;
            background-color: #f5f5f5;
            color: #000000;
            font-size: 16px;
        }
        input[type="submit"] {
            background-color: #000000;
            color: #ffffff;
            border: none;
            border-radius: 5px;
            padding: 8px 15px;
            cursor: pointer;
            font-size: 16px;
        }
        input[type="submit"]:hover {
            background-color: #333333;
        }
        div {
            margin-bottom: 15px;
        }
    </style>
</head>

<body>
    <center>
        <div>
            <div class="box">
                <h1>POWER OF LAMP IN INCANDESCENT BULB</h1>
                <form method="POST">
                    {% csrf_token %}
                    <div>
                        INTENSITY : 
                        <input type="text" name="Intensity" value="{{I}}">(in A)<br />
                    </div>
                    <div>
                        RESISTANCE : 
                        <input type="text" name="Resistence" value="{{R}}">(in Ω)<br />
                    </div>
                    <div>
                        <input type="submit" value="Calculate"><br />
                    </div>
                    <div>
                        POWER : 
                        <input type="text" name="Power" value="{{Power}}">W<br />
                    </div>
                </form>
            </div>
        </div>
    </center>
</body>
</html>

views.py 

from django.shortcuts import render

def powerlamp(request):
    context={}
    context['Power'] = ""
    context['I'] = ""
    context['R'] = ""
    if request.method == 'POST':
        print("POST method is used")
        I = request.POST.get('Intensity','')
        R = request.POST.get('Resistence','')
        print('request=',request)
        print('Intensity=',I)
        print('Resistence=',R)
        Power = int(I) * int(I) * int(R)
        context['Power'] = Power
        context['I'] = I
        context['R'] = R
        print('Power=',Power)
    return render(request,'mathapp/math.html',context)

    urls.py

    from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.powerlamp,name="powerlamp"),]
```

## SERVER SIDE PROCESSING:
 ![alt text](<Screenshot (78).png>)


## HOMEPAGE:
 ![alt text](<Screenshot (77).png>)
 
## RESULT:
The program for performing server side processing is completed successfully.
