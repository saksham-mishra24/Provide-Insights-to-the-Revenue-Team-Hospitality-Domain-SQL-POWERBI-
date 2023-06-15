## We will query the given metrics

## 1. Revenue -

```` sql
SELECT
  CONCAT(ROUND(SUM(revenue_realized) / 1000000 , 0), ' M') AS Revenue
FROM bookings_Table;
````
#### Answer:

```
Revenue 
 1709 M
``` 

## 2. Total Bookings	 -

```` sql
SELECT 
  CONCAT(COUNT(booking_id)/ 1000, ' K') AS Total_Bookings
FROM bookings_Table 
````
#### Answer:

```
Total_Bookings 
134 K
```
## 3. Total Capacity		 -

```` sql
SELECT 
  CONCAT(ROUND(SUM(capacity)/ 1000,0), ' K') AS Total_capacity
FROM aggregated_bookings_Table
````
#### Answer:

```
Total_capacity 
233 K
``` 

## 4. Total Successful Bookings		 -

```` sql
SELECT  
  CONCAT(ROUND(SUM(successful_bookings) / 1000,0), ' K') AS Total_Successful_Bookings 
FROM aggregated_bookings_Table 

````
#### Answer:

```
Total_Successful_Bookings 
135 K
``` 
## 5. Occupancy_percent	 -

```` sql
SELECT
    CONCAT(ROUND(SUM(successful_bookings) / SUM(capacity) * 100, 1), '%') AS Occupancy_percent
FROM aggregated_bookings_Table
````
#### Answer:

```
Occupancy_percent
57.9%
```

## 6. Average Rating			 -

```` sql
SELECT 
  ROUND(AVG(ratings_given), 2) as  Average_Rating	 
FROM bookings_Table 
````
#### Answer:

```
Average_Rating 
3.62
```
## 7. Number of days			 -

```` sql
SELECT 
  COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
FROM Date_Table 
````
#### Answer:

```
NO_OF_DAYS 
92
```

## 8. Total cancelled bookings		 -

```` sql
SELECT 
  CONCAT(round(COUNT(*)/ 1000,0), ' K') AS TOTAL_CANCELLED_BOOKING  
FROM bookings_Table  
WHERE booking_status = 'CANCELLED'
````
#### Answer:

```
TOTAL_CANCELLED_BOOKING 
33 K
```

## 9. Cancellation_percent			 -

```` sql
 SELECT 
  CONCAT(ROUND((CAST(COUNT(*) AS FLOAT) / (SELECT COUNT(*) FROM bookings_Table)) * 100, 2), '%') AS Cancellation_Percentage
FROM bookings_Table
WHERE booking_status = 'CANCELLED';

````

#### Answer:

```
Cancellation_Percentage
24.83 %
```

## 10. Total Checked Out -

```` sql
SELECT 
  COUNT(*) AS TOTAL_CHECKED_OUT 
FROM bookings_Table 
WHERE booking_status = 'Checked Out'
````
#### Answer:

```
TOTAL_CHECKED_OUT
94411
```

## 11. Total no show bookings	-

```` sql
SELECT 
  COUNT(*) AS Total_Noshow_bookings
FROM bookings_Table  
WHERE booking_status = 'No Show'
````
#### Answer:

```
Total_Noshow_bookings
6759
```

## 12. No Show rate %	 -

```` sql
 SELECT 
  CONCAT(ROUND((CAST(COUNT(*) AS FLOAT) / (SELECT COUNT(*) FROM bookings_Table)) * 100, 2), '%') AS Noshow_Percentage
FROM bookings_Table
WHERE booking_status = 'NO SHOW';
````
#### Answer:

```
Noshow_Percentage
5.04%
```

## 13. Booking % by Platform	-

```` sql
SELECT 
    booking_platform,
    CONCAT(ROUND(CAST(COUNT(*) * 100.0 / (SELECT COUNT(*) FROM bookings_Table) as float),2),'%') AS Booking_Percentage
FROM bookings_Table
GROUP BY booking_platform
ORDER BY COUNT(*) * 100.0 / (SELECT COUNT(*) FROM bookings_Table)  DESC
````
#### Answer:

