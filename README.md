Python Practice Problem - LOAD BLANCER

Assume you have a flask API, that deals different ML models, but due to GPU/CPU/RAM restrictions,
it can load only 2 ML model at once. This flask API has two following routes.
1. '/get_loaded_models' This will return the two loaded models info at that time (code is already provided below)
2. '/process_request' This will process the request, using the required model, specified in request against key 'model'.
If that model is already loaded, the API will process that request using loaded model. 
Otherwise the API will load this model at the place of the one model which is previously loaded and has less frequently requested.
You are required to write its load balancer. Your load balancer should be able to record the number of requests processed by all models,
so that it can intelligently load new model on the place of less frequent model.
Sample code with dummy processing is provided below. You have to write its load balancer function. 
You may also also re structure the code, or change in code according to your need. But those changes should not change any previous functionality.

----------------------------------------EXPALINATION-----------------------------------

This code defines a Flask web application that uses a simple load balancing mechanism for serving machine learning models.

The ML class is defined, which has the following attributes and methods:

avaliable_models: a dictionary that maps model names to their file paths.
loaded_models_limit: an integer that specifies the maximum number of models that can be loaded at once.
loaded_models: a dictionary that maps loaded model names to their file paths.
request_counters: a Counter object that counts the number of requests received by each loaded model.
The load_weights method loads the file path for a given model name from the avaliable_models dictionary.

The load_balancer method is the load balancing mechanism that is called when a new request is received. It updates the request_counters for each loaded model, finds the least frequently requested model using the min function on the request_counters dictionary, unloads the least frequent model, loads the new model, and resets the request counter for the unloaded model.

The Flask web application is defined using the Flask class, and an instance of the ML class is created as ml.

Two routes are defined:

The '/' route renders an HTML template that displays the names of the currently loaded models.
The '/process_request' route processes a new request by getting the model name from the form data, checking if the model is already loaded, and if not, calling the load_balancer method to load the model. The method then returns a string indicating which model processed the request.
The try and except blocks in the process_request function catch and print any exceptions that occur during request processing.

Finally, the __main__ block starts the Flask application and runs it in debug mode.
