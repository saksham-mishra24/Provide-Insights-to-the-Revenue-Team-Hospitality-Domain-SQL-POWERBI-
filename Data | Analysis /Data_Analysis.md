
# 💰 REVENUE

### 🤯 Insights - https://tinyurl.com/2x5tva85

###  * Revenue :

```` sql
SELECT
  CONCAT(ROUND(SUM(revenue_realized) / 1000000 , 0), ' M') AS Revenue
FROM bookings_Table;
````
### Answer:

```
Revenue 
 1709 M
```

* MONTH-WISE :
```sql
SELECT
  B.Month_year,
  CONCAT(ROUND(SUM(A.revenue_generated) / 1000000, 0), ' M') AS Realised_generated,
  CONCAT(ROUND(SUM(A.revenue_realized) / 1000000, 0), ' M') AS Realised_revenue
FROM
  bookings_Table A
JOIN
  Date_Table B ON A.check_in_date = B.Date
GROUP BY
  B.Month_year
ORDER BY
  SUM(A.revenue_generated) DESC,
  SUM(A.revenue_realized) DESC;
```
#### Answer:
|Month_year|	Realised_generated|	Realised_revenue|
|---------|-------------|-------------|
|May 2022|	684 M|	582 M|
|Jul 2022|	672 M|	573 M|
|Jun 2022|	652 M|	554 M|

* CITY-WISE :
```sql

SELECT
  h.city,
  CONCAT(ROUND(SUM(b.revenue_generated) / 1000000, 0), ' M') AS Realised_generated,
  CONCAT(ROUND(SUM(b.revenue_realized) / 1000000, 0), ' M') AS Realized_revenue
FROM
  bookings_Table b
JOIN
  hotels h ON b.property_id = h.property_id
GROUP BY
  h.city
ORDER BY
  SUM(b.revenue_generated) DESC,
  SUM(b.revenue_realized) DESC;
```

|city	|Realised_generated	|Realized_revenue|
|---|----------|---------------|
|Mumbai	|785 M	|669 M|
|Bangalore|	495 M|	420 M|
|Hyderabad|	381 M|	325 M|
|Delhi|	346 M|	295 M|


* Day_type :
```sql
SELECT
  b.Day_type,
  CONCAT(ROUND(SUM(a.revenue_generated) / 1000000, 0), ' M') AS Realised_generated,
  CONCAT(ROUND(SUM(a.revenue_realized) / 1000000, 0), ' M') AS Realised_revenue
FROM
  bookings_Table A
JOIN
  Date_Table B ON A.check_in_date = B.Date
GROUP BY
  b.Day_type
ORDER BY
  SUM(a.revenue_generated) DESC,
  SUM(a.revenue_realized) DESC;
```

|Day_type|	Realised_generated|	Realised_revenue|
|---|----------|---------------|
|Weekday|	1259 M|	1070 M|
|Weekend|	748 M|	639 M|

*  ROOM_CLASS :

```SQL
SELECT
  r.room_class,
  CONCAT(ROUND(SUM(b.revenue_generated) / 1000000, 0), ' M') AS Realised_generated,
  CONCAT(ROUND(SUM(b.revenue_realized) / 1000000, 0), ' M') AS Realized_revenue
FROM
  bookings_Table b
JOIN
  rooms r ON b.room_category = r.room_id
GROUP BY
  r.room_class
ORDER BY
  SUM(b.revenue_generated) DESC,
  SUM(b.revenue_realized) DESC;
```

|room_class	|Realised_generated	|Realized_revenue|
|----------|----------|-------------|
|Elite|	659 M	|560 M|
|Premium|	544 M	|462 M
|Presidential|	441 M	|377 M
|Standard|	364 M|	310 M

*  Week_no :

```SQL

SELECT
  B.Week_no,
  CONCAT(ROUND(SUM(A.revenue_generated) / 1000000, 0), ' M') AS Realised_generated,
  CONCAT(ROUND(SUM(A.revenue_realized) / 1000000, 0), ' M') AS Realised_revenue
FROM
  bookings_Table A
JOIN
  Date_Table B ON A.check_in_date = B.Date
GROUP BY
  B.Week_no
ORDER BY
  SUM(A.revenue_generated) DESC,
  SUM(A.revenue_realized) DESC;
```

|Week_no	|Realised_generated	|Realised_revenue|
|----------|----------|-------------|
|24|	165 M|	140 M
|29|	164 M|	140 M
|27|	164 M|	140 M
|25|	164 M|	139 M
|22|	164 M|	139 M
|20|	163 M	|139 M
|19|	163 M|	138 M
|28|	163 M	|139 M
|23|	135 M|	116 M
|21|	135 M|	115 M
|31|	135 M|	115 M
|26|	135 M|	114 M
|30|	134 M|	115 M
|32|	25 M|	21 M


* PLATFORM :


```SQL
SELECT
  booking_platform,
  CONCAT(ROUND(SUM(revenue_generated) / 1000000, 0), ' M') AS Realised_generated,
  CONCAT(ROUND(SUM(revenue_realized) / 1000000, 0), ' M') AS Realized_revenue
FROM
  bookings_Table
GROUP BY
  booking_platform
ORDER BY
  SUM(revenue_generated) DESC,
  SUM(revenue_realized) DESC;
```

|booking_platform|	Realised_generated|	Realized_revenue|
|----------|----------|-------------|
|others|	821 M	|699 M
|makeyourtrip	|402 M|	341 M
|logtrip	|219 M	|188 M
|direct online	|199 M	|169 M
|tripster	|145 M	|123 M
|journey	|121 M	|103 M
|direct offline	|101 M	|86 M

* PROPERTY_NAME :


```SQL
SELECT
  h.property_name,
  CONCAT(ROUND(SUM(b.revenue_generated) / 1000000, 0), ' M') AS Realised_generated,
  CONCAT(ROUND(SUM(b.revenue_realized) / 1000000, 0), ' M') AS Realized_revenue
FROM
  bookings_Table b
JOIN
  hotels h ON b.property_id = h.property_id
GROUP BY
  h.property_name
ORDER BY
  SUM(b.revenue_generated) DESC,
  SUM(b.revenue_realized) DESC;
```

|property_name	|Realised_generated	|Realized_revenue
|------------|-----------------|--------------|
|Atliq Exotica	|375 M|	320 M
|Atliq Palace|	358 M	|304 M
|Atliq City|	337 M	|286 M
|Atliq Blu|	307 M	|261 M
|Atliq Bay|	305 M|	260 M
|Atliq Grands|	249 M	|212 M
|Atliq Seasons|	78 M	|66 M

* CATEGORY :

```SQL
SELECT
  h.category,
  CONCAT(ROUND(SUM(b.revenue_generated) / 1000000, 0), ' M') AS Realised_generated,
  CONCAT(ROUND(SUM(b.revenue_realized) / 1000000, 0), ' M') AS Realized_revenue
FROM
  bookings_Table b
JOIN
  hotels h ON b.property_id = h.property_id
GROUP BY
  h.category
ORDER BY
  SUM(b.revenue_generated) DESC,
  SUM(b.revenue_realized) DESC;
```

|category	|Realised_generated|	Realized_revenue|
|------------|-----------------|--------------|
|Luxury	|1235 M	|1053 M
|Business|	772 M	|656 M


## 🧑‍🤝‍🧑 Capacity | Total_Bookings | Total_cancelled_Bookings | Total_NO_Show
### 🤯 Insights - https://tinyurl.com/2b3hdyvx


* MONTH-WISE :

```sql
SELECT
    e.Month_year,
    CONCAT(ROUND(SUM(e.capacity) / 1000.0, 0), 'k') AS Total_capacity,
    CONCAT(CAST(ROUND(SUM(e.count_c) / 1000.0, 0) AS INT), 'k') AS Total_booking,
    CONCAT(CAST(ROUND(SUM(e.Cancelled_booking) / 1000.0, 0) AS INT), 'k') AS Cancelled_booking,
    CONCAT(CAST(ROUND(SUM(e.No_show) / 1000.0, 0) AS INT), 'k') AS Total_No_show
FROM (
    SELECT A.Month_year, A.capacity, NULL AS count_c, NULL AS Cancelled_booking, NULL AS No_show
    FROM (
        SELECT B.Month_year, SUM(A.capacity) AS capacity
        FROM aggregated_bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
        GROUP BY B.Month_year
    ) A
    UNION
    SELECT B.Month_year, NULL AS capacity, B.count_c, NULL AS Cancelled_booking, NULL AS No_show
    FROM (
        SELECT B.Month_year, COUNT(A.booking_id) AS count_c
        FROM bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
        GROUP BY B.Month_year
    ) B
    UNION
    SELECT c.Month_year, NULL AS capacity, NULL AS count_c, c.TOTAL_CANCELLED_BOOKING AS Cancelled_booking, NULL AS No_show
    FROM (
        SELECT B.Month_year, COUNT(*) AS TOTAL_CANCELLED_BOOKING
        FROM bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
        WHERE booking_status = 'CANCELLED'
        GROUP BY B.Month_year
    ) c
    UNION
    SELECT d.Month_year, NULL AS capacity, NULL AS count_c, NULL AS Cancelled_booking, d.TOTAL_NOSHOW AS No_show
    FROM (
        SELECT B.Month_year, COUNT(*) AS TOTAL_NOSHOW
        FROM bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
        WHERE booking_status = 'No Show'
        GROUP BY B.Month_year
    ) D
) e
GROUP BY e.Month_year
ORDER BY SUM(e.capacity) DESC, SUM(e.count_c) DESC, SUM(e.Cancelled_booking) DESC,SUM(e.No_show) DESC
```
#### Answer:

|Month_year|	Total_capacity   |	Total_booking	|Cancelled_booking|Total_no_show|
|----------|-------------------|-------------------|------------------|-------------|
|May 2022      |	78k	|46k	|11k|2k|
|Jul 2022	|78k|	45k	|11k|2k|
|Jun 2022|	76k|	44k|	11k|2k|


