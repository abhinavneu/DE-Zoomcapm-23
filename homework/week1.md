# DE Zoomcamp Homework Week 1

### Question 1. Knowing docker tags

Which tag has the following text? - Write the image ID to the file

```text 
Answer : --iidfile string
```

### Question 2. Understanding docker first run

Run docker with the python:3.9 image in an interactive mode and the entrypoint of bash. Now check the python modules that are installed ( use pip list). How many python packages/modules are installed?

```text 
Answer : 3

Package    Version
---------- -------
pip        22.0.4
setuptools 58.1.0
wheel      0.38.4
```

### Question 3. Count records

How many taxi trips were totally made on January 15?

```sql 
Answer : 20689

SELECT COUNT(1) FROM public.green_taxi_data
WHERE CAST(lpep_pickup_datetime as date) = '2019-01-15' 
```

### Question 4. Largest trip for each day

Which was the day with the largest trip distance Use the pick up time for your calculations.

```sql 
Answer : 2019-01-15

SELECT lpep_pickup_datetime FROM public.green_taxi_data
ORDER BY trip_distance DESC
LIMIT 1
```

### Question 5. The number of passengers

In 2019-01-01 how many trips had 2 and 3 passengers?

```sql 
Answer : 2: 1282 ; 3: 254

SELECT passenger_count,COUNT(1) FROM public.green_taxi_data
WHERE CAST(lpep_pickup_datetime as date) = '2019-01-01' AND passenger_count IN (2,3)
GROUP BY 1
```

### Question 6. Largest tip

For the passengers picked up in the Astoria Zone which was the drop off zone that had the largest tip? We want the name of the zone, not the id.

```sql 
Answer : Long Island City/Queens Plaza

SELECT zDO."Zone",gtd.tip_amount
FROM public.green_taxi_data as gtd
JOIN public.taxi_zone_data as zPU
ON gtd."PULocationID" = zPU."LocationID"
JOIN public.taxi_zone_data as zDO
ON gtd."DOLocationID" = zDO."LocationID"
WHERE zPU."Zone" = 'Astoria'
ORDER BY 2 DESC
LIMIT 1
```
