---
layout: post
title: Playing with the googlemaps Python SDK
---

Yesterday I chose a project idea to be my case study in the Java Software Developer training course I'm currently taking. Briefly, it's an app that will tell you whether the price the Uber is offering you for a trip is a good deal or overpriced, compared to historical trip data.

To get started with this idea, I decided to hack together a prototype in Python. For that I needed to learn the googlmaps Python SDK. Fortunately it was pretty easy to use.

I created an API key on the Google Cloud Platform console, activated it for the directions API of Google Maps, and copied it to a `.env.txt` file in my project folder.

Then I picked up some example code from the github repository for the Python googlemaps API. One of the things this code had was a call to request directions from one location to another. That's the one I wanted because I want to know the duration and distance of a trip from point A to point B so that I can estimate the price of an Uber trip.

I used the PyCharm debugger to inspect the result of this call to googlemaps, and found that it was a nested structure of lists and dictionaries. I was able to pull out, for example, the distance in kilometers with this code: `directions_result[0]['legs'][0]['distance']['value']`.

Once I had the distance in meters and the time in seconds, I proceeded to write a function to estimate the cost of a ride, based on those numbers.

I used numbers from the internet to estimate the cost per mile and minute of a trip. 

Now I have a simple script that takes two String values and prints out the price estimate in dollars. I don't think it's accurate yet; I want to go back to a past data science project which analized data from rideshare trips starting and ending in Chicago to get a clearer idea of what the numbers should be for cost per mile and cost per minute.

I think this will be an intersting project.