*  CITY :
```sql

SELECT
    e.city,
    CONCAT(ROUND(SUM(e.capacity) / 1000.0, 0), 'k') AS Total_capacity,
    CONCAT(CAST(ROUND(SUM(e.count_c) / 1000.0, 0) AS INT), 'k') AS Total_booking,
    CONCAT(CAST(ROUND(SUM(e.Cancelled_booking) / 1000.0, 0) AS INT), 'k') AS Cancelled_booking,
    CONCAT(CAST(ROUND(SUM(e.No_show) / 1000.0, 0) AS INT), 'k') AS Total_No_show
FROM (
    SELECT A.city, A.capacity, NULL AS count_c, NULL AS Cancelled_booking, NULL AS No_show
    FROM (
        SELECT h.city, SUM(A.capacity) AS capacity
        FROM aggregated_bookings_Table A
        JOIN hotels h ON a.property_id = h.property_id
        GROUP BY h.city
    ) A
    UNION
    SELECT B.city, NULL AS capacity, B.count_c, NULL AS Cancelled_booking, NULL AS No_show
    FROM (
        SELECT h.city, COUNT(A.booking_id) AS count_c
        FROM bookings_Table A
        JOIN hotels h ON a.property_id = h.property_id
        GROUP BY h.city
    ) B
    UNION
    SELECT c.city, NULL AS capacity, NULL AS count_c, c.TOTAL_CANCELLED_BOOKING AS Cancelled_booking, NULL AS No_show
    FROM (
        SELECT h.city, COUNT(*) AS TOTAL_CANCELLED_BOOKING
        FROM bookings_Table A
        JOIN hotels h ON a.property_id = h.property_id
        WHERE booking_status = 'CANCELLED'
        GROUP BY h.city
    ) c
    UNION
    SELECT d.city, NULL AS capacity, NULL AS count_c, NULL AS Cancelled_booking, d.TOTAL_NOSHOW AS No_show
    FROM (
        SELECT h.city, COUNT(*) AS TOTAL_NOSHOW
        FROM bookings_Table A
        JOIN hotels h ON a.property_id = h.property_id
        WHERE booking_status = 'No Show'
        GROUP BY h.city
    ) D
) e
GROUP BY e.city
ORDER BY SUM(e.capacity) DESC, SUM(e.count_c) DESC, SUM(e.Cancelled_booking) DESC,SUM(e.No_show) DESC
```
|city	|Total_capacity	|Total_booking	|Cancelled_booking	|Total_No_show|
|----------|-------------------|-------------------|------------------|-------------|
|Mumbai	   | 75k | 43k| 11k|	2k
|Hyderabad |60k  | 35k|	 9k|	2k
|Bangalore | 57k |32k|	 8k|	2k
|Delhi	   |40k	|24k|	 6k|	1k

* Day_type :
```sql

SELECT
    e.Day_type,
    CONCAT(ROUND(SUM(e.capacity) / 1000.0, 0), 'k') AS Total_capacity,
    CONCAT(CAST(ROUND(SUM(e.count_c) / 1000.0, 0) AS INT), 'k') AS Total_booking,
    CONCAT(CAST(ROUND(SUM(e.Cancelled_booking) / 1000.0, 0) AS INT), 'k') AS Cancelled_booking,
    CONCAT(CAST(ROUND(SUM(e.No_show) / 1000.0, 0) AS INT), 'k') AS Total_No_show
FROM (
    SELECT A.Day_type, A.capacity, NULL AS count_c, NULL AS Cancelled_booking, NULL AS No_show
    FROM (
        SELECT B.Day_type, SUM(A.capacity) AS capacity
        FROM aggregated_bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
        GROUP BY B.Day_type
    ) A
    UNION
    SELECT B.Day_type, NULL AS capacity, B.count_c, NULL AS Cancelled_booking, NULL AS No_show
    FROM (
        SELECT B.Day_type, COUNT(A.booking_id) AS count_c
        FROM bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
        GROUP BY B.Day_type
    ) B
    UNION
    SELECT c.Day_type, NULL AS capacity, NULL AS count_c, c.TOTAL_CANCELLED_BOOKING AS Cancelled_booking, NULL AS No_show
    FROM (
        SELECT B.Day_type, COUNT(*) AS TOTAL_CANCELLED_BOOKING
        FROM bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
        WHERE booking_status = 'CANCELLED'
        GROUP BY B.Day_type
    ) c
    UNION
    SELECT d.Day_type, NULL AS capacity, NULL AS count_c, NULL AS Cancelled_booking, d.TOTAL_NOSHOW AS No_show
    FROM (
        SELECT B.Day_type, COUNT(*) AS TOTAL_NOSHOW
        FROM bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
        WHERE booking_status = 'No Show'
        GROUP BY B.Day_type
    ) D
) e
GROUP BY e.Day_type
ORDER BY SUM(e.capacity) DESC, SUM(e.count_c) DESC, SUM(e.Cancelled_booking) DESC,SUM(e.No_show) DESC
```

|Day_type	|Total_capacity	|Total_booking|	Cancelled_booking|Total_No_show|
|----------|-------------------|-------------------|------------------|-----|
Weekday	|164k|	84k|	21k|	4k
Weekend	|68k|	50k|	12k|	3k

* ROOM_CLASS :

```SQL

SELECT e.room_class,
   CONCAT(ROUND(SUM(e.capacity) / 1000.0, 0), 'k') AS Total_capacity,
    CONCAT(CAST(ROUND(SUM(e.count_c) / 1000.0, 0) AS INT), 'k') AS Total_booking,
    CONCAT(CAST(ROUND(SUM(e.Cancelled_booking) / 1000.0, 0) AS INT), 'k') AS Cancelled_booking,
    CONCAT(CAST(ROUND(SUM(e.No_show) / 1000.0, 0) AS INT), 'k') AS Total_No_show
FROM (
    SELECT A.room_class, A.capacity, NULL as count_c,NULL AS Cancelled_booking, null as No_show
    FROM (
        SELECT r.room_class, SUM(A.capacity) as capacity
        FROM aggregated_bookings_Table A
        JOIN rooms r ON a.room_category = r.room_id
        GROUP BY  r.room_class) A
    UNION
    SELECT B.room_class, NULL as capacity, B.count_c,null as Cancelled_booking, null as No_show
    FROM (
        SELECT  r.room_class,COUNT(A.booking_id) as count_c
        FROM bookings_Table A
        JOIN rooms r ON a.room_category = r.room_id
        GROUP BY  r.room_class) B
    UNION
	SELECT  c.room_class, NULL as capacity, null as Total_booking, c.TOTAL_CANCELLED_BOOKING AS Cancelled_booking, null as No_show
    FROM (
        SELECT    r.room_class, COUNT(*) AS TOTAL_CANCELLED_BOOKING
        FROM bookings_Table A
        JOIN rooms r ON a.room_category = r.room_id
		WHERE booking_status = 'CANCELLED'
        GROUP BY   r.room_class
		) c
		UNION
    SELECT d.room_class, NULL AS capacity, NULL AS Total_booking, null AS Cancelled_booking, d.TOTAL_NOSHOW as No_show
    FROM (
        SELECT  r.room_class, COUNT(*) AS TOTAL_NOSHOW
        FROM bookings_Table A
       JOIN rooms r ON a.room_category = r.room_id
        WHERE booking_status ='No Show'
        GROUP BY  r.room_class) D
) e
GROUP BY e.room_class
ORDER BY SUM(e.capacity) DESC, SUM(e.count_c) DESC, SUM(e.Cancelled_booking) DESC,SUM(e.No_show) DESC
```
|room_class |	Total_capacity|	Total_booking|	Cancelled_booking	|Total_No_show
|----------|-------------------|-------------------|------------------|-----------------|
|Elite|	86k|	50k|	12k|	2k
|Standard|	66k|	38k|	10k	|2k
|Premium|	53k|	31k|	8k|	2k
|Presidential|	27k|	16k	|4k|	1k

* Week_no :

```SQL

SELECT e.Week_no,
      CONCAT(ROUND(SUM(e.capacity) / 1000.0, 0), 'k') AS Total_capacity,
    CONCAT(CAST(ROUND(SUM(e.count_c) / 1000.0, 0) AS INT), 'k') AS Total_booking,
    CONCAT(CAST(ROUND(SUM(e.Cancelled_booking) / 1000.0, 0) AS INT), 'k') AS Cancelled_booking,
    CONCAT(CAST(ROUND(SUM(e.No_show) / 1000.0, 0) AS INT), 'k') AS Total_No_show
FROM (
    SELECT A.Week_no, A.capacity, NULL as count_c,NULL AS Cancelled_booking, null as No_show
    FROM (
        SELECT  B.Week_no, SUM(A.capacity) as capacity
        FROM aggregated_bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
        GROUP BY   B.Week_no) A
    UNION
    SELECT B.Week_no, NULL as capacity, B.count_c,null as Cancelled_booking, null as No_show
    FROM (
        SELECT   B.Week_no,COUNT(A.booking_id) as count_c
        FROM bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
        GROUP BY   B.Week_no) B
    UNION
	SELECT  c.Week_no, NULL as capacity, null as Total_booking, c.TOTAL_CANCELLED_BOOKING AS Cancelled_booking, null as No_show
    FROM (
        SELECT    B.Week_no, COUNT(*) AS TOTAL_CANCELLED_BOOKING
        FROM bookings_Table A
        JOIN Date_Table B ON A.check_in_date = B.Date
		WHERE booking_status = 'CANCELLED'
        GROUP BY   B.Week_no
		) c
			UNION
    SELECT d.Week_no, NULL AS capacity, NULL AS Total_booking, null AS Cancelled_booking, d.TOTAL_NOSHOW as No_show
    FROM (
        SELECT   B.Week_no, COUNT(*) AS TOTAL_NOSHOW
        FROM bookings_Table A
       JOIN Date_Table B ON A.check_in_date = B.Date
        WHERE booking_status ='No Show'
        GROUP BY   B.Week_no) D
) e
GROUP BY e.Week_no
ORDER BY SUM(e.capacity) DESC, SUM(e.count_c) DESC, SUM(e.Cancelled_booking) DESC,SUM(e.No_show) DESC

```

