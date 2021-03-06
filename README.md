# PatikaSQL
## <p id = 'Ödev 1' > Ödev 1 </p> 
#### Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
~~~sql
SELECT title,description FROM film;
~~~~
#### film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
~~~~sql
SELECT *  FROM film
WHERE length > 60 AND length < 75;
~~~~
#### film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
~~~~sql
SELECT *  FROM film
WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99
~~~~
#### customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
~~~~sql
SELECT last_name FROM customer
WHERE first_name = 'Mary';
~~~~
#### film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
~~~~sql
SELECT * FROM film
WHERE length < 50 AND NOT rental_rate = 2.99 AND NOT rental_rate = 4.99;
~~~~
## <p id = 'Ödev 2' > Ödev 2 </p> 
#### film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
~~~~sql
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
~~~~
#### actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
~~~~sql
SELECT first_name, last_name FROM actor
WHERE first_name IN ( 'Penelople' , 'Nick' , 'Ed' );
~~~~
#### film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. (IN operatörünü kullanınız.)
~~~~sql
SELECT * FROM film
WHERE rental_rate IN (0.99,2.99,4.99) AND replacement_cost IN ( 12.99 , 15.99 , 28.99 );
~~~~
## <p id = 'Ödev 3' > Ödev 3 </p>
#### country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
~~~~sql
SELECT country FROM country
WHERE country LIKE 'A%a';
~~~~
#### country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
~~~~sql
SELECT country FROM country
WHERE country LIKE '_____%n';
~~~~
#### film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
~~~~sql
SELECT title FROM film
WHERE title ILIKE '%t%t%t%t';
~~~~
#### film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
~~~~sql
SELECT * FROM film
WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;
~~~~
## <p id = 'Ödev 4' > Ödev 4 </p>
#### film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
~~~~sql
SELECT DISTINCT replacement_cost FROM film;
~~~~
#### film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır? 
~~~~sql
SELECT COUNT (DISTINCT replacement_cost) FROM film;
~~~~
#### film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
~~~~sql
SELECT COUNT (*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
~~~~
#### country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
~~~~sql
SELECT COUNT (*) FROM country
WHERE country LIKE '_____';
~~~~
#### city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
~~~~sql
SELECT COUNT (*) FROM city
WHERE city ILIKE '%r';
~~~~
## <p id = 'Ödev 5' > Ödev 5 </p>
#### film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
~~~~sql
SELECT title FROM film 
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
~~~~
#### film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
~~~~sql
SELECT title FROM film 
WHERE title LIKE '%n'
ORDER BY length ASC
OFFSET 5
LIMIT 5;
~~~~
#### customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
~~~~sql
SELECT last_name FROM customer 
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
~~~~
## <p id = 'Ödev 6' > Ödev 6 </p>
#### film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
~~~~sql
SELECT round(AVG(rentaL_rate),2) FROM film; 
~~~~
#### film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
~~~~sql
SELECT COUNT(title) FROM film 
WHERE title LIKE 'C%';
~~~~
#### film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
~~~~sql
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
~~~~
#### film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
~~~~sql
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;
~~~~
## <p id = 'Ödev 7' > Ödev 7 </p>
#### film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
~~~~sql
SELECT rating FROM film
GROUP BY rating;
~~~~
#### film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerinive karşılık gelen film sayısını sıralayınız.
~~~~sql
SELECT replacement_cost FROM film
GROUP BY replacement_cost
HAVING COUNT(title) <50;
~~~~
#### customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
~~~~sql
SELECT store_id , COUNT(*)  FROM customer
GROUP BY store_id;
~~~~
#### city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisinive şehir sayısını paylaşınız
~~~~sql
SELECT COUNT(*),country_id FROM city
GROUP BY country_id;
ORDER BY COUNT(*) DESC
LIMIT 1;
~~~~
## <p id = 'Ödev 8' > Ödev 8 </p>
#### test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
~~~~sql
CREATE TABLE employee(
   id INTEGER PRIMARY KEY, 
   name VARCHAR(50) NOT NULL,
   birthday DATE NOT NULL,
   email VARCHAR(100)
 ); 
~~~~
#### Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
~~~~sql
insert into employee (id, name, email, birthday) values (1, 'Bessy', 'bscarse0@alexa.com', '2021-01-13');
insert into employee (id, name, email, birthday) values (2, 'Avie', 'agerkens1@marketwatch.com', '2021-02-17');
insert into employee (id, name, email, birthday) values (3, 'Hewie', 'hhevner2@nyu.edu', '2021-04-09');
insert into employee (id, name, email, birthday) values (4, 'Chaim', 'cbruyett3@cdbaby.com', '2020-10-21');
insert into employee (id, name, email, birthday) values (5, 'Alisander', 'acoolbear4@squarespace.com', '2020-10-12');
insert into employee (id, name, email, birthday) values (6, 'Ethe', 'emuscroft5@utexas.edu', '2021-05-18');
insert into employee (id, name, email, birthday) values (7, 'Lilla', 'llamperd6@ox.ac.uk', '2020-11-07');
insert into employee (id, name, email, birthday) values (8, 'Wain', 'wackenhead7@squidoo.com', '2020-08-27');
insert into employee (id, name, email, birthday) values (9, 'Chelsie', 'cmacneill8@washingtonpost.com', '2020-11-27');
insert into employee (id, name, email, birthday) values (10, 'Dorris', 'dpingstone9@geocities.com', '2021-04-03');
insert into employee (id, name, email, birthday) values (11, 'Fina', 'fthorpa@google.com.br', '2021-01-07');
insert into employee (id, name, email, birthday) values (12, 'Ileana', 'ipindellb@upenn.edu', '2020-10-26');
insert into employee (id, name, email, birthday) values (13, 'Claudine', 'cdeveralc@opera.com', '2020-07-11');
insert into employee (id, name, email, birthday) values (14, 'Patricia', 'pschreinerd@youtu.be', '2020-10-04');
insert into employee (id, name, email, birthday) values (15, 'Chan', 'ctownere@phoca.cz', '2020-08-19');
insert into employee (id, name, email, birthday) values (16, 'Marcellina', 'mandreuccif@themeforest.net', '2021-07-07');
insert into employee (id, name, email, birthday) values (17, 'Rab', 'rlisciardellig@reddit.com', '2021-02-09');
insert into employee (id, name, email, birthday) values (18, 'Perkin', 'pkulash@ebay.com', '2021-06-29');
insert into employee (id, name, email, birthday) values (19, 'Violetta', 'vimorei@fema.gov', '2020-12-15');
insert into employee (id, name, email, birthday) values (20, 'Allie', 'amournianj@epa.gov', '2020-12-23');
insert into employee (id, name, email, birthday) values (21, 'Shelli', 'sabramovicik@ocn.ne.jp', '2021-03-20');
insert into employee (id, name, email, birthday) values (22, 'Ashly', 'aindgsl@irs.gov', '2020-07-29');
insert into employee (id, name, email, birthday) values (23, 'Angelo', 'asiberym@washingtonpost.com', '2021-03-27');
insert into employee (id, name, email, birthday) values (24, 'Lesli', 'lboydlen@rakuten.co.jp', '2021-04-21');
insert into employee (id, name, email, birthday) values (25, 'Cori', 'csmalecombeo@shareasale.com', '2020-12-12');
insert into employee (id, name, email, birthday) values (26, 'Gordan', 'gdelacotep@example.com', '2020-11-30');
insert into employee (id, name, email, birthday) values (27, 'Thacher', 'tvanderbeekq@theguardian.com', '2020-07-25');
insert into employee (id, name, email, birthday) values (28, 'Albie', 'apottipharr@bbc.co.uk', '2020-07-14');
insert into employee (id, name, email, birthday) values (29, 'Eddi', 'emilnthorpes@elegantthemes.com', '2021-03-26');
insert into employee (id, name, email, birthday) values (30, 'Murray', 'mtissellt@webmd.com', '2021-02-01');
insert into employee (id, name, email, birthday) values (31, 'Clareta', 'cgellandu@hc360.com', '2020-08-29');
insert into employee (id, name, email, birthday) values (32, 'Eustace', 'ekitchinerv@latimes.com', '2021-01-04');
insert into employee (id, name, email, birthday) values (33, 'Antoine', 'afeeleyw@vistaprint.com', '2021-05-28');
insert into employee (id, name, email, birthday) values (34, 'Nicky', 'nbesantx@ucoz.ru', '2020-07-11');
insert into employee (id, name, email, birthday) values (35, 'Welsh', 'wgrigoroniy@devhub.com', '2021-05-10');
insert into employee (id, name, email, birthday) values (36, 'Jacqui', 'jknightz@yahoo.co.jp', '2021-03-18');
insert into employee (id, name, email, birthday) values (37, 'Onfre', 'oplesing10@cdc.gov', '2020-09-10');
insert into employee (id, name, email, birthday) values (38, 'Ag', 'aproughten11@jimdo.com', '2020-11-20');
insert into employee (id, name, email, birthday) values (39, 'Robinson', 'rbottelstone12@ifeng.com', '2021-03-29');
insert into employee (id, name, email, birthday) values (40, 'Jule', 'jhurlston13@sciencedaily.com', '2021-04-01');
insert into employee (id, name, email, birthday) values (41, 'Terra', 'tbettington14@addtoany.com', '2021-05-15');
insert into employee (id, name, email, birthday) values (42, 'Aurea', 'akittiman15@dmoz.org', '2020-09-29');
insert into employee (id, name, email, birthday) values (43, 'Mendy', 'mfrowde16@thetimes.co.uk', '2020-08-28');
insert into employee (id, name, email, birthday) values (44, 'Ode', 'obrandoni17@tinypic.com', '2021-05-02');
insert into employee (id, name, email, birthday) values (45, 'Lucy', 'lmatiebe18@w3.org', '2020-12-28');
insert into employee (id, name, email, birthday) values (46, 'Vergil', 'vrawles19@reverbnation.com', '2020-12-24');
insert into employee (id, name, email, birthday) values (47, 'Case', 'cbrokenbrow1a@ca.gov', '2021-05-16');
insert into employee (id, name, email, birthday) values (48, 'Greer', 'gbarg1b@dagondesign.com', '2021-06-16');
insert into employee (id, name, email, birthday) values (49, 'Heddi', 'handrusov1c@wikia.com', '2021-04-09');
insert into employee (id, name, email, birthday) values (50, 'Ernestine', 'esleicht1d@mlb.com', '2021-02-02');
~~~~
#### Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
~~~~sql
UPDATE employee
   SET name = 'Invalid Name'
   WHERE name LIKE 'C%';
~~~~
#### Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
~~~~sql
DELETE FROM employee
 WHERE NAME LIKE '_____'
~~~~
## <p id = 'Ödev 9' > Ödev 9 </p>
#### 
~~~~sql

~~~~
