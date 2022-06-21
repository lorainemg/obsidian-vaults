# Falsehoods Programmers Believe About Aircraft Seat Maps
Creado: 2022-06-16 22:50
Tags: #every-programmer-should-know, #falsehoods, #business, #aircrafts
Topic: [[Falsehoods Programmers Believe about Business]]

----
## Falsehoods Programmers Believe About Aircraft Seat Maps

At Duffel, we are working towards making the complex world of selling  flights accessible to anyone. When designing our Seat Map API, we've  investigated hundreds of real seat maps along with multiple existing  seat map display systems. The findings were quite surprising!

In the spirit of the classic [Falsehoods Programmers Believe About Names](https://www.kalzumeus.com/2010/06/17/falsehoods-programmers-believe-about-names/) blog post, here are 12 assumptions seat map display designers often make about seat maps. All of these assumptions are wrong!

Seat map examples are courtesy of [SeatGuru](https://www.seatguru.com/).

- The same aircraft model always has the same seat map.

  Airlines are free to outfit their aircraft as they please.

  **Examples**

  [British Airways A321](https://www.seatguru.com/airlines/British_Airways/British_Airways_Airbus_A321_C.php)

  [American Airlines A321](https://www.seatguru.com/airlines/American_Airlines/American_Airlines_Airbus_A321_V2.php)

- The same aircraft model, operated by the same airline, always has the same seat map.

  Sometimes, even the same airline will outfit the same model of aircraft differently for different purposes.

  **Examples**

  [British Airways A321 Domestic](https://www.seatguru.com/airlines/British_Airways/British_Airways_Airbus_A321_E.php)

  [British Airways A321 European](https://www.seatguru.com/airlines/British_Airways/British_Airways_Airbus_A321_D.php)

- The order of cabins in the aircraft is always: First, Business, Premium Economy, Economy.

  Not necessarily! Airlines will prioritize efficient use of cabin space over keeping the ordering. For example, the [British Airways Boeing 747-400 Layout 1](https://www.seatguru.com/airlines/British_Airways/British_Airways_Boeing_747-400_C.php) has First, World Traveller Plus (Premium Economy), Club World (Business), World Traveller (Economy) from front to back.

- Aircraft seats always face forward.

  Half of Business class seats in the cabin often face backwards. Business  Class and First Class seats can also be positioned at an angle.

  **Example**

  [British Airways Boeing 747-400 Layout 1](https://www.seatguru.com/airlines/British_Airways/British_Airways_Boeing_747-400_C.php)

  ![[Screenshot-2021-11-02-at-17.39.51-1-1.png]]

- Seat rows are numbered with consecutive numbers

  Some airlines skip row numbers, especially row number 13.

  **Example**

  [Ryanair Boeing 737-800](https://www.seatguru.com/airlines/Ryanair/Ryanair_Boeing_737-800.php)

  ![[Screenshot-2021-11-02-at-17.45.59.png]]

- Seats in a row are numbered with consecutive letter

  The "I" letter is often not used to avoid confusing it with the number 1.

  **Example**

  [Virgin Atlantic Boeing 747-400](https://www.seatguru.com/airlines/Virgin_Atlantic_Airways/Virgin_Atlantic_Airways_B747-400_LGW-1.php)

![[Screenshot-2021-11-03-at-11.58.36-1.png]]

- Seat rows always have the same number of seats in a single cabin

  Sometimes, seats are missing, especially near emergency exits or in the tail section.

  **Example**

  [British Airways Airbus A321neo Layout 2](https://www.seatguru.com/airlines/British_Airways/British_Airways_Airbus_A321neo_V5.php)

![[Screenshot-2021-11-02-at-17.21.07.png]]

- The seat in front or behind always has the same letter

  Sometimes, when there are fewer seats in a row, the letters of the aisle and  window seats are preserved, and only middle seats are removed. This is  often the case in Business Class or when there are fewer seats in a tail section.

  Lots of seat map displays make the mistake of aligning  the seats in columns by letter, which leads to misrepresentation of what the row really looks like!

  **Example**

  [American Airlines Boeing 777-200](https://www.seatguru.com/airlines/American_Airlines/American_Airlines_Boeing_777-200ER_E.php)

![[Screenshot-2021-11-02-at-17.55.46.png]]

- Toilets and galleys are always placed before or after blocks of seats

  Sometimes toilets and galleys are placed where seats would normally be. This  often occurs in the tail section which has narrower sides but can still  provide more seats in the middle.

  **Example**

  [American Airlines Boeing 777-200](https://www.seatguru.com/airlines/American_Airlines/American_Airlines_Boeing_777-200ER_E.php)

  ![[Screenshot-2021-11-02-at-18.01.13-1.png]]

- Seats are aligned in rows in a cabin

  In wide-body aircrafts, the seats between the aisles are often "staggered" in respect to the seats near the windows in the same "row" to fill  cabin space more efficiently.

  **Example**

  [American Airlines Boeing 787-8](https://www.seatguru.com/airlines/American_Airlines/American_Airlines_AA_Boeing_787-8_A.php)

  ![[Screenshot-2021-11-02-at-18.04.57.png]]

- Seats are aligned in columns in a cabin

  Sometimes, when a seat is missing in a row, the remaining seats will be shifted by half a seat to keep them centered.

  **Example**

  [American Airlines Airbus A330-200](https://www.seatguru.com/airlines/American_Airlines/American_Airlines_Airbus_A330-200_C.php)

  ![[Screenshot-2021-11-02-at-18.30.23-1.png]]

- Seats are aligned in columns in a cabin or shifted half a seat

  Not even that! In tail sections, rows with missing seats can start out  aligned with the other rows and slowly converge towards being shifted  half a seat across multiple rows.

  **Example**

  [Eurowings Airbus A330-200](https://www.seatguru.com/airlines/Eurowings_Airlines/Eurowings_Airbus_A330-200.php)

  ![[Screenshot-2021-11-02-at-18.43.49-1.png]]
  
## Referencias