|Week_no	|Total_capacity	|Total_booking	|Cancelled_booking	|Total_No_show
|----------|-------------------|-------------------|------------------|-----------------|
|24	|18k|	11k|	3k|	1k
|29	|18k|	11k|	3k|	1k
|19	|18k|	11k|	3k|	1k
|27	|18k|	11k|	3k|	1k
|20	|18k|	11k|	3k|	1k
|25	|18k|	11k|	3k|	1k
|22	|18k|	11k|	3k|	1k
|28	|18k|	11k|	3k|	1k
|23	|18k|	9k|	2k|	0k
|21	|18k|	9k|	2k|	0k
|31	|18k|	9k|	2k|	0k
|30	|18k|	9k|	2k|	0k
|26	|18k|	9k|	2k|	0k
|32	|3k|	2k|	0k|	0k

* PLATFORM :

```SQL

SELECT D.booking_platform,
    CONCAT(CAST(ROUND(SUM(D.count_c) / 1000.0, 0) AS INT), 'k') as Total_booking,
	CONCAT(CAST(round(SUM(D.Cancelled_booking)/ 1000.0, 0)AS INT), 'k') as Cancelled_booking,
	 CONCAT(CAST(ROUND(SUM(d.No_show) / 1000.0, 0) AS INT), 'k') AS Total_No_show
FROM (
    SELECT a.booking_platform, a.count_c,null as Cancelled_booking, null as No_show
    FROM (
        SELECT   booking_platform,COUNT(booking_id) as count_c
        FROM bookings_Table 
        GROUP BY   booking_platform) a
    UNION
	SELECT b.booking_platform,  null as Total_booking, b.TOTAL_CANCELLED_BOOKING AS Cancelled_booking, null as No_show
    FROM (
        SELECT    booking_platform, COUNT(*) AS TOTAL_CANCELLED_BOOKING
        FROM bookings_Table
		WHERE booking_status = 'CANCELLED'
        GROUP BY  booking_platform
		) b
				UNION
    SELECT c.booking_platform,  NULL AS Total_booking, null AS Cancelled_booking, c.TOTAL_NOSHOW as No_show
    FROM (
        SELECT   booking_platform, COUNT(*) AS TOTAL_NOSHOW
        FROM bookings_Table A
        WHERE booking_status ='No Show'
        GROUP BY   booking_platform) c
) d
GROUP BY D.booking_platform
ORDER BY SUM(D.count_c) DESC, SUM(D.Cancelled_booking) DESC,SUM(D.No_show) DESC
```
|booking_platform	|Total_booking	|Cancelled_booking|	Total_No_show|
|----------|-------------------|-------------------|------------------|
|others	        |55k	|14k|	3k
|makeyourtrip	|27k|	7k|	1k
|logtrip	|15k|	4k|	1k
|direct online	|13k|	3k|	1k
|tripster	|10k|	2k|	0k
|journey	|8k|	2k|	0k
|direct offline	|7k|	2k|	0k

* PROPERTY_NAME :

```SQL
SELECT e.property_name,
   CONCAT(ROUND(SUM(e.capacity) / 1000.0, 0), 'k') AS Total_capacity,
    CONCAT(CAST(ROUND(SUM(e.count_c) / 1000.0, 0) AS INT), 'k') AS Total_booking,
    CONCAT(CAST(ROUND(SUM(e.Cancelled_booking) / 1000.0, 0) AS INT), 'k') AS Cancelled_booking,
    CONCAT(CAST(ROUND(SUM(e.No_show) / 1000.0, 0) AS INT), 'k') AS Total_No_show
FROM (
    SELECT A.property_name, A.capacity, NULL as count_c,NULL AS Cancelled_booking, null as No_show
    FROM (
        SELECT  h.property_name, SUM(A.capacity) as capacity
        FROM aggregated_bookings_Table A
        JOIN hotels h ON a.property_id = h.property_id
        GROUP BY    h.property_name) A
    UNION
    SELECT B.property_name, NULL as capacity, B.count_c,null as Cancelled_booking, null as No_show
    FROM (
        SELECT   h.property_name,COUNT(A.booking_id) as count_c
        FROM bookings_Table A
        JOIN hotels h ON a.property_id = h.property_id
        GROUP BY  h.property_name) B
    UNION
	SELECT  c.property_name, NULL as capacity, null as Total_booking, c.TOTAL_CANCELLED_BOOKING AS Cancelled_booking, null as No_show
    FROM (
        SELECT    h.property_name, COUNT(*) AS TOTAL_CANCELLED_BOOKING
        FROM bookings_Table A
        JOIN hotels h ON a.property_id = h.property_id
		WHERE booking_status = 'CANCELLED'
        GROUP BY   h.property_name
		) c
		UNION
    SELECT d.property_name, NULL AS capacity, NULL AS Total_booking, null AS Cancelled_booking, d.TOTAL_NOSHOW as No_show
    FROM (
        SELECT   h.property_name, COUNT(*) AS TOTAL_NOSHOW
        FROM bookings_Table A
       JOIN hotels h ON a.property_id = h.property_id
        WHERE booking_status ='No Show'
        GROUP BY   h.property_name) D
) e
GROUP BY e.property_name
ORDER BY SUM(e.capacity) DESC, SUM(e.count_c) DESC, SUM(e.Cancelled_booking) DESC,SUM(e.No_show) DESC
```

|property_name|	Total_capacity	|Total_booking|Cancelled_booking|	Total_No_show|
|----------|-------------------|-------------------|------------------|-----------------|
|Atliq Exotica|	41k|	23k|	6k|	1k
|Atliq Palace|	39k|	24k|	6k|	1k
|Atliq City|	39k|	23k|	6k|	1k
|Atliq Bay|	37k|	21k|	5k|	1k
|Atliq Blu|	35k|	22k|	5k|	1k
|Atliq Grands|	32k|	17k|	4k|	1k
|Atliq Seasons|	9k|	4k|	1k|	0k

* CATEGORY :

```SQL

SELECT e.category,
     CONCAT(ROUND(SUM(e.capacity) / 1000.0, 0), 'k') AS Total_capacity,
    CONCAT(CAST(ROUND(SUM(e.count_c) / 1000.0, 0) AS INT), 'k') AS Total_booking,
    CONCAT(CAST(ROUND(SUM(e.Cancelled_booking) / 1000.0, 0) AS INT), 'k') AS Cancelled_booking,
    CONCAT(CAST(ROUND(SUM(e.No_show) / 1000.0, 0) AS INT), 'k') AS Total_No_show
FROM (
    SELECT A.category, A.capacity, NULL as count_c,NULL AS Cancelled_booking, null as No_show
    FROM (
        SELECT  h.category, SUM(A.capacity) as capacity
        FROM aggregated_bookings_Table A
        JOIN hotels h ON a.property_id = h.property_id
        GROUP BY    h.category) A
    UNION
    SELECT B.category, NULL as capacity, B.count_c,null as Cancelled_booking, null as No_show
    FROM (
        SELECT   h.category,COUNT(A.booking_id) as count_c
        FROM bookings_Table A
        JOIN hotels h ON a.property_id = h.property_id
        GROUP BY  h.category) B
    UNION
	SELECT  c.category, NULL as capacity, null as Total_booking, c.TOTAL_CANCELLED_BOOKING AS Cancelled_booking, null as No_show
    FROM (
        SELECT    h.category, COUNT(*) AS TOTAL_CANCELLED_BOOKING
        FROM bookings_Table A
        JOIN hotels h ON a.property_id = h.property_id
		WHERE booking_status = 'CANCELLED'
        GROUP BY   h.category
		) c
	UNION
    SELECT d.category, NULL AS capacity, NULL AS Total_booking, null AS Cancelled_booking, d.TOTAL_NOSHOW as No_show
    FROM (
        SELECT   h.category, COUNT(*) AS TOTAL_NOSHOW
        FROM bookings_Table A
       JOIN hotels h ON a.property_id = h.property_id
        WHERE booking_status ='No Show'
        GROUP BY   h.category) D
) e
GROUP BY e.category
ORDER BY SUM(e.capacity) DESC, SUM(e.count_c) DESC, SUM(e.Cancelled_booking) DESC,SUM(e.No_show) DESC
```

|category|	Total_capacity|	Total_booking|	Cancelled_booking|	Total_No_show
|-----|------|-----|------|-------|
|Luxury	|145k|	84k|	21k	|4k
|Business|	87k	|51k|	13k	|2k


# 🧑‍🤝‍🧑 Occupancy Percentage
### 🤯 Insights - https://tinyurl.com/muehwkp6

* MONTH :
```sql
SELECT B.Month_year, 
    CONCAT(ROUND(SUM(successful_bookings) / SUM(capacity) * 100, 1), '%') AS Occupancy_percent
FROM aggregated_bookings_Table A
JOIN Date_Table B
ON A.check_in_date = B.Date
GROUP BY B.Month_year
ORDER BY SUM(successful_bookings) / SUM(capacity) DESC 
```
#### Answer:
|Month_year|	Occupancy_percent |
|----------|-------------------|
|May 2022	|58.5%|
|Jul 2022	|57.6%|
|Jun 2022	|57.5%|

	
* CITY :
```sql

SELECT h.city,
       CONCAT(ROUND(SUM(successful_bookings) / SUM(capacity) * 100, 1), '%') AS Occupancy_percent
FROM aggregated_bookings_Table A
JOIN hotels h ON a.property_id = h.property_id
GROUP BY h.city
ORDER BY SUM(successful_bookings) / SUM(capacity) DESC 

```
|city	|Occupancy_percent|
|--------|-----------|
|Delhi	|60.5%|
|Hyderabad|	58.1%|
|Mumbai	|57.9%|
|Bangalore|	55.8%|

* Day_type :
```sql
SELECT 
      b.Day_type,
       CONCAT(ROUND(SUM(successful_bookings) / SUM(capacity) * 100, 1), '%') AS Occupancy_percent
FROM aggregated_bookings_Table A
JOIN Date_Table B ON A.check_in_date = B.Date
GROUP BY  b.Day_type
ORDER BY SUM(successful_bookings) / SUM(capacity) DESC
```

|Day_type|	Occupancy_percent
|-------|--------------|
|Weekend|	73.6%
|Weekday|	51.3%
* ROOM_CLASS :

