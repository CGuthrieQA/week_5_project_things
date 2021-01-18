# SQL Database Design

![ERD](ERD.png)

## setup 

```SQL
drop schema ims;
CREATE SCHEMA IF NOT EXISTS `ims`;
USE `ims`;
```

## customer

```SQL
CREATE TABLE IF NOT EXISTS `ims` . `customer` (
	`id` INT(11) NOT NULL PRIMARY KEY AUTO_INCREMENT,
	`first_name` VARCHAR(30) NULL DEFAULT NULL,
	`last_name` VARCHAR(30) NULL DEFAULT NULL,
	PRIMARY KEY (`id`)
);
```

## order

```SQL
CREATE TABLE IF NOT EXISTS `ims` . `order` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`fk_customer_id` INT NOT NULL,
	PRIMARY KEY (`id`),
	FOREIGN KEY (`fk_customer_id`) REFERENCES customer(`id`)
);
```

## orders_items

```SQL
CREATE TABLE IF NOT EXISTS `ims` . `order_items` (
	`fk_order_id` INT NOT NULL,
	`fk_item_id` INT NOT NULL,
	FOREIGN KEY (`fk_order_id`) REFERENCES order(`id`),
	FOREIGN KEY (`fk_item_id`) REFERENCES item(`id`)
);
```

## item

```SQL
CREATE TABLE IF NOT EXISTS `ims` . `item` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`name` VARCHAR(50) NOT NULL,
	`value` DECIMAL(5,2) NOT NULL,
	PRIMARY KEY (`id`)
);
```