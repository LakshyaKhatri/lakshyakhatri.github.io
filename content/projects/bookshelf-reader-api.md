---
title: "Bookshelf Reader API"
date: 2020-01-24T00:02:18+05:30
slug: "bookshelf-reader-api"
description: ""
keywords: []
tags: []
draft: true
math: false
toc: false
---

A browsable REST API built using Django REST Framework for recognizing book spines in an image.

<br>
<br>

Uploaded Image        | Result
:--------------------:|:---------------------------:
<img src="https://raw.githubusercontent.com/LakshyaKhatri/Bookshelf-Reader-API/master/assets/spines.jpg" alt="Uploaded Image" width="300" />|<img src="https://raw.githubusercontent.com/LakshyaKhatri/Bookshelf-Reader-API/master/assets/drawn_spines.jpeg" alt="Resulted Image" width="300" />

# Installation
* To run this project locally, clone or download this repository.
* Install requirements using:
    ```
    pip install -r requirements.txt
    ```
* Then run the migrations using:
    ```
    python3 manage.py makemigrations  
    python3 manage.py migrate
    ```
* Run the application:
    ```
    python3 manage.py runserver
    ```

# Usage
Add these URLs after your landing URL:

<br>
<br>

Function                | url                    | Return  
:----------------------:|:----------------------:|:----------------------------------------------------:  
Upload Bookshelf Image  | `/api/create-bookshelf/` | ID for referring the uploaded image (Inside the Response Header)  
Spine Line Drawn Image  | `/api/bookshelf/\<bookshelf-id\>/` | Spine line drawn image
Cropped Spines          | `/api/spines/\<bookshelf-id\>/` | URLS of the cropped spine images

# Further Implementation

This project contains scrappers to scrap the information of all the books recognized in the spine image. Recognized spine can be sent for text recognition and then the recieved text can be uploaded to below URL's for scrapping the book's information.

> **NOTE 1:** It's okay if the recognized text is not accurate. The scrapper will automatically find the correct book.  
> **NOTE 1:** The uploaded text is expected to be the book title \[and author name\].

<br>
<br>

Function                | url                    | Return  
:----------------------:|:----------------------:|:----------------------------------------------------:  
Upload book title text for scrapping information  | `/api/add-book/` | ID of the created Book object (Inside the Response Header)
Get Book Information | `/api/book/\<book-id\>/` | Scrapped book information.

# Client Side Application
If you want to see how this REST API can be used at client side then checkout [Bookshelf Reader Android Application](https://github.com/LakshyaKhatri/Bookshelf-Reader)