```SQL
SELECT r.room_class,
       CONCAT(ROUND(SUM(successful_bookings) / SUM(capacity) * 100, 1), '%') AS Occupancy_percent
FROM aggregated_bookings_Table b
JOIN rooms r ON b.room_category = r.room_id
GROUP BY r.room_class
ORDER BY SUM(successful_bookings) / SUM(capacity) DESC

```

|room_class	|Occupancy_percent|
|--------|-----------|
|Presidential|	59.2%
|Standard|	57.9%
|Elite|	57.6%
|Premium|	57.6%

* Week_no :

```SQL

SELECT B.Week_no,
       CONCAT(ROUND(SUM(successful_bookings) / SUM(capacity) * 100, 1), '%') AS Occupancy_percent
FROM aggregated_bookings_Table A
JOIN Date_Table B ON A.check_in_date = B.Date
GROUP BY B.Week_no
having B.Week_no != '32'
ORDER BY SUM(successful_bookings) / SUM(capacity) DESC
```

|Week_no	|Occupancy_percent|
|--------|-----------|
|24	|62.4%|
|29|	62.3%|
|19	|62%|
|27	|61.9%|
|20	|61.9%|
|25	|61.8%|
|22	|61.8%|
|28	|61.8%|
|23	|51.4%|
|21	|51.1%|
|31	|51%|
|30	|51%|
|26|	51%|


* PROPERTY_NAME :


```SQL
SELECT h.property_name,
       CONCAT(ROUND(SUM(successful_bookings) / SUM(capacity) * 100, 1), '%') AS Occupancy_percent
FROM aggregated_bookings_Table A
JOIN hotels h ON a.property_id = h.property_id
GROUP BY h.property_name
ORDER BY SUM(successful_bookings) / SUM(capacity) DESC
```
|property_name|	Occupancy_percent|
|--------|-----------|
|Atliq Blu|	62%|
|Atliq Palace|	60%|
|Atliq City|	59.5%|
|Atliq Bay	|58.4%|
|Atliq Exotica|	57.3%|
|Atliq Grands|	52.6%|
|Atliq Seasons|	44.6%|

* CATEGORY :

```SQL
SELECT h.category,
       CONCAT(ROUND(SUM(successful_bookings) / SUM(capacity) * 100, 1), '%') AS Occupancy_percent
FROM aggregated_bookings_Table A
JOIN hotels h ON a.property_id = h.property_id
GROUP BY h.category
ORDER BY SUM(successful_bookings) / SUM(capacity) DESC
```

|category	|Occupancy_percent|
|--------|-----------|
|Business|	58.2%|
|Luxury|	57.7%|


# 🔲 RevPAR

### 🤯 Insights - https://tinyurl.com/5etjxw3j 

* MONTH :
```sql
SELECT A.Month_year, ROUND(SUM(revenue) / SUM(capacity_total), 0) AS RevPAR
FROM (
  SELECT check_in_date, SUM(revenue_realized) AS revenue
  FROM bookings_Table
  GROUP BY check_in_date) AS revenue_table,
(SELECT check_in_date, SUM(capacity) AS capacity_total
  FROM aggregated_bookings_Table
  GROUP BY check_in_date) AS capacity_table,
Date_Table A
WHERE A.Date = revenue_table.check_in_date
  AND A.Date = capacity_table.check_in_date
GROUP BY A.Month_year
ORDER BY RevPAR DESC
```
#### Answer:
|Month_year|	RevPAR|
|--------|-----------|
|Jul 2022	|7310|
|Jun 2022	|7304|
|May 2022|	7426|

* CITY :
```sql
SELECT h.city, ROUND(SUM(revenue) / SUM(capacity_total), 0) AS RevPAR
FROM (
  SELECT property_id, SUM(revenue_realized) AS revenue
  FROM bookings_Table
  GROUP BY property_id) AS revenue_table,
(SELECT property_id, SUM(capacity) AS capacity_total
  FROM aggregated_bookings_Table
  GROUP BY property_id) AS capacity_table,
hotels h
WHERE h.property_id = revenue_table.property_id
  AND h.property_id = capacity_table.property_id
GROUP BY h.city
ORDER BY RevPAR DESC
```

|city	|RevPAR|
|--------|-----------|
|Mumbai	|8907|
|Delhi	|7359|
|Bangalore	|7323|
|Hyderabad|	5414|

* Day_type :
```sql
SELECT A.Day_type, ROUND(SUM(revenue) / SUM(capacity_total), 0) AS RevPAR
FROM (
  SELECT check_in_date, SUM(revenue_realized) AS revenue
  FROM bookings_Table
  GROUP BY check_in_date) AS revenue_table,
(SELECT check_in_date, SUM(capacity) AS capacity_total
  FROM aggregated_bookings_Table
  GROUP BY check_in_date) AS capacity_table,
Date_Table A
WHERE A.Date = revenue_table.check_in_date
  AND A.Date = capacity_table.check_in_date
GROUP BY A.Day_type
ORDER BY RevPAR DESC
```

|Day_type|	RevPAR|
|--------|-----------|
|Weekend|	9363|
|Weekday|	6510|

* ROOM_CLASS :

```SQL
SELECT r.room_class, ROUND(SUM(revenue) / SUM(capacity_total), 0) AS RevPAR
FROM (
  SELECT room_category, SUM(revenue_realized) AS revenue
  FROM bookings_Table
  GROUP BY room_category) AS revenue_table,
(SELECT room_category, SUM(capacity) AS capacity_total
  FROM aggregated_bookings_Table
  GROUP BY room_category) AS capacity_table,
rooms r
WHERE r.room_id = revenue_table.room_category
  AND r.room_id = capacity_table.room_category
GROUP BY r.room_class
ORDER BY RevPAR DESC
```

|room_class	|RevPAR|
|--------|-----------|
|Presidential |	13882|
|Premium|	8706|
|Elite	|6520|
|Standard	|4661|


* PROPERTY_NAME :


```SQL
SELECT  h.property_name, ROUND(SUM(revenue) / SUM(capacity_total), 0) AS RevPAR
FROM (
  SELECT property_id, SUM(revenue_realized) AS revenue
  FROM bookings_Table
  GROUP BY property_id) AS revenue_table,
(SELECT property_id, SUM(capacity) AS capacity_total
  FROM aggregated_bookings_Table
  GROUP BY property_id) AS capacity_table,
hotels h
WHERE h.property_id = revenue_table.property_id
  AND h.property_id = capacity_table.property_id
GROUP BY h.property_name
ORDER BY RevPAR DESC
```

|property_name|	RevPAR|
|--------|-----------|
|Atliq Exotica|	7824|
|Atliq Palace	|7723|
|Atliq Blu	|7422|
|Atliq Seasons|	7410|
|Atliq City	|7293|
|Atliq Bay	|7102|
|Atliq Grands	|6532|

* CATEGORY :

```SQL
SELECT  h.category, ROUND(SUM(revenue) / SUM(capacity_total), 0) AS RevPAR
FROM (
  SELECT property_id, SUM(revenue_realized) AS revenue
  FROM bookings_Table
  GROUP BY property_id) AS revenue_table,
(SELECT property_id, SUM(capacity) AS capacity_total
  FROM aggregated_bookings_Table
  GROUP BY property_id) AS capacity_table,
hotels h
WHERE h.property_id = revenue_table.property_id
  AND h.property_id = capacity_table.property_id
GROUP BY h.category
ORDER BY RevPAR DESC
```

|category|	RevPAR|
|------------|-------------|
|Business	|7498|
|Luxury	|7256|


# ⭐ AVERAGE RATINGS

## 🤯 Insights - https://tinyurl.com/y3wj3686

* MONTH :
```sql
SELECT B.Month_year, 
   ROUND(AVG(ratings_given), 2) as AVERAGE_RATINGS 
FROM bookings_Table a
JOIN Date_Table B
ON A.check_in_date = B.Date
GROUP BY B.Month_year
ORDER BY AVG(ratings_given) DESC 
```
#### Answer:
|Month_year|	AVERAGE_RATINGS|
|------------|-------------|
|May 2022	|3.63|
|Jun 2022	|3.62|
|Jul 2022|	3.62|

* CITY :
```sql
SELECT h.city, 
   ROUND(AVG(ratings_given), 2) as AVERAGE_RATINGS 
FROM bookings_Table a
JOIN hotels h ON A.property_id = h.property_id
GROUP BY h.city
ORDER BY AVG(ratings_given) DESC 
```

|city	|AVERAGE_RATINGS|
|------------|-------------|
|Delhi	|3.78|
|Hyderabad|	3.66|
|Mumbai	|3.65|
|Bangalore|	3.41|


* ROOM_CLASS :

```SQL
SELECT r.room_class, 
   ROUND(AVG(ratings_given), 2) as AVERAGE_RATINGS 
FROM bookings_Table a
JOIN rooms r ON A.room_category = r.room_id
GROUP BY  r.room_class
ORDER BY AVG(ratings_given) DESC 
```
|room_class|	AVERAGE_RATINGS|
|------------|-------------|
|Presidential|	3.69|
|Standard	|3.63|
|Elite|	3.6|
|Premium	|3.59|

* Week_no :

```SQL
SELECT B.Week_no, 
   ROUND(AVG(ratings_given), 2) as AVERAGE_RATINGS 
FROM bookings_Table a
JOIN Date_Table B ON A.check_in_date = B.Date
GROUP BY B.Week_no
ORDER BY AVG(ratings_given) DESC 
```

|Week_no|	AVERAGE_RATINGS|
|------------|-------------|
|19	|3.65|
|23	|3.65|
|31	|3.64|
|27	|3.63|
|25|	3.63|
|21|	3.62|
|20|	3.62|
|28|	3.62|
|32|	3.62|
|29|	3.61|
|26|	3.6|
|24|	3.6|
|22|	3.59|
|30	|3.59|

* PLATFORM :
 

```SQL
SELECT booking_platform, 
   ROUND(AVG(ratings_given), 2) as AVERAGE_RATINGS 
FROM bookings_Table 
GROUP BY booking_platform
ORDER BY AVG(ratings_given) DESC
```

