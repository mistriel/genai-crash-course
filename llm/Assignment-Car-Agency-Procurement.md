# Car Agency Procurement
Following previous assignment, GenAi Car agency has decided to procure a new fleet of cars. </br>
The agency provides a quote for the new car, and the procurement department will evaluate the quote based on the following criteria:  </br>

## Estimated Price Evaluation
In order to evaluate the price of a new car, the procurement department will use the following steps:
- Acquire the car's `market_price`
- Calculate the `evaluated_price` using the `Cost Reduction Rules` method.
- Check if the car can be parked in the parking lot based on lot vacancy.

Prepare the following methods:

### Market Price Knowledge Base

Under `resources` you will find a JSON file `car_agency_inventory.json` from the previous assignment that contains the market price of cars.
1. Create a `market_price_evaluation` method that lookup the price index for cars of the same model and brand.
2. If no cars of same model and brand were found, return `None`.
3. If found, return a list of tuples with the following attributes:
   - `Brand`
   - `Model`
   - `Year`
   - `MarketPrice`

### Estimated Price Evaluation 
From the previous assignment, you have already implemented the `evaluate_car_price` method.
The method gets a car with the `market_price` and returns the `car` with the final `evaluated_price`.


### Parking Lot Vacancy
Extend the `ParkingLot` class so each lot has a `maximum`  and `current` number of cars. The `maximum` number of cars is set when the lot is created. The `current` number of cars is updated when a car is added or removed from the lot.
Create a method `check_vacancy` that checks if the lot has enough space for a new car. If the lot is full, return `True`. Otherwise, return `False`.

## Assignment Details 
Configure the LLM to return a quote for the new car or a proper decline reason if the car cannot be procured.

1. Create a prompt that asks the LLM to create a quote for the new car. Use the `market_price_evaluation` method to inject `few shots` examples of the car's market price.
2. Ask the prompt to evaluate the price given the examples or decline the car with `No Prior Knowledge` if no prior examples found.
3. Extend the LLM with function calling to call the `evaluate_car_price` method in order to calculate the `evaluated_price`.
4. Extend the LLM with function calling to call the `check_vacancy` method in order to check if the lot has enough space for a new car.
5. If the lot is full, return a 'Parking Lot is Full` decline reason. Otherwise, return the quote for the new car.
6. Print the debugging information for critical steps in the process.
7. Bonus: use prompt caching for the prompt in bullet #1 so queries for the same brand and model are cached.