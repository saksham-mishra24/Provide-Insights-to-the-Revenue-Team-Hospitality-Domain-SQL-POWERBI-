# Hey ! Welcome 
## ❕ Let's start some calculation of our given metrics 

## Here is Metric Table : 





| Metric                         | Formula                                                                                | Table |
| -----------                    | -----------                                                                             |-------|
| Revenue                        | SUM(fact_bookings[revenue_realized])	                                                     | fact_bookings |
| Total Bookings	           | COUNT fact_bookings[booking_id])	         | fact_bookings  |
| Total Capacity           |  SUM(fact_aggregated_bookings[capacity])          | 	fact_aggregated_bookings |
| Total Successful Bookings	                 |          SUM(fact_aggregated_bookings[successful_bookings])	 |   fact_aggregated_bookings
Occupancy %	                  |          DIVIDE([Total Successful Bookings],[Total Capacity],0)	   |    fact_aggregated_bookings
Average Rating	               |            AVERAGE(fact_bookings[ratings_given])	 | fact_bookings
No of days	                      |       DATEDIFF(MIN(dim_date[date]),MAX(dim_date[date]),DAY) +1	  |   dim_date
Total cancelled bookings	    |                       CALCULATE([Total Bookings],fact_bookings[booking_status]="Cancelled")	 |   fact_bookings
Cancellation %	             |              DIVIDE([Total cancelled bookings],[Total Bookings])	     |  fact_bookings
Total Checked Out	             |                CALCULATE([Total Bookings],fact_bookings[booking_status]="Checked Out")	    |  fact_bookings
Total no show bookings	     |                      CALCULATE([Total Bookings],fact_bookings[booking_status]="No Show")	  |   fact_bookings
No Show rate %               |            	                           DIVIDE([Total no show bookings],[Total Bookings])    | 	fact_bookings
Booking % by Platform        |                   	DIVIDE([Total Bookings], CALCULATE([Total Bookings], ALL(fact_bookings[booking_platform]))) * 100   | 	fact_bookings
Booking % by Room class	      |                       DIVIDE([Total Bookings], CALCULATE([Total Bookings], ALL(dim_rooms[room_class]))) * 100	  |  fact_bookings, dim_rooms
ADR	                        |   DIVIDE( [Revenue], [Total Bookings],0)	                    |                  fact_bookings
Realisation %                 |            	1 - ([Cancellation %] + [No Show rate %])	     |                            fact_bookings
RevPAR	                    |       DIVIDE([Revenue],[Total Capacity])                  |                  	fact_bookings, fact_agg_bookings
DBRN	                       |     DIVIDE([Total Bookings], [No of days])	           |      fact_bookings, dim_date
DSRN	                     |      DIVIDE([Total Capacity], [No of days])	       |         fact_agg_bookings, dim_date
DURN	                     |      DIVIDE([Total Checked Out],[No of days])	     |          fact_bookings, dim_date