|booking_platform|	AVERAGE_RATINGS|
|---------|----------|
|journey	|3.63|
|logtrip	|3.62|
|direct offline|	3.62|
|tripster|	3.62|
|others	|3.62|
|makeyourtrip|	3.62|
|direct online|	3.61|

* PROPERTY_NAME :


```SQL
SELECT h.property_name, 
   ROUND(AVG(ratings_given), 2) as AVERAGE_RATINGS 
FROM bookings_Table a
JOIN hotels h ON A.property_id = h.property_id
GROUP BY h.property_name
ORDER BY AVG(ratings_given) DESC 
```

|property_name	|AVERAGE_RATINGS|
|---------|----------|
|Atliq Blu|	3.96|
|Atliq Palace|	3.75|
|Atliq Bay	|3.71|
|Atliq City|	3.69|
|Atliq Exotica|	3.62|
|Atliq Grands	|3.1|
|Atliq Seasons|	2.29|

* CATEGORY :

```SQL
SELECT h.category, 
   ROUND(AVG(ratings_given), 2) as AVERAGE_RATINGS 
FROM bookings_Table a
JOIN hotels h ON A.property_id = h.property_id
GROUP BY h.category
ORDER BY AVG(ratings_given) DESC 
```

|category	|AVERAGE_RATINGS|
|---------|----------|
|Luxury	|3.62|
|Business|	3.61|

# ❎ Cancellation Percentage
### 🤯 Insights - https://tinyurl.com/5n74h8mu

* MONTH :
```sql
  SELECT
  total_bookings.month,
  concat( ROUND((CAST(cancelled_bookings.TOTAL_CANCELLED_BOOKING AS FLOAT) / total_bookings.Total_Bookings) * 100, 2), '%' ) AS Cancellation_Percentage
FROM
  (SELECT
    date_table.Month_year AS month,
    COUNT(*) AS TOTAL_CANCELLED_BOOKING
    FROM
    bookings_Table
  JOIN
    date_table ON date_table.date = bookings_Table.check_in_date
  WHERE
    booking_status = 'CANCELLED'
  GROUP BY
  date_table.Month_year
  ) AS cancelled_bookings
JOIN
  (SELECT
   date_table.Month_year AS month,
    COUNT(booking_id) AS Total_Bookings
  FROM
    bookings_Table
  JOIN
    Date_Table ON date_table.date = bookings_Table.check_in_date
  GROUP BY
     date_table.Month_year
  ) AS total_bookings ON cancelled_bookings.month = total_bookings.month
```
#### Answer:
|month	|Cancellation_Percentage
|------|---------|
|Jul 2022|	24.46%
|Jun 2022|	25.09%
|May 2022|	24.95%

* CITY :
```sql
  SELECT
  total_bookings.city,
  concat( ROUND((CAST(cancelled_bookings.TOTAL_CANCELLED_BOOKING AS FLOAT) / total_bookings.Total_Bookings) * 100, 2), '%' ) AS Cancellation_Percentage
FROM
  (SELECT
   h.city AS city,
    COUNT(*) AS TOTAL_CANCELLED_BOOKING
    FROM
    bookings_Table b
JOIN hotels h ON b.property_id = h.property_id
  WHERE
    booking_status = 'CANCELLED'
  GROUP BY
   h.city 
  ) AS cancelled_bookings
JOIN
  (SELECT
   h.city AS city,
    COUNT(booking_id) AS Total_Bookings
  FROM
    bookings_Table b
JOIN hotels h ON b.property_id = h.property_id
  GROUP BY
     h.city
  ) AS total_bookings ON cancelled_bookings.city = total_bookings.city

```

|city|	Cancellation_Percentage
|-----|-------------|
|Bangalore|	24.99%
|Delhi	|25.06%
|Hyderabad|	24.63%
|Mumbai	|24.75%

* Day_type :
```sql
  SELECT
  total_bookings.day_type,
  concat( ROUND((CAST(cancelled_bookings.TOTAL_CANCELLED_BOOKING AS FLOAT) / total_bookings.Total_Bookings) * 100, 2), '%' ) AS Cancellation_Percentage
FROM
  (SELECT
    d.Day_type AS day_type,
    COUNT(*) AS TOTAL_CANCELLED_BOOKING
    FROM
    bookings_Table b
  JOIN
    date_table d ON d.date = b.check_in_date
  WHERE
    booking_status = 'CANCELLED'
  GROUP BY
  d.Day_type
  ) AS cancelled_bookings
JOIN
  (SELECT
   d.Day_type AS day_type,
    COUNT(booking_id) AS Total_Bookings
  FROM
    bookings_Table b
  JOIN
    Date_Table d ON d.date = b.check_in_date
  GROUP BY
     d.Day_type
  ) AS total_bookings ON cancelled_bookings.day_type = total_bookings.day_type

```

|day_type|	Cancellation_Percentage
|-----|----------|
|Weekday	|25.04%
|Weekend|	24.48%

* ROOM_CLASS :

```SQL
  SELECT
  total_bookings.room_class,
  concat( ROUND((CAST(cancelled_bookings.TOTAL_CANCELLED_BOOKING AS FLOAT) / total_bookings.Total_Bookings) * 100, 2), '%' ) AS Cancellation_Percentage
FROM
  (SELECT
    r.room_class AS room_class,
    COUNT(*) AS TOTAL_CANCELLED_BOOKING
    FROM
    bookings_Table b
  JOIN rooms r ON b.room_category = r.room_id
  WHERE
    booking_status = 'CANCELLED'
  GROUP BY
 r.room_class
  ) AS cancelled_bookings
JOIN
  (SELECT
   r.room_class AS room_class,
    COUNT(booking_id) AS Total_Bookings
  FROM
    bookings_Table b
JOIN rooms r ON b.room_category = r.room_id
  GROUP BY
    r.room_class
  ) AS total_bookings ON cancelled_bookings.room_class = total_bookings.room_class

```
|room_class|	Cancellation_Percentage
|---------|---------|
|Elite	|24.96%
|Premium	|24.88%
|Presidential	|24.44%
|Standard	|24.79%

*  Week_no :

```SQL

 SELECT
  total_bookings.week,
  concat( ROUND((CAST(cancelled_bookings.TOTAL_CANCELLED_BOOKING AS FLOAT) / total_bookings.Total_Bookings) * 100, 2), '%' ) AS Cancellation_Percentage
FROM
  (SELECT
    d.Week_no AS week,
    COUNT(*) AS TOTAL_CANCELLED_BOOKING
    FROM
    bookings_Table b
  JOIN
    date_table d ON d.date = b.check_in_date
  WHERE
    booking_status = 'CANCELLED'
  GROUP BY
  d.Week_no
  ) AS cancelled_bookings
JOIN
  (SELECT
   d.Week_no AS week,
    COUNT(booking_id) AS Total_Bookings
  FROM
    bookings_Table b
  JOIN
    Date_Table d ON d.date = b.check_in_date
  GROUP BY
     d.Week_no
  ) AS total_bookings ON cancelled_bookings.week = total_bookings.week
```
|week|	Cancellation_Percentage
|----------|------------|
|19|	25.34%
|20|	24.74%
|21|	24.62%
|22|	25.35%
|23|	24.45%
|24|	25.33%
|25|	25.11%
|26|	25.5%
|27|	24.55%
|28|	24.18%
|29|	24.8%
|30|	24.5%
|31|	24.31%
|32|	23.99%

* PLATFORM :


```SQL

  SELECT
  total_bookings.platform,
  concat( ROUND((CAST(cancelled_bookings.TOTAL_CANCELLED_BOOKING AS FLOAT) / total_bookings.Total_Bookings) * 100, 2), '%' ) AS Cancellation_Percentage
FROM
  (SELECT
      booking_platform AS platform,
    COUNT(*) AS TOTAL_CANCELLED_BOOKING
    FROM
    bookings_Table b
  WHERE
    booking_status = 'CANCELLED'
  GROUP BY
 booking_platform
  ) AS cancelled_bookings
JOIN
  (SELECT
   booking_platform AS platform,
    COUNT(booking_id) AS Total_Bookings
  FROM
    bookings_Table 
  GROUP BY
   booking_platform
  ) AS total_bookings ON cancelled_bookings.platform = total_bookings.platform
```

|platform	|Cancellation_Percentage
|-------|-----------|
|others	|24.88%
|journey|	24.78%
|direct online|	24.99%
|direct offline	|24.49%
|tripster|	24.99%
|logtrip|	24.3%
|makeyourtrip|	24.99%

* PROPERTY_NAME :


```SQL
SELECT
  total_bookings.property_name,
  concat( ROUND((CAST(cancelled_bookings.TOTAL_CANCELLED_BOOKING AS FLOAT) / total_bookings.Total_Bookings) * 100, 2), '%' ) AS Cancellation_Percentage
FROM
  (SELECT
    H.property_name AS property_name,
    COUNT(*) AS TOTAL_CANCELLED_BOOKING
    FROM
    bookings_Table b
  JOIN hotels h ON b.property_id = h.property_id
  WHERE
    booking_status = 'CANCELLED'
  GROUP BY
  H.property_name
  ) AS cancelled_bookings
JOIN
  (SELECT
   h.property_name AS property_name,
    COUNT(booking_id) AS Total_Bookings
  FROM
    bookings_Table  B
  JOIN hotels h ON b.property_id = h.property_id
  GROUP BY
     H.property_name
  ) AS total_bookings ON cancelled_bookings.property_name = total_bookings.property_name

```

|property_name|	Cancellation_Percentage
|-------|-----------|
|Atliq Bay|	24.84%
|Atliq Blu|	24.65%
|Atliq City|	24.92%
|Atliq Exotica|	24.37%
|Atliq Grands|	25.08%
|Atliq Palace	|25.18%
|Atliq Seasons|	24.79%

* CATEGORY :

