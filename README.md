# EX01 Developing a Simple Webserver

# Date:21/9/2024
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:
views.py
from django.shortcuts import render,HttpResponse
from http.server import HTTPServer,BaseHTTPRequestHandler

def lapspec(request):
    return HttpResponse("Hello, Django!")

content = '''
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laptop Specification Sheet</title>
    <style>
        /* General Styling */
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #f7f7f7, #eaeaea);
            color: #333;
        }

        /* Header Section */
        header {
            background-color: #4CAF50;
            color: white;
            padding: 20px 10px;
            text-align: center;
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2);
        }
        header h1 {
            margin: 0;
            font-size: 2rem;
        }

        /* Table Styling */
        table {
            width: 80%;
            margin: 30px auto;
            border-collapse: collapse;
            background: #fff;
            box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
            overflow: hidden;
        }
        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        th {
            background-color: #4CAF50;
            color: white;
            text-transform: uppercase;
            font-size: 14px;
        }
        tr:nth-child(even) {
            background-color: #f9f9f9;
        }
        tr:hover {
            background-color: #f1f1f1;
        }
        td {
            font-size: 16px;
            color: #555;
        }

        /* Footer Styling */
        footer {
            margin-top: 20px;
            background: #4CAF50;
            color: white;
            text-align: center;
            padding: 10px 0;
            font-size: 14px;
            box-shadow: 0px -2px 6px rgba(0, 0, 0, 0.1);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            table {
                width: 95%;
            }
            header h1 {
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>

    <header>
        <h1>Laptop Specification Sheet</h1>
    </header>

    <table>
        <tr>
            <th>Component</th>
            <th>Details</th>
        </tr>
        <tr>
            <td>Brand</td>
            <td>Asus ROG</td>
        </tr>
        <tr>
            <td>Model</td>
            <td>UltraBook Pro 15</td>
        </tr>
        <tr>
            <td>Processor</td>
            <td>Intel Core i7-12700H (12th Gen)</td>
        </tr>
        <tr>
            <td>Graphics</td>
            <td>NVIDIA GeForce RTX 3060</td>
        </tr>
        <tr>
            <td>Memory (RAM)</td>
            <td>16 GB DDR5</td>
        </tr>
        <tr>
            <td>Storage</td>
            <td>1 TB NVMe SSD</td>
        </tr>
        <tr>
            <td>Display</td>
            <td>15.6" Full HD (1920 x 1080) 144Hz</td>
        </tr>
        <tr>
            <td>Operating System</td>
            <td>Windows 11 Home</td>
        </tr>
        <tr>
            <td>Battery</td>
            <td>76 WHr, 8-cell Lithium-ion</td>
        </tr>
        <tr>
            <td>Weight</td>
            <td>1.8 kg</td>
        </tr>
        <tr>
            <td>Price</td>
            <td>$1,499.00</td>
        </tr>
    </table>

    <footer>
        &copy; 2024 Laptop Specifications. All Rights Reserved.
    </footer>

</body>
</html>


'''


class Myserver(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200)
        self.send_header("content-type","text/html")
        self.end_headers()
        self.wfile.write(content.encode())

print("This is my webserver")
server_address = ('',8000)
httpd = HTTPServer(server_address,Myserver)
httpd.serve_forever()

urls.py

from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("", include("lapspec.urls")),
    path('admin/', admin.site.urls)
]
lapspec/urls.py

from django.urls import path
from lapspec import views

urlpatterns = [
    path("", views.lapspec, name="lapspec"),
]

# OUTPUT:
![Screenshot 2024-12-19 091421](https://github.com/user-attachments/assets/bbed0c35-d1ca-4d55-a150-77e8b308516d)


# RESULT:
The program for implementing simple webserver is executed successfully.
