# SQL-XAMPP -> CREATE DATABASES for a toy store ;

Create the toy store tables : customers, address, orders, order item and store products.

Database design -> https://app.dbdesigner.net/





![sql](https://user-images.githubusercontent.com/120104620/224477805-f584da92-e26b-4b3e-ad06-c00d706394a3.png)




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

