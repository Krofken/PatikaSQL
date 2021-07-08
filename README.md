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
