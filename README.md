# How to use the weather trivia microservice
This service retrieves a random piece of weather trivia from a .txt file containing lots of prewritten weather trivia using Flask and HTTP requests. It is intended to run on a temperary URL locally.

# How to request data from a microservice
To retrieve data from the microservice it is nessessary to define a function in the main file (I used python, main.py) and make an HTTP GET request similar to the following:

```
import requests


def get_random_trivia():
    response = requests.get("http://localhost:5000/random_trivia")

    if response.status_code == 200:
        trivia = response.json().get("trivia")
        return trivia
    else:
        print("failed to get trivia")
        return None
```

Run microservice.py to start the Flask server, then run the main program and call get_random_trivia() to retrieve a single line of random trivia to use anywhere in your app

# How to recieve data from the microservice
call get_random_trivia in your main program to get back a random line of weather trivia:
```
random_trivia = get_random_trivia()
if random_trivia is not None:
    print("Random trivia: ", random_trivia)
```
In this example, the variable will contain a JSON containg a single string of weather data. For example, the above code will print 
```
Random trivia:  Lightning causes forest fires.
```
get_random_trivia() can be used anywhere in the app that needs a piece of random weather trivia

# UML Sequence Diagram
![UMLSequenceDiagram](https://github.com/RossKieser/weather_trivia_microservice/assets/83362014/b64f6102-f6ae-4563-a6fc-945a767b0ffe)

