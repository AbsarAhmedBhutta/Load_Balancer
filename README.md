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
