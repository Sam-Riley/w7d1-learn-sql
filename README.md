1) How many users are there?
select * count from users //50

2)What are the 5 most expensive items?
select price from items order by price desc;
//9984, 9859, 9790, 9390, 9341
select * items from items order by price desc limit 5;
//id          title                category                    description                         price     
----------  -------------------  --------------------------  ----------------------------------  ----------
25          Small Cotton Gloves  Automotive, Shoes & Beauty  Multi-layered modular service-desk  9984      
83          Small Wooden Comput  Health                      Re-engineered fault-tolerant adapt  9859      
100         Awesome Granite Pan  Toys & Books                Upgradable 24/7 access              9790      
40          Sleek Wooden Hat     Music & Baby                Quality-focused heuristic info-med  9390      
60          Ergonomic Steel Car  Books & Outdoors            Enterprise-wide secondary firmware  9341      


3)What's the cheapest book? (Does that change for "category is exactly 'book'" versus "category contains 'book'"?)
select price, title, category from items where category like '%books%' order by price
   ...> ;
price       title                    category  
----------  -----------------------  ----------
1496        Ergonomic Granite Chair  Books     
1727        Small Cotton Hat         Beauty & B
2377        Incredible Granite Comp  Books, Toy
3056        Practical Plastic Hat    Books     
6584        Fantastic Plastic Glove  Beauty, Mo
6720        Fantastic Rubber Shirt   Toys & Boo
8904        Fantastic Rubber Shoes   Books     
9246        Fantastic Steel Chair    Books     
9341        Ergonomic Steel Car      Books & Ou
9790        Awesome Granite Pants    Toys & Boo
select price, title, category from items where category='Books' order by price, title, category
   ...> ;
price       title                    category  
----------  -----------------------  ----------
1496        Ergonomic Granite Chair  Books     
3056        Practical Plastic Hat    Books     
8904        Fantastic Rubber Shoes   Books     
9246        Fantastic Steel Chair    Books     


4)Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?
select user_id from addresses where street like '%Zetta%'; //40
select * from addresses where user_id like '40';
id          user_id     street            city        state       zip       
----------  ----------  ----------------  ----------  ----------  ----------
43          40          6439 Zetta Hills  Willmouth   WY          15029     
44          40          54369 Wolff Forg  Lake Bryon  CA          31587   
select addresses.user_id, users.first_name, users.last_name from addresses inner join users on addresses.user_id=users.id where street like '%Zetta%';
user_id     first_name  last_name
----------  ----------  ----------
40          Corrine     Little    
sqlite>

5)Correct Virginie Mitchell's address to "New York, NY, 10108".
