# theatertime

## Input

Content of text file we will input into our application:

```
Movie Title, Release Year, MPAA Rating, Run Time  # header
There's Something About Mary, 1998, R, 2:14  
How to Lose a Guy in 10 Days, 2003, PG-13, 1:56  
Knocked Up, 2007, R, 2:08  
The Wedding Singer, 1998, PG-13, 1:36  
High Fidelity, 2000, R, 1:54  
Sleepless in Seattle, 1993, PG, 1:46  
The Proposal, 2009, PG-13, 1:48
```

## Magic

Naive pseudocode for planning our app:

* Theater Opening Times:  
    **Monday - Thursday 8:00am - 11:00pm**  
    **Friday - Sunday 10:30am - 11:30pm**
* Use Python [time](https://docs.python.org/2/library/time.html), [datetime](https://docs.python.org/2/library/datetime.html#module-datetime) and [calendar](https://docs.python.org/2/library/calendar.html#module-calendar)?
* For each movie in list (each line in text file after the first one which is the header), take the last item (Run_Time), probably using pop() https://docs.python.org/3/tutorial/datastructures.html:
  * If Mon-Thurs:
    * Earliest movie Start_Time is 09:00
    * Latest movie Start_Time is (23:00 minus the Movie_Title Run_Time)
  * Elif Fri-Sun: 
    * Earliest movie Start_Time is 11:30
    * Latest movie Start_Time is (23:30 minus the Movie_Title Run_Time)
* Scheduled times will be movie Run_Time with 35 minute intervals (theater setup time) [rounded to five](https://stackoverflow.com/questions/2272149/round-to-5-or-other-number-in-python):
```
def myround(x, base=5):
    return int(base * round(float(x)/base))
```
* *Surely forgetting many things that need to happen here*
* Print:  
    ```
    Day, mm/dd/yyyy # (cursed U.S. time system)  
    
    Movie - Rating, Run_Time  
      Start_Time - End_Time  
      Start_Time - End_Time  
      Start_Time - End_Time  
      Start_Time - End_Time  
    ```
  
## Ouput

What we want outputted to the terminal when we run `theatertime.py example_client_data_file.txt`:

```
Thursday 12/31/2015  

There's Something About Mary - Rated R, 2:14  
  12:15 - 14:29  
  15:05 - 17:19  
  17:55 - 20:09  
  20:45 - 22:59  

High Fidelity - Rated R, 1:54  
  ...
```
