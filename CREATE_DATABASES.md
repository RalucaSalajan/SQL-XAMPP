# SQL-XAMPP -> DATABASES for a toy store ;

## Create the toy store tables : customers, address, orders, order item and store products. ##

*Database design -> https://app.dbdesigner.net/*




![sql](https://user-images.githubusercontent.com/120104620/224480465-132e918f-5ff7-4f3c-9256-f39c16777fda.png)






CREATE TABLE `customer` (

  `CustomerID` INT AUTO_INCREMENT PRIMARY KEY,
  
  `CustomerName` varchar(32) NOT NULL,
  
  `CustomerSurname` varchar(32) NOT NULL,
  
  `CustomerAge` int(11) NOT NULL
  
) 

INSERT INTO `customer` (`CustomerID`, `CustomerName`, `CustomerSurname`, `CustomerAge`) VALUES

(1, 'Anna', 'Pop', 25),

(2, 'Daniela', 'Gopa', 65),

(3, 'Hans', 'Mihael', 35),

(4, 'Maria', 'Petre', 45),

(5, 'Emma', 'Golesa', 45);


CREATE TABLE `address` (

  `AddressID` INT AUTO_INCREMENT PRIMARY KEY,
  
  `CustomerID` INT UNSIGNED NOT NULL,
  
  `AddressDetails` varchar(128) NOT NULL,
  
  `AddressCity` varchar(32) NOT NULL
  
) 

INSERT INTO `address` (`AddressID`, `CustomerID`, `AddressDetails`, `AddressCity`) VALUES


(1, 1, 'str. Gari, nr.1', 'Cluj-Napoca'),

(2, 5, 'str. Magnoliei , nr.5', 'Calarasi'),

(3, 4, 'strada Noua 54', 'Satu Mare'),

(4, 3, 'Galaxiei 1', 'Cluj-Napoca'),

(5, 2, 'str. 1 Mai, nr.54', 'Constranta'),

(6, 2, 'str. Republicii, nr.2', 'Cluj-Napoca'),

(7, 1, 'Albinii 24', 'Brasov');

CREATE TABLE `order` (

  `OrderID` INT AUTO_INCREMENT PRIMARY KEY,
  
  `CustomerID` INT UNSIGNED NOT NULL,
  
  `AddressID` INT UNSIGNED NOT NULL
  
) 

INSERT INTO `order` (`OrderID`, `CustomerID`, `AddressID`) VALUES

(1, 1, 1),

(2, 2, 6),

(3, 3, 4);

CREATE TABLE `order_item` (

  `OrderItemID` INT AUTO_INCREMENT PRIMARY KEY,
  
  `OrderID` INT DEFAULT NULL,
  
  `ProductID` INT DEFAULT NULL,
  
  `OrderItemQuantity` INT DEFAULT NULL
  
) 

INSERT INTO `order_item` (`OrderItemID`, `OrderID`, `ProductID`, `OrderItemQuantity`) VALUES

(1, 1, 1, 2),

(2, 2, 2, 2),

(3, 2, 3, 1),

(4, 3, 4, 1),

(5, 3, 5, 1);

CREATE TABLE `toy` (

  `ToyID` INT AUTO_INCREMENT PRIMARY KEY,
  
  `ToyName` varchar(64) DEFAULT NULL,
  
  `ToyPrice` float DEFAULT NULL,
  
  `ToyDescription` varchar(32) NOT NULL
  
) 

INSERT INTO `toy` (`ToyID`, `ToyName`, `ToyPrice`,`ToyDescription`) VALUES

(1, 'PuzzelTrefl', 12,'Contains  24 pieces of puzzle'),

(2, 'Rhino', 15.3,'Contains 5 construction cars'),

(3, 'HotWheels', 25,'Contains a set of 23 pieces of race cars'),

(4, 'HotWheels', 17,'Contains 5 monster trucks'),

(5, 'Maisto', 25.5,'Contains a set of 22 cars'),

(6, 'Barbie', 47.5,'Contains a barbie doll');

![Screenshot 2023-03-11 130512](https://user-images.githubusercontent.com/120104620/224480722-c5a288e2-70f5-4902-8414-fec51d7e0a43.png)


## basic sql queries ##

-- list all the toys

SELECT * FROM toy

-- list all toys name that starts with “H”

SELECT * FROM toy WHERE ToyName LIKE 'H%' 

-- add a new toy

INSERT INTO toy VALUES (NULL, 'Barbie', 99,’Barbie doll mermaid’) 

-- update address city to user 1

UPDATE address SET AddressCity = 'Brasov' WHERE AddressID = 1 

-- delete address id 3 from address

DELETE FROM address WHERE AddressID = 3 

-- use JOIN: tabel customers name,surname with tabel addreess and city

SELECT customers.CustomerName, customers.CustomerSurname, addreess.AddressDetails, addreess.AddressCity 

FROM customer 

RIGHT JOIN address 

ON customers.CustomerID = addreess.CustomerID 


