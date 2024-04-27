###  RAW SQL queries:
##### About The Project 
##### 1. normalization of a datatabese
###### by raw sql queries - one table remade as a system of 4 tables relates with each other by forein keys
![изображение](https://github.com/vadimlvov71/sql/assets/57807117/5e91af0b-e821-42a7-a4ce-349ff8c195e9)

* [github normalization](https://github.com/vadimlvov71/sql/blob/main/normalization)
* ![изображение](https://github.com/vadimlvov71/sql/assets/57807117/755d5305-1b46-466a-97a8-63ce99f48b4e)
* result:
* only one foreign key:
![изображение](https://github.com/vadimlvov71/sql/assets/57807117/d25052cc-6b79-4d4b-9bde-6b12081f8866)

* with new tables:
* cities,regions anf areas(oblast)
* * only one foreign key:
 
  * ![изображение](https://github.com/vadimlvov71/sql/assets/57807117/0de2df5d-7bf4-4cae-a5bb-9d0e7fe5853f)

* result:
 ```sh

SELECT cc.id,
c.name_uk as city_name,
r.name_uk as region_name,
a.name_uk as area_name 
FROM `catalog_city` as cc
LEFT JOIN cities as c
ON cc.city_id = c.id
LEFT JOIN regions as r
ON c.id_region = r.id
LEFT JOIN areas as a
ON r.id_area = a.id;
   ```

![изображение](https://github.com/vadimlvov71/sql/assets/57807117/e090d422-1d60-4e65-9c0a-cdf45701248a)


