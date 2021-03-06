# Angular Labs
Labs for the Angular Courses

## Getting started
1. [Prerequisites](#prerequisites)
1. [To install on your machine](#to-install-on-your-machine)
1. [Lab instructions](#lab-instructions)
1. [To run the labs](#to-run-the-labs)
1. [To run a solution](#to-run-a-solution)
1. [About the warehouse](#about-the-warehouse)
1. [RESTful APIs](#restful-apis)

## Prerequisites
There are only four things needed for setup and to run the labs:
* bash 

You'll know you have it if you can ...

```
bash --version
```

and you get a version.

* node ^6.7 and npm

You'll know you have it if you can ...

```
node --version
```

and you get a version greater than 6.7.0;

* The Angular CLI

You'll know you have it if you can ...

```
ng --version
```

and you get a version.

* mongoDB ^3
You'll know you have it if you can ...

```
mongod --version
```

and you get a version greater than 3.


## To install on your machine

To setup, look in the setup folder. Run these commands:

```
installLab.bash
```

## Lab instructions

Each lab's instructions are located in the instructions folder. 


## To run the lab site
```
cd warehouse
npm start
```
This will compile the app and begin serving it.
Point your browser to http://localhost:4200

## To run the solutions
Each lab can be run without copying any files. Just open a bash shell, cd to the lab solution folder and type in 
```
npm install
npm start
```
If you want to use a solution from a prior lab as a starter, either copy the whole folder to a new one or simply begin editing the code in that folder.

# About the warehouse
We have products, locations, orders, and customers. They are stored in collections (ie. tables) in a mongo database.

## Orders
Have a status:
* 0 - Ready to pick, pack, and ship
* 1 - Shipped
* 2 - Has problem(s) that a supervisor should fix

## Locations
LocationID is a string with this format: AASHB
* AA- Aisle - 01-99
* S - Slot - A-Z
* H - Shelf - 1-9
* B - Bin - A-Z
For example, 
01A1A = Aisle 1, Slot A, Shelf 1, Bin A

Only one product will be stored in a location so locationID is a primary key

# RESTful APIs
## Orders
* GET /api/orders/readyToShip - Get a list of orders that are ready to ship (status=0 means "ready to ship". status=1 means "shipped")
* GET /api/orders/ - Get a list of all orders
* GET /api/orders/<id> - Get a single order
* PATCH /api/orders/<id>/markAsShipped - Mark the order as "shipped" (status=1)
* PATCH /api/orders/<id>/markAsProblem - Mark the order as "has a problem" (status=2)
* POST /api/orders/ - Create a new order. New order record is in the body.
* PUT /api/orders/<id> - Replace the order with what is in the body.
* DELETE /api/orders/<id> - Delete the order
* PATCH /api/orders/<id> - Update the order with the values in the body.
## Products
* GET /api/products - All products
* GET /api/products/<id> - A single product with that id (ids are between 1 and about 77 currently)
* GET /api/products/featured - All featured products (Those we want to promote. Have featured==true)
* GET /api/products?search=<searchString> - All products with searchString as part of the name.
* PUT /api/products - Insert a new product into the database. The product's fields are in the body.
* PATCH /api/products/<id> - Update the product. Updated fields are in the body.
* DELETE /api/products/<id> - Delete the product
## Customers
## Categories
## Locations