```SQL
SELECT
    total_bookings.category,
    CONCAT(ROUND((CAST(cancelled_bookings.TOTAL_CANCELLED_BOOKING AS FLOAT) / total_bookings.Total_Bookings) * 100, 2), '%') AS Cancellation_Percentage
FROM
    (SELECT
        H.category AS category,
        COUNT(*) AS TOTAL_CANCELLED_BOOKING
    FROM
        bookings_Table b
    JOIN hotels h ON b.property_id = h.property_id
    WHERE
        booking_status = 'CANCELLED'
    GROUP BY
        H.category
    ) AS cancelled_bookings
JOIN
    (SELECT
        h.category AS category,
        COUNT(booking_id) AS Total_Bookings
    FROM
        bookings_Table B
    JOIN hotels h ON b.property_id = h.property_id
    GROUP BY
        H.category
    ) AS total_bookings ON cancelled_bookings.category = total_bookings.category;
```

| category|	Cancellation_Percentage
|----------|-------------|
|Business|	25.03%
|Luxury	|24.71% 


# 🅰️ ADR :
### 🤯 Insights - https://tinyurl.com/5kxn7n6x
```sql
SELECT 
     d.Month_year, 
     ROUND(SUM(b.revenue_realized) / COUNT(b.booking_id), 0) AS ADR
FROM bookings_Table b
JOIN Date_Table d ON b.check_in_date = d.Date
GROUP BY d.Month_year
ORDER BY ADR DESC;
```
|Month_year	|ADR
|---------|-------------|
|Jul 2022	|12724
|May 2022	|12683
|Jun 2022	|12681

* CITY
```sql
SELECT 
	h.city, 
	ROUND(SUM(b.revenue_realized) / COUNT(b.booking_id), 0) AS ADR
FROM bookings_Table b
JOIN hotels h ON b.property_id = h.property_id
GROUP BY h.city
ORDER BY ADR DESC;
```
|city	|ADR
|----|------|
|Mumbai	|15387
|Bangalore|	13131
|Delhi	|12154
|Hyderabad	|9322

* DAYTYPE
```sql
SELECT 
	b.Day_type, 
	ROUND(SUM(A.revenue_realized) / COUNT(A.booking_id), 0) AS ADR
FROM bookings_Table A
JOIN Date_Table B ON A.check_in_date = B.Date
GROUP BY b.Day_type
ORDER BY ADR DESC;
```

| Day_type|	ADR
|-------|------|
|Weekend|	12724
|Weekday	|12679

* Room_class
```sql
SELECT 
	r.room_class, 
	ROUND(SUM(b.revenue_realized) / COUNT(b.booking_id), 0) AS ADR
FROM bookings_Table b
JOIN rooms r ON b.room_category = r.room_id
GROUP BY r.room_class
ORDER BY ADR DESC;
```
|room_class|	ADR
|-------|-------|
|Presidential|	23440
|Premium|	15120
|Elite	|11317
|Standard|	8052

* WEEK_NO
```sql
SELECT 
	B.Week_no, 
	ROUND(SUM(A.revenue_realized) / COUNT(A.booking_id), 0) AS ADR
FROM bookings_Table A
JOIN Date_Table B ON A.check_in_date = B.Date
GROUP BY B.Week_no
ORDER BY ADR DESC;
```
|Week_no|	ADR
|-----|------|
|28|	12754
|31|	12753
|27|	12731
|30|	12729
|32|	12726
|20|	12725
|23|	12715
|21|	12710
|22|	12687
|29|	12682
|25|	12672
|26|	12660
|24|	12642
|19|	12602

* Booking_platform
```sql
SELECT 
	booking_platform, 
	ROUND(SUM(revenue_realized) / COUNT(booking_id), 0) AS ADR
FROM bookings_Table
GROUP BY booking_platform
ORDER BY ADR DESC;

```
|booking_platform|	ADR
|------|-------|
|direct offline|	12791
|tripster	|12780
|logtrip	|12710
|others|12700
|makeyourtrip	|12671
|journey	|12649
|direct online|	12634

* Property_name
```sql
SELECT 
	h.property_name, 
	ROUND(SUM(b.revenue_realized) / COUNT(b.booking_id), 0) AS ADR
FROM bookings_Table b
JOIN hotels h ON b.property_id = h.property_id
GROUP BY h.property_name
ORDER BY ADR DESC;

```
|property_name|	ADR
|------|------|
|Atliq Seasons|	16606
|Atliq Exotica|	13665
|Atliq Palace|	12871
|Atliq Grands|	12418
|Atliq City|	12255
|Atliq Bay|	12158
|Atliq Blu|	11969

* Category
```sql
SELECT 
        h.category, 
	ROUND(SUM(b.revenue_realized) / COUNT(b.booking_id), 0) AS ADR
FROM bookings_Table b
JOIN hotels h ON b.property_id = h.property_id
GROUP BY h.category
ORDER BY ADR DESC;

```
|category|	ADR
|-----------|------|
|Business |	12881
|Luxury   |	12584

# 💠 Realisation_Percentage
### 🤯 Insights - https://tinyurl.com/ytpvkh94
* MONTH 
```sql
WITH Cancellation_Query AS (
  SELECT
    total_bookings.Month_year,
    ROUND((CAST(TOTAL_CANCELLED_BOOKING AS FLOAT) / Total_Bookings) * 100, 2) AS Cancellation_Percentage
  FROM
    (
      SELECT
        D.Month_year,
        COUNT(*) AS TOTAL_CANCELLED_BOOKING
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      WHERE
        booking_status = 'CANCELLED'
      GROUP BY
        D.Month_year
    ) AS cancelled_bookings,
    (
      SELECT
        D.Month_year,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      GROUP BY
        D.Month_year
    ) AS total_bookings
  WHERE
    cancelled_bookings.Month_year = total_bookings.Month_year
),
NoShow_Query AS (
  SELECT
    total_bookings.Month_year,
    ROUND((CAST(no_show_bookings AS FLOAT) / Total_Bookings) * 100, 2) AS NoShow_Percentage
  FROM
    (
      SELECT
        D.Month_year,
        COUNT(*) AS no_show_bookings
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      WHERE
        booking_status = 'NO SHOW'
      GROUP BY
        D.Month_year
    ) AS no_show_bookings,
    (
      SELECT
        D.Month_year,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      GROUP BY
        D.Month_year
    ) AS total_bookings
  WHERE
    no_show_bookings.Month_year = total_bookings.Month_year
)
SELECT
  Cancellation_Query.Month_year,
  CONCAT(ROUND((1 - (Cancellation_Percentage / 100 + NoShow_Percentage / 100)) * 100, 2), '%') AS Realisation_Percentage
FROM
  Cancellation_Query,
  NoShow_Query
WHERE
  Cancellation_Query.Month_year = NoShow_Query.Month_year;

```
|Month_year	|Realisation_Percentage
|------|--------|
|Jul 2022|	70.57%
|Jun 2022	|70.05%
|May 2022	|69.82%


* CITY 
```sql
 WITH Cancellation_Query AS (
  SELECT
    total_bookings.city,
    ROUND((CAST(TOTAL_CANCELLED_BOOKING AS FLOAT) / Total_Bookings) * 100, 2) AS Cancellation_Percentage
  FROM
    (
      SELECT
        H.city,
        COUNT(*) AS TOTAL_CANCELLED_BOOKING
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      WHERE
        booking_status = 'CANCELLED'
      GROUP BY
        H.city
    ) AS cancelled_bookings,
    (
      SELECT
        H.city,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      GROUP BY
        H.city
    ) AS total_bookings
  WHERE
    cancelled_bookings.city = total_bookings.city
),
NoShow_Query AS (
  SELECT
    total_bookings.city,
    ROUND((CAST(no_show_bookings AS FLOAT) / Total_Bookings) * 100, 2) AS NoShow_Percentage
  FROM
    (
      SELECT
        H.city,
        COUNT(*) AS no_show_bookings
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      WHERE
        booking_status = 'NO SHOW'
      GROUP BY
        H.city
    ) AS no_show_bookings,
    (
      SELECT
        H.city,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      GROUP BY
        H.city
    ) AS total_bookings
  WHERE
    no_show_bookings.city = total_bookings.city
)
SELECT
  Cancellation_Query.city,
  CONCAT(ROUND((1 - (Cancellation_Percentage / 100 + NoShow_Percentage / 100)) * 100, 2), '%') AS Realisation_Percentage
FROM
  Cancellation_Query,
  NoShow_Query
WHERE
  Cancellation_Query.city = NoShow_Query.city;
```
|City|	Realisation_Percentage
|------|-------|
|Bangalore|	69.92%
|Delhi|	70.05%
|Hyderabad|	70.32%
|Mumbai	|70.22%

* DAYTYPE 
```sql
WITH Cancellation_Query AS (
  SELECT
    total_bookings.Day_type,
    ROUND((CAST(TOTAL_CANCELLED_BOOKING AS FLOAT) / Total_Bookings) * 100, 2) AS Cancellation_Percentage
  FROM
    (
      SELECT
        D.Day_type,
        COUNT(*) AS TOTAL_CANCELLED_BOOKING
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      WHERE
        booking_status = 'CANCELLED'
      GROUP BY
        D.Day_type
    ) AS cancelled_bookings
    JOIN (
      SELECT
        D.Day_type,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      GROUP BY
        D.Day_type
    ) AS total_bookings ON cancelled_bookings.Day_type = total_bookings.Day_type
),
NoShow_Query AS (
  SELECT
    total_bookings.Day_type,
    ROUND((CAST(no_show_bookings AS FLOAT) / Total_Bookings) * 100, 2) AS NoShow_Percentage
  FROM
    (
      SELECT
        D.Day_type,
        COUNT(*) AS no_show_bookings
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      WHERE
        booking_status = 'NO SHOW'
      GROUP BY
        D.Day_type
    ) AS no_show_bookings
    JOIN (
      SELECT
        D.Day_type,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      GROUP BY
        D.Day_type
    ) AS total_bookings ON no_show_bookings.Day_type = total_bookings.Day_type
)
SELECT
  Cancellation_Query.Day_type,
  CONCAT(ROUND((1 - (Cancellation_Percentage / 100 + NoShow_Percentage / 100)) * 100, 2), '%') AS Realisation_Percentage
FROM
  Cancellation_Query
  JOIN NoShow_Query ON Cancellation_Query.Day_type = NoShow_Query.Day_type;
```
|Day_type	|Realisation_Percentage
|--------|------------|
|Weekday	|69.96%
|Weekend	|70.47%


