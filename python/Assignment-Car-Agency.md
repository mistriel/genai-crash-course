## Car Agency Pricing and Lot Assignment

**Objective:** Develop a system to evaluate and manage the pricing and physical placement of vehicles within a car agency's parking lots based on defined criteria.

**Context:**
The agency operates with three distinct parking lots, each designated for vehicles meeting specific age and evaluated price thresholds:

* **Front Lot:** Reserved for vehicles manufactured within the last 5 years and having an `EvaluatedPrice` not less than 20% of their `MarketPrice`.
* **Middle Lot:** Reserved for vehicles manufactured within the last 10 years and having an `EvaluatedPrice` not less than 30% of their `MarketPrice`.
* **Back Lot:** Accommodates all other vehicles that do not meet the criteria for the Front or Middle lots.

**Car Inventory:**
In the `resources` folder, you will find a JSON file named `car_agency_inventory.json`. This file contains a list of cars with their respective attributes. You can use this data to populate the `ParkingLot` structure.

**Car Class Attributes:**

* `Name`: String
* `Model`: String
* `Brand`: String
* `Year`: Integer (Manufacturing Year)
* `MarketPrice`: Integer (Original Market Value)
* `EvaluatedPrice`: Integer (Calculated price after applying cost reductions)
* `Mileage`: Integer (Total distance covered)
* `Previous Owners`: Integer (Number of prior owners)
* `Color Integrity`: Array of tuples, where each tuple is `(IssueType: String, Quantity: Integer)`. IssueType can be "Dent", "Scratch", "Chips", or "Bend". Example: `[("Dent", 3), ("Chips", 1)]`
* `Accident History`: List of strings, indicating types of damage from accidents. Allowed values: "Dent", "Scratch", "PaintChips", "InteriorDamage", "Mechanical", "Chassis". Repetition of types is possible. Example: `["Chassis", "Mechanical"]`

## Cost Reduction Rules (Applied during Evaluation):

* **Mileage:**
    * `> 250,000`: 30% reduction from Market Price
    * `150,001 - 250,000`: 25% reduction from Market Price
    * `100,001 - 150,000`: 20% reduction from Market Price
    * `50,001 - 100,000`: 10% reduction from Market Price
* **Previous Owners:**
    * 5% reduction per owner from Market Price
* **Paint Issues (Deducted in USD):**
    * Scratch: $50 per instance
    * Dent: $100 per instance
    * Chips: $200 per instance
    * Bend: $300 per instance
* **Accident:**
    * Chassis Damage: 30% reduction from Market Price

    
## Assignments:

**Style Guide:** Ensure that the code adheres to PEP 8 style guidelines for Python.

1.  **Car Class Modeling:** Design and implement a `Car` class to encapsulate vehicle attributes.
2.  **JSON Data Parsing:** Write a function to read the `car_agency_inventory.json` file and create instances of the `Car` class for each vehicle in the inventory.
3.  **ParkingLot Class Modeling:** Design and implement a `ParkingLot` class or structure to manage vehicles assigned to each lot. </br>
   a.  **Evaluation Function:** Implement a function to calculate a car's `EvaluatedPrice` based on the specified cost reduction rules. </br>
   b.  **Constructor:** `ParkingLot` class constructor should use the above function to evaluate the price of each car and assign it to the appropriate lot. </br>
4. **Display Function:** Implement a function to display the cars in `ParkingLot`, include the following attributes: `brand`, `name`, `model`, `year` `EvaluatedPrice`  </br>
   a.  Each row contains 3 cars </br>
   b.  Display the lot name and the number of cars in it </br>
   c.  Try to maintain equal spacing between the rows and columns </br>


### Bonus:
1.  **Data Validation:** Implement validation checks to ensure that the data read from the JSON file is in the expected format and handle any discrepancies gracefully.
2.  **Pydantic Validation:** Use Pydantic to validate the attributes of the `Car` class. Ensure that the `Year` is a valid integer, `MarketPrice` and `EvaluatedPrice` are positive integers, and `Mileage` is a non-negative integer. Validate that `Color Integrity` contains valid issue types and quantities. Validate that `Accident History` contains valid damage types.
