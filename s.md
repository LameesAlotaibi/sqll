create database storre;
use storre;
create table countries (
code  int not null primary key,
name varchar (20) unique ,
continent_name varchar(20) not null

);
create table users (
id int not null primary key ,
full_name varchar(20) not null ,
email varchar(20) unique,
gender char (1) check (gender='f' or gender ='m'),
date_of_bitrh varchar(15) ,
created_at datetime  ,
country_code int unique

);
create table orders (
id int not null primary key  ,
status varchar(6) check (status='start ' or status='finish'),
created_at datetime,
user_id int unique

);
create table products (
id int not null primary key ,
name varchar(20)not null ,
price int default 0 ,
status varchar (10) check(status = 'valid' or status= 'expired'),
created_at datetime 

);
create table order_products(
order_id int not null ,
product_id int,
quantity int default 0 ,
 primary key (order_id,product_id)
);
alter table users 
add foreign key (country_code) REFERENCES countries (code);

alter table orders 
add foreign key (user_id) REFERENCES users (id);
alter table order_products 
add foreign key (order_id) REFERENCES orders (id);
alter table order_products 
add foreign key (product_id) REFERENCES products (id);


INSERT INTO countries (code, name, continent_name)
VALUES (1,"lamees","asia");
insert into users 
values (11,"lamees alotaibi","lam@GMAIL.COM","f","99-02-07","2000-07-09 2:30:54",101);
insert into orders
values  (09,1,'start','2022-04-12 2:13:55');
insert into products
values  (11,"lamees",356,'expiered','1999-09-09 3:40:43');
insert into order_product
values  (112345,87654,6);
update countries
set continent_name ='africa'
where code =1;
delete from products where id =11;