* ROOM_CLASS 
```sql
WITH Cancellation_Query AS (
  SELECT
    total_bookings.room_class,
    ROUND((CAST(TOTAL_CANCELLED_BOOKING AS FLOAT) / Total_Bookings) * 100, 2) AS Cancellation_Percentage
  FROM
    (
      SELECT
        r.room_class,
        COUNT(*) AS TOTAL_CANCELLED_BOOKING
      FROM
        bookings_Table B
        JOIN rooms r ON B.room_category = r.room_id
      WHERE
        booking_status = 'CANCELLED'
      GROUP BY
        r.room_class
    ) AS cancelled_bookings
    JOIN (
      SELECT
        r.room_class,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN rooms r ON B.room_category = r.room_id
      GROUP BY
        r.room_class
    ) AS total_bookings ON cancelled_bookings.room_class = total_bookings.room_class
),
NoShow_Query AS (
  SELECT
    total_bookings.room_class,
    ROUND((CAST(no_show_bookings AS FLOAT) / Total_Bookings) * 100, 2) AS NoShow_Percentage
  FROM
    (
      SELECT
        r.room_class,
        COUNT(*) AS no_show_bookings
      FROM
        bookings_Table B
        JOIN rooms r ON B.room_category = r.room_id
      WHERE
        booking_status = 'NO SHOW'
      GROUP BY
        r.room_class
    ) AS no_show_bookings
    JOIN (
      SELECT
        r.room_class,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN rooms r ON B.room_category = r.room_id
      GROUP BY
        r.room_class
    ) AS total_bookings ON no_show_bookings.room_class = total_bookings.room_class
)
SELECT
  Cancellation_Query.room_class,
  CONCAT(ROUND((1 - (Cancellation_Percentage / 100 + NoShow_Percentage / 100)) * 100, 2), '%') AS Realisation_Percentage
FROM
  Cancellation_Query
  JOIN NoShow_Query ON Cancellation_Query.room_class = NoShow_Query.room_class;
```
|room_class|	Realisation_Percentage
|-------|--------|
|Elite	|70%
|Premium	|70.17%
|Presidential|	70.58%
|Standard|	70.14%


* Week_no
```sql
WITH Cancellation_Query AS (
  SELECT
    total_bookings.Week_no,
    ROUND((CAST(TOTAL_CANCELLED_BOOKING AS FLOAT) / Total_Bookings) * 100, 2) AS Cancellation_Percentage
  FROM
    (
      SELECT
        D.Week_no,
        COUNT(*) AS TOTAL_CANCELLED_BOOKING
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      WHERE
        booking_status = 'CANCELLED'
      GROUP BY
        D.Week_no
    ) AS cancelled_bookings
    JOIN (
      SELECT
        D.Week_no,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      GROUP BY
        D.Week_no
    ) AS total_bookings ON cancelled_bookings.Week_no = total_bookings.Week_no
),
NoShow_Query AS (
  SELECT
    total_bookings.Week_no,
    ROUND((CAST(no_show_bookings AS FLOAT) / Total_Bookings) * 100, 2) AS NoShow_Percentage
  FROM
    (
      SELECT
        D.Week_no,
        COUNT(*) AS no_show_bookings
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      WHERE
        booking_status = 'NO SHOW'
      GROUP BY
        D.Week_no
    ) AS no_show_bookings
    JOIN (
      SELECT
        D.Week_no,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN Date_Table D ON B.check_in_date = D.Date
      GROUP BY
        D.Week_no
    ) AS total_bookings ON no_show_bookings.Week_no = total_bookings.Week_no
)
SELECT
  Cancellation_Query.Week_no,
  CONCAT(ROUND((1 - (Cancellation_Percentage / 100 + NoShow_Percentage / 100)) * 100, 2), '%') AS Realisation_Percentage
FROM
  Cancellation_Query,
  NoShow_Query
WHERE
  Cancellation_Query.Week_no = NoShow_Query.Week_no;
```
|Week_no	|Realisation_Percentage
|-------|----------|
|19	|69.57%
|20	|70.26%
|21	|70.02%
|22	|69.37%
|23	|70.4%
|24	|69.63%
|25	|69.97%
|26	|69.78%
|27	|70.55%
|28	|70.98%
|29	|70.59%
|30	|70.38%
|31	|70.36%
|32	|70.8%


* Platform 

```sql
WITH Cancellation_Query AS (
  SELECT
    total_bookings.booking_platform,
    ROUND((CAST(TOTAL_CANCELLED_BOOKING AS FLOAT) / Total_Bookings) * 100, 2) AS Cancellation_Percentage
  FROM
    (
      SELECT
        booking_platform,
        COUNT(*) AS TOTAL_CANCELLED_BOOKING
      FROM
        bookings_Table B
      WHERE
        booking_status = 'CANCELLED'
      GROUP BY
        booking_platform
    ) AS cancelled_bookings
    JOIN (
      SELECT
        booking_platform,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table
      GROUP BY
        booking_platform
    ) AS total_bookings ON cancelled_bookings.booking_platform = total_bookings.booking_platform
),
NoShow_Query AS (
  SELECT
    total_bookings.booking_platform,
    ROUND((CAST(no_show_bookings AS FLOAT) / Total_Bookings) * 100, 2) AS NoShow_Percentage
  FROM
    (
      SELECT
        booking_platform,
        COUNT(*) AS no_show_bookings
      FROM
        bookings_Table B
      WHERE
        booking_status = 'NO SHOW'
      GROUP BY
        booking_platform
    ) AS no_show_bookings
    JOIN (
      SELECT
        booking_platform,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table
      GROUP BY
        booking_platform
    ) AS total_bookings ON no_show_bookings.booking_platform = total_bookings.booking_platform
)
SELECT
  Cancellation_Query.booking_platform,
  CONCAT(ROUND((1 - (Cancellation_Percentage / 100 + NoShow_Percentage / 100)) * 100, 2), '%') AS Realisation_Percentage
FROM
  Cancellation_Query
  JOIN NoShow_Query ON Cancellation_Query.booking_platform = NoShow_Query.booking_platform;
  ```
|booking_platform	|Realisation_Percentage
|----------|-----|
|others	|70.07%
|journey	|70.52%
|direct online	|70.27%
|direct offline	|70.2%
|tripster	|69.84%
|logtrip	|70.59%
|makeyourtrip|	69.99%

* Proeprty 
```sql
WITH Cancellation_Query AS (
  SELECT
    total_bookings.property_name,
    ROUND((CAST(TOTAL_CANCELLED_BOOKING AS FLOAT) / Total_Bookings) * 100, 2) AS Cancellation_Percentage
  FROM
    (
      SELECT
        H.property_name,
        COUNT(*) AS TOTAL_CANCELLED_BOOKING
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      WHERE
        booking_status = 'CANCELLED'
      GROUP BY
        H.property_name
    ) AS cancelled_bookings
    JOIN (
      SELECT
        H.property_name,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      GROUP BY
        H.property_name
    ) AS total_bookings ON cancelled_bookings.property_name = total_bookings.property_name
),
NoShow_Query AS (
  SELECT
    total_bookings.property_name,
    ROUND((CAST(no_show_bookings AS FLOAT) / Total_Bookings) * 100, 2) AS NoShow_Percentage
  FROM
    (
      SELECT
        H.property_name,
        COUNT(*) AS no_show_bookings
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      WHERE
        booking_status = 'NO SHOW'
      GROUP BY
        H.property_name
    ) AS no_show_bookings
    JOIN (
      SELECT
        H.property_name,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      GROUP BY
        H.property_name
    ) AS total_bookings ON no_show_bookings.property_name = total_bookings.property_name
)
SELECT
  Cancellation_Query.property_name,
  CONCAT(ROUND((1 - (Cancellation_Percentage / 100 + NoShow_Percentage / 100)) * 100, 2), '%') AS Realisation_Percentage
FROM
  Cancellation_Query
  JOIN NoShow_Query ON Cancellation_Query.property_name = NoShow_Query.property_name;
```
|property_name	|Realisation_Percentage
|-----|------|
|Atliq Bay	|69.97%
|Atliq Blu	|70.05%
|Atliq City	|70.16%
|Atliq Exotica	|70.63%
|Atliq Grands	|69.94%
|Atliq Palace	|69.98%
|Atliq Seasons	|70.59%


* Category 
```sql
WITH Cancellation_Query AS (
  SELECT
    total_bookings.category,
    ROUND((CAST(TOTAL_CANCELLED_BOOKING AS FLOAT) / Total_Bookings) * 100, 2) AS Cancellation_Percentage
  FROM
    (
      SELECT
        H.category,
        COUNT(*) AS TOTAL_CANCELLED_BOOKING
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      WHERE
        booking_status = 'CANCELLED'
      GROUP BY
        H.category
    ) AS cancelled_bookings
    JOIN (
      SELECT
        H.category,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      GROUP BY
        H.category
    ) AS total_bookings ON cancelled_bookings.category = total_bookings.category
),
NoShow_Query AS (
  SELECT
    total_bookings.category,
    ROUND((CAST(no_show_bookings AS FLOAT) / Total_Bookings) * 100, 2) AS NoShow_Percentage
  FROM
    (
      SELECT
        H.category,
        COUNT(*) AS no_show_bookings
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      WHERE
        booking_status = 'NO SHOW'
      GROUP BY
        H.category
    ) AS no_show_bookings
    JOIN (
      SELECT
        H.category,
        COUNT(booking_id) AS Total_Bookings
      FROM
        bookings_Table B
        JOIN hotels H ON B.property_id = H.property_id
      GROUP BY
        H.category
    ) AS total_bookings ON no_show_bookings.category = total_bookings.category
)
SELECT
  Cancellation_Query.category,
  CONCAT(ROUND((1 - (Cancellation_Percentage / 100 + NoShow_Percentage / 100)) * 100, 2), '%') AS Realisation_Percentage
FROM
  Cancellation_Query
  JOIN NoShow_Query ON Cancellation_Query.category = NoShow_Query.category;
```
|category|	Realisation_Percentage
|-----|------|
|Business|	70.11%
|Luxury|	70.17%

