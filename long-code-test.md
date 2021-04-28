# Intro

This is a coding test for GoGoVan back-end positions.

You're free to use what tools you want,
but we use Ruby

We don't expect you to complete everything,
so choose the scope you think you have time for.

Variations from this are welcome,
as long as you tackle something similar.

We'll assess you on how you design your software, with a view to it being extended and modified over time.

# Concept

Pets.local is the hottest startup yet to come out of Hong Kong.

They provide a soft real-time, location-based matching service for Customers who are looking to find a new Pet.

## Your Task

Build a basic system for matching Pets and Customers

## Entities

### Pet

A pet, looking for a new home.

Properties

* id - integer
* name - string
* available_from - timestamp
* age - integer
* species - string
  * cat
  * dog
  * rabbit
* breed - string (for a dog) 
  * labrador
  * poodle
  * spaniel
  * terrier

### Customer

People looking for pets

* id - integer
* preference - *CustomerPreference

### Customer Preference

A description of a customer's preference for a pet

They could be very permissive "anything will do",
or be very restricitive "only poodles aged < 2"

* age - a range 
* species - a list of species they'd accept
* breed - if they accept dogs, they can select a list of breeds they'd accept

## API

### POST /pets

Add a new pet to the system, with all the properties described above

### GET /pets/{id}

Fetch the pet by ID

### GET /pets/{id}/matches

Get an array of "matching" customers for the given pet

### POST /customers

Add a new customer to the system

Together with their preferences for pets

### GET /customers/{id}

Fetch the customer by ID

### GET /customers/{id}/matches

Get an array of "matching" Pets for the given customer

### POST /customers/{id}/adopt?pet_id={pet_id}

The Customer adopts the given Pet

The Pet and Customer should no longer appear in `/matches` queries

# Extension #1 - Real-Time

Use Websockets (or something similar) to allow Customers to subscribe for the latest pet matches.

Demonstrate with a browser app that allows us to subscribe as a customer,
and push new pets into the system.

## Example

Alice only likes "Poodles ages <= 2"
Bob like "Dogs and Cats"
Charlie likes anything

We should be able to open a browser window for each Customer,
and when we create a new "Poodle aged 3" see it apppear on Bob and Charlie's screens, but not Alice's

# Extension #2 - Location

Pets can be positioned anywhere around Hong Kong

Customers can travel around Hong Kong, and see the nearest Pets to them

## Options

* Sort the `matches` by distance
* Create a map view of Pets relative to the Customer's location

# Extension #3 - Scale

Pets.local is growing rapidly.

It expects to hit the following metrics soon:

* 10,000 pets on its books at any one time
* 5,000 customers browsing at any one time

Explain how your code will scale to this level.