| booking_platform | Booking_Percentage | 
| ----------- | ---------- |
|others	| 40.91%|
|makeyourtrip	|19.99% |
|logtrip|	10.96%|
|direct online|	9.94%|
|tripster|	7.16%|
|journey|	6.02%|
|direct offline	|5.02%|

## 14. Booking % by Room class	 -

```` sql

SELECT 
    R.room_class,
    CONCAT(ROUND(CAST(COUNT(*) * 100.0 / (SELECT COUNT(*) FROM bookings_Table) as float),2),'%') AS Booking_Percentage
FROM bookings_Table  B 
JOIN ROOMS R
ON B.room_category = R.room_id
GROUP BY R.room_class
ORDER BY BookingPercentage DESC
````
#### Answer:

|room_class	|Booking_Percentage|
| ----------- | ---------- |
|Elite|	36.78%|
|Standard|	28.57%|
|Premium|22.71%|
|Presidential|	11.94%|


## 15. ADR -

```` sql
SELECT 
  ROUND(SUM(revenue_realized)/COUNT(booking_id),0) AS ADR
FROM bookings_Table

````
#### Answer:

```
ADR
12696
```
## 16. Realisation %		-

```` sql
 WITH 
  Cancellation_Query AS (
    SELECT 
      ROUND((CAST(TOTAL_CANCELLED_BOOKING AS FLOAT) / Total_Bookings) * 100, 2) AS Cancellation_Percentage
    FROM
      (SELECT COUNT(*) AS TOTAL_CANCELLED_BOOKING FROM bookings_Table WHERE booking_status = 'CANCELLED') AS cancelled_bookings,
      (SELECT COUNT(booking_id) AS Total_Bookings FROM bookings_Table) AS total_bookings
  ),
  NoShow_Query AS (
    SELECT 
      ROUND((CAST(TOTAL_NO_SHOW_BOOKING AS FLOAT) / Total_Bookings) * 100, 2) AS NoShow_Percentage
    FROM
      (SELECT COUNT(*) AS TOTAL_NO_SHOW_BOOKING FROM bookings_Table WHERE booking_status = 'NO SHOW') AS no_show_bookings,
      (SELECT COUNT(booking_id) AS Total_Bookings FROM bookings_Table) AS total_bookings
  )
SELECT 
  CONCAT(ROUND((1 - (Cancellation_Percentage / 100 + NoShow_Percentage / 100)) * 100, 2), '%') AS Realisation_Percentage
FROM
  Cancellation_Query,
  NoShow_Query;
````
#### Answer:

```
Realisation_Percentage
70.15%
```

## 17. RevPAR	-

```` sql
SELECT
  ROUND(SUM(revenue) / SUM(capacity_total),0) AS RevPAR 
  FROM 
  (
  SELECT SUM(revenue_realized) AS revenue 
    FROM bookings_Table) AS revenue_table, 
  (
  SELECT SUM(capacity) AS capacity_total 
     FROM aggregated_bookings_Table) AS capacity_table;

````
#### Answer:

```
RevPAR
7347
```

## 18. DBRN	-

```` sql
SELECT 
  booking / NO_OF_DAYS AS DBRN
FROM (
      SELECT counT(booking_id) AS booking 
      FROM bookings_Table) AS [Total Bookings], 
    (
     SELECT COUNT(DISTINCT(DATE))as NO_OF_DAYS
     FROM Date_Table ) AS No_of_days;
````
#### Answer:

```
DBRN
1462
```

## 19. DSRN	-

```` sql

SELECT 
  booking / NO_OF_DAYS AS DSRN 
FROM (
      SELECT SUM(capacity) AS booking 
      FROM aggregated_bookings_Table) AS [Total Bookings], 
    (
     SELECT COUNT(DISTINCT(DATE))as NO_OF_DAYS 
     FROM Date_Table ) AS No_of_days;
````
#### Answer:

```
DSRN
2528
```
## 20. DURN	-

```` sql
SELECT 
  booking / NO_OF_DAYS AS DURN 
FROM (
      SELECT COUNT(*) AS booking 
      FROM bookings_Table
      WHERE booking_status = 'Checked Out') AS [Total Bookings], 
    (
      SELECT COUNT(DISTINCT(DATE))as NO_OF_DAYS
      FROM Date_Table ) AS No_of_days;

````
#### Answer:

```
DURN
1026
```