# ⚪ DURN
### 🤯 Insights - https://tinyurl.com/258kxpfz
* MONTH

```sql
SELECT No_of_days.Month_year, (booking / NO_OF_DAYS) AS DURN
FROM (
    SELECT D.Month_year, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN Date_Table D ON B.check_in_date = D.Date
    WHERE booking_status = 'Checked Out'
    GROUP BY D.Month_year
) AS [Total Bookings],
(
    SELECT Month_year, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table
    GROUP BY Month_year
) AS No_of_days
WHERE [Total Bookings].Month_year = No_of_days.Month_year
```
|Month_year|	DURN
|----|----|
|Jul 2022|	1024
|Jun 2022|	1020
|May 2022|	1033

* CITY

```sql
SELECT No_of_days.city, (booking / NO_OF_DAYS) AS DURN
FROM (
    SELECT H.city, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN hotels H ON b.property_id = H.property_id
    WHERE booking_status = 'Checked Out'
    GROUP BY H.city
) AS [Total Bookings],
(
    SELECT H.city, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    CROSS JOIN hotels H
    GROUP BY H.city
) AS No_of_days
WHERE [Total Bookings].city = No_of_days.city

```
|city	|DURN
|----|-----|
|Bangalore|	243
|Delhi	|184
|Hyderabad|	266
|Mumbai	|331


####  If you want to join two tables in SQL Server without matching columns, you can use a CROSS JOIN. A CROSS JOIN generates the Cartesian product of the two tables, combining each row from the first table with every row from the second table*/



* CATEGORY
```sql
SELECT No_of_days.category, (booking / NO_OF_DAYS) AS DURN
FROM (
    SELECT H.category, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN hotels H ON b.property_id = H.property_id
    WHERE booking_status = 'Checked Out'
    GROUP BY H.category
) AS [Total Bookings],
(
    SELECT H.category, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    CROSS JOIN hotels H
    GROUP BY H.category
) AS No_of_days
WHERE [Total Bookings].category = No_of_days.category
```
|Category	|DURN
|----|----|
|Business	|388
|Luxury	|638

* PROPERTY NAME
 ```sql
SELECT No_of_days.booking_platform, (booking / NO_OF_DAYS) AS DURN
FROM (
    SELECT booking_platform, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN hotels H ON b.property_id = H.property_id
    WHERE booking_status = 'Checked Out'
    GROUP BY booking_platform
) AS [Total Bookings],
(
    SELECT booking_platform, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    JOIN bookings_Table b ON b.check_in_date = D.Date
    GROUP BY booking_platform
) AS No_of_days
WHERE [Total Bookings].booking_platform = No_of_days.booking_platform

```
|booking_platform|	DURN
|----|-----|
|direct offline|	51
|direct online	|102
|journey	|62
|logtrip	|113
|makeyourtrip	|204
|others	|419
|tripster|	73

* Week_no

```sql
SELECT No_of_days.Week_no, (booking / NO_OF_DAYS) AS DURN
FROM (
    SELECT d.Week_no, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN Date_Table d ON b.check_in_date = d.Date
    WHERE booking_status = 'Checked Out'
    GROUP BY d.Week_no
) AS [Total Bookings],
(
    SELECT Week_no, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table
    GROUP BY Week_no
) AS No_of_days
WHERE [Total Bookings].Week_no = No_of_days.Week_no

```
|Week_no	|DURN
|-----|-----|
|19	|1089
|20	|1099
|21	|904
|22	|1083
|23	|914
|24	|1098
|25	|1093
|26	|898
|27	|1104
|28	|1108
|29	|1111
|30	|906
|31	|906
|32	|1169

* Room_class

```sql
SELECT No_of_days.room_class, (booking / NO_OF_DAYS) AS DURN
FROM (
    SELECT r.room_class, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN rooms r ON b.room_category = r.room_id
    WHERE booking_status = 'Checked Out'
    GROUP BY r.room_class
) AS [Total Bookings],
(
    SELECT room_class, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    CROSS JOIN rooms
    GROUP BY room_class
) AS No_of_days
WHERE [Total Bookings].room_class = No_of_days.room_class
```
|room_class|	DURN
|-----|----|
|Elite	|376
|Premium	|233
|Presidential|	123
|Standard	|293

# ◻️ DBRN
### 🤯 Insights - https://tinyurl.com/mryr6v3r

* MONTH
```sql
SELECT No_of_days.Month_year, (booking / NO_OF_DAYS) AS DBRN
FROM (
    SELECT D.Month_year, COUNT(booking_id) AS booking
    FROM bookings_Table b
    JOIN Date_Table D ON B.check_in_date = D.Date
    GROUP BY D.Month_year
) AS [Total Bookings],
(
    SELECT Month_year, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table
    GROUP BY Month_year
) AS No_of_days
WHERE [Total Bookings].Month_year = No_of_days.Month_year
```
|Month_year|	DBRN
|------|------|
|Jul 2022|	1452
|Jun 2022|	1456
|May 2022|	1480

* CITY

```sql
SELECT No_of_days.city, (booking / NO_OF_DAYS) AS DBRN
FROM (
    SELECT H.city, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN hotels H ON b.property_id = H.property_id
    GROUP BY H.city
) AS [Total Bookings],
(
    SELECT H.city, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    CROSS JOIN hotels H
    GROUP BY H.city
) AS No_of_days
WHERE [Total Bookings].city = No_of_days.city
```
|city	|DBRN
|----|----|
|Bangalore|	348
|Delhi	|263
|Hyderabad|	379
|Mumbai|	472

* CATEGORY
```sql
SELECT No_of_days.category, (booking / NO_OF_DAYS) AS DBRN
FROM (
    SELECT H.category, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN hotels H ON b.property_id = H.property_id
    GROUP BY H.category
) AS [Total Bookings],
(
    SELECT H.category, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    CROSS JOIN hotels H
    GROUP BY H.category
) AS No_of_days
WHERE [Total Bookings].category = No_of_days.category

```
|category|	DBRN
|-----|-----|
|Business|	553
|Luxury	|909

* Booking_platform
  
```sql
SELECT No_of_days.booking_platform, (booking / NO_OF_DAYS) AS DBRN
FROM (
    SELECT booking_platform, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN hotels H ON b.property_id = H.property_id
    GROUP BY booking_platform
) AS [Total Bookings],
(
    SELECT booking_platform, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    JOIN bookings_Table b ON b.check_in_date = D.Date
    GROUP BY booking_platform
) AS No_of_days
WHERE [Total Bookings].booking_platform = No_of_days.booking_platform
```
|booking_platform|	DBRN
|---|----|
|direct offline|	73
|direct online|	145
|journey|	88
|logtrip|	160
|makeyourtrip|	292
|others	|598
|tripster|	104

* Week_no
```sql
SELECT No_of_days.Week_no, (booking / NO_OF_DAYS) AS DBRN
FROM (
    SELECT d.Week_no, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN Date_Table d ON b.check_in_date = d.Date
    GROUP BY d.Week_no
) AS [Total Bookings],
(
    SELECT Week_no, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table
    GROUP BY Week_no
) AS No_of_days
WHERE [Total Bookings].Week_no = No_of_days.Week_no
```
|Week_no|	DBRN
|-----|----|
|19|	1566
|20|	1565
|21|	1291
|22|	1562
|23|	1298
|24|	1577
|25|	1563
|26|	1288
|27|	1566
|28|	1561
|29|	1574
|30|	1288
|31|	1288
|32|	1651

* Room_class
```sql
SELECT No_of_days.room_class, (booking / NO_OF_DAYS) AS DBRN
FROM (
    SELECT r.room_class, COUNT(*) AS booking
    FROM bookings_Table b
    JOIN rooms r ON b.room_category = r.room_id
    GROUP BY r.room_class
) AS [Total Bookings],
(
    SELECT room_class, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    CROSS JOIN rooms
    GROUP BY room_class
) AS No_of_days
WHERE [Total Bookings].room_class = No_of_days.room_class

```
|room_class|	DBRN
|-----|-----|
|Elite	|538
|Premium|	332
|Presidential|	174
|Standard|	417

# 🔳 DSRN

### 🤯 Insights - https://tinyurl.com/4u7b2fkv

* CITY

```sql
SELECT No_of_days.city, (booking / NO_OF_DAYS) AS DSRN
FROM (
    SELECT H.city, SUM(b.capacity) AS booking
    FROM aggregated_bookings_Table b
    JOIN hotels H ON b.property_id = H.property_id
    GROUP BY H.city
) AS [Total Bookings],
(
    SELECT H.city, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    CROSS JOIN hotels H
    GROUP BY H.city
) AS No_of_days
WHERE [Total Bookings].city = No_of_days.city
```
|city	|DSRN
|----|----|
|Mumbai	|816
|Hyderabad|	653
|Bangalore|	624
|Delhi	|435

* CATEGORY
```sql
SELECT No_of_days.category, (booking / NO_OF_DAYS) AS DSRN
FROM (
    SELECT H.category, SUM(b.capacity) AS booking
    FROM aggregated_bookings_Table b
    JOIN hotels H ON b.property_id = H.property_id
    GROUP BY H.category
) AS [Total Bookings],
(
    SELECT H.category, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    CROSS JOIN hotels H
    GROUP BY H.category
) AS No_of_days
WHERE [Total Bookings].category = No_of_days.category
```
|category|	DSRN
|----|----|
|Business|	951
|Luxury	|1577


* Room_class

```sql
SELECT No_of_days.room_class, (booking / NO_OF_DAYS) AS DSRN
FROM (
    SELECT r.room_class, SUM(b.capacity) AS booking
    FROM aggregated_bookings_Table b
    JOIN rooms r ON b.room_category = r.room_id
    GROUP BY r.room_class
) AS [Total Bookings],
(
    SELECT room_class, COUNT(DISTINCT(DATE)) AS NO_OF_DAYS
    FROM Date_Table D
    CROSS JOIN rooms
    GROUP BY room_class
) AS No_of_days
WHERE [Total Bookings].room_class = No_of_days.room_class
ORDER BY DSRN DESC
```
|room_class	|DSRN
|----|-----|
|Elite           |934
|Standard	|722
|Premium	|577
|Presidential	|295
