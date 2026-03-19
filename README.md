# streaming-workshop
streaming workshop for DEZoomcamp

## Seventh Module & Homework in the DE Zoomcamp Series

1. What version of Redpanda are you running?

  docker exec -it streaming-workshop-redpanda-1 rpk version
  rpk version: v25.3.9

2. The time it takes to send the entire dataset and flush: ~ 10 seconds

3. How many trips have trip_distance > 5?
    8506

4. Which PULocationID had the most trups in a single 5-minute window? 74

postgres@localhost:postgres> SELECT PULocationID, num_trips
 FROM trips_per_location
 ORDER BY num_trips DESC
 LIMIT 3;
+--------------+-----------+
| pulocationid | num_trips |
|--------------+-----------|
| 74           | 15        |

5. How many trips were in the longest session? 81

6. Which hour had the highest total tip amount? 2025-10-16


postgres@localhost:postgres> SELECT window_start, total_tip_amount
 FROM tip_amount_per_hour
 ORDER BY total_tip_amount DESC
 LIMIT 1;
+---------------------+-------------------+
| window_start        | total_tip_amount  |
|---------------------+-------------------|
| 2025-10-16 18:00:00 | 524.9599999999998 |
+---------------------+-------------------+