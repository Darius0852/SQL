# SQL

##Notes


##Questions from TestDome

1)

Write a query that select all distinct pet names.

ANSWER:

  SELECT name FROM dogs 
  UNION 
  SELECT name FROM cats

2)

write a query that returns the number of students whose first name is John.

ANSWER:

  SELECT COUNT(*) FROM students WHERE firstName = "John";

3)

The following data definition defines an organization's employee hierarchy.
An employee is a manager if any other employee has their managerId set to this employee's id. That means John is a manager if at least one other employee has their managerId set to John's id.
TABLE employees
  id INTEGER NOT NULL PRIMARY KEY
  managerId INTEGER REFERENCES employees(id)
  name VARCHAR(30) NOT NULL


ANSWER:

  SELECT name FROM employees
  WHERE id NOT IN (SELECT managerId from employees WHERE managerId IS NOT NULL)

4)

Each item in a web shop belongs to a seller. To ensure service quality, each seller has a rating.
The data are kept in the following two tables:
TABLE sellers
  id INTEGER PRIMARY KEY,
  name VARCHAR(30) NOT NULL,
  rating INTEGER NOT NULL

TABLE items
  id INTEGER PRIMARY KEY,
  name VARCHAR(30) NOT NULL,
  sellerId INTEGER REFERENCES sellers(id)
Write a query that selects the item name and the name of its seller for each item that belongs to a seller with a rating greater than 4. The query should return the name of the item as the first column and name of the seller as the second column.

ANSWER:

  select items.name, sellers.name from items
  join sellers on items.sellerId = sellers.id
  where sellers.rating > 4;

5)

