# Falsehoods Programmers Believe

## Falsehoods programmers believe about prices

1. You can store a price in a floating point variable.
1. All currencies are subdivided in 1/100th units (like US dollar/cents, euro/eurocents etc.).
1. All currencies are subdivided in decimal units (like dinar/fils)
1. All currencies currently in circulation are subdivided in decimal units. (to exclude shillings, pennies) (counter-example: MGA)
1. All currencies are subdivided. (counter-examples: KRW, COP, JPY... Or subdivisions can be deprecated.)
1. Prices can't have more precision than the smaller sub-unit of the currency. (e.g. gas prices)
1. For any currency you can have a price of 1. (ZWL)
1. Every country has its own currency. (EUR is the best example, but also Franc CFA, etc.)
1. No country uses another's country official currency as its official currency. (many countries use USD: Ecuador, Micronesia...)
1. Countries have only one currency.
1. Countries have only one currency currently in circulation. (Panama officially uses both PAB and USD)
1. I'll only deal with currencies currently in circulation anyway.
1. All currencies have an ISO 4217 3-letter code. (The Transnistrian ruble has none, for example)
1. All currencies have a different name. (French franc, "nouveau franc")
1. You always put the currency symbol after the price.
1. You always put the currency symbol before the price.
1. You always put the currency symbol either after, or before the price, never in the middle.
1. There's only one currency symbol for any currency. (元, 角, 分 are increasing units of the Chinese renminbi.)
1. For a given currency, you always, but always, put the symbol in the same place.
1. OK. But if you only use the ISO 4217 currency codes, you always put it before the price. (Hint: it depends on the language.)
1. Before the price means on the left. (ILS)
1. You can always use a dot (or a comma, etc.) as a decimal separator.
1. You can always use a space (or a dot, or a comma, etc.) as a thousands separator.
1. You separate big prices by grouping numbers in triplets (thousands). (One writes `¥1 0000`)
1. Prices at a single company will never range from five digits before the decimal to five digits after.
1. Prices contains only digits and punctuation. (Germans can write `12,- €`)
1. A price can be *at most* 10^N for some value of N.
1. Given two currencies, there is only one exchange rate between them at any given point in time.
1. Given two currencies, there is at least one exchange rate between them at any given point in time. (restriction on export of MAD, ARS, CNY, for example)
1. And the final one: a standalone `$` character is always pronounced dollar. (It's also the peso sign.)

## Falsehoods Programmers Believe About IBANs

In the spirit of [Falsehoods Programmers Believe About Phone Numbers](https://github.com/googlei18n/libphonenumber/blob/master/FALSEHOODS.md), here is a list of mistaken perspectives on International Bank Account Numbers (IBAN)...

1. **IBANs are global.**
   While the IBAN system has been deployed in some states on most continents, it is a long way from achieving universal adoption. Certain states, such as Australia, when their High Value Clearing Payments Association were queried regarding their decision not to adopt IBAN, first refused to respond for upwards of 12 months then finally refused to release any reasoning. There are a lot of established interests that are against reduced barriers to financial systems integration.
2. **IBAN country codes are the same as ISO3166-1 alpha-2 country codes.**
   Quite dangerously this is mostly, but not always the case. Both unofficial codes such as `AA` and various dependent territories which may use the parent jurisdiction's code instead of their own do not equate to the ISO3166-1 alpha-2 country code as expected.
3. **IBAN country codes are the same as IANA country codes.**
   Quite dangerously this is mostly, but not always the case. Take for example `XK`, unofficial codes such as `AA`, or various dependent territories which may use the parent jurisdiction's code instead of their own.
4. **IBAN represents a 'free' and 'neutral' namespace for global financial cooperation.**
   In fact, under the IBAN standard, which is managed by defacto global monopoly SWIFT, which has significant political significance to and affinity for US interests despite being a nominally Belgium-registered international cooperative, the only people who can create endpoints are existing financial institutions within countries holding an ISO3166-1 alpha-2 country code, a list which excludes many legitimate actors, virtually all innovators, plus the various states of the world with limited recognition. For a potentially mutually interoperable system adopted by some actors (eg. Bitcoin exchange Kraken) see the Internet IBAN (IIBAN) proposal at http://ifex-project.org/
5. **Pre-IBAN national checksums are still in operation.**
   There is no way to reliably determine whether or not a given country had a national, pre-IBAN checksum system, whether that system was actually applied to all banks (certain central banks are known exceptions), or whether that system is still in operation after IBAN adoption. The `php-iban` library represents a best-effort approach to gathering this knowledge as appropriate.
6. **IBAN is clearly published standard.**
   There are significant problems with the current dual-format publishing process used by SWIFT, which are documented [over here](https://raw.githubusercontent.com/globalcitizen/php-iban/master/docs/COMEDY-OF-ERRORS).
7. **IBANs are always written the same way.**
   Some countries tend to continue to use methods of spacing/delineation amongst legacy components present within the IBAN. Others tend to concatenate the entire IBAN to a machine-readable single word. Still others use the human-style formatting with four characters per block, `XXXX YYYY ZZZZ 0000`. It is difficult to know how to best present an IBAN to a customer. In general, reasonable practice is that if the user is likely to manually transcribe (eg. via pen and paper) then a human format (four characters per block) is recommended. If the output is likely to be copy-pasted, however, then a single word (machine format) is preferred... in which case care should be taken to exclude neighbouring punctuation.
8. **IBAN solves input errors.**
   IBAN has a strong checksum system built in, however this does not really help you to help the user find the source of an input problem. The `php-iban` library includes a flexible and robust mistranscription error detection system which can assist you in presenting possible errors to the user for manual evaluation.
9. **IBAN should be kept secret.**
   Bank account numbers are public identifiers and are generally not supposed to be secret. Any banking system capable of being exploited purely through the knowledge of an account number (The US check clearance system and early credit card systems were classic cases) should have long since been fixed by the time IBAN came in to being. The security argument in therefore misguided (see also, [security through obscurity](https://en.wikipedia.org/wiki/Security_through_obscurity)). However, for user experience optimization purposes it can be useful to obfuscate portions of an IBAN where it reduces cognitive load for users, such as in identifying one IBAN from a set using only the leading and unique trailing portions.

## Falsehoods about cars that developers believe in

- Car has four wheels. Nope. There is [Reliant Robin](https://en.wikipedia.org/wiki/Reliant_Robin). 

- If car has more than 4 wheels it's a bus or a truck. Nope. There is [Mercedes-Benz G63 AMG 6x6](https://en.wikipedia.org/wiki/Mercedes-Benz_G63_AMG_6x6). 

- Car has one engine. Nope. There is 
- Car has one type of fuel. Nope. There are hybrid cars that have an electric engine in addition to the standard diesel/petrol engine. 
- There is nothing else fuel-related if it's not hybrid. Nope. There is 
- Car consumption is measured in either metric (l/100km) or imperial (mpg) units. Nope. There are electric cars with kW/100km and hydrogen powered cards with kg/100km. 
- Car height is one value. Nope. There are camper vans with elevating roofs and cars with 
- Hatchbacks have 3 or 5 doors. Nope. There is [Hyundai Veloster](https://en.wikipedia.org/wiki/Hyundai_Veloster) which has 4 doors. There is 1 on driver's side, 2 on passenger's side and a rear door.

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

  ![Screenshot-2021-11-02-at-17.39.51-1-1](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\Screenshot-2021-11-02-at-17.39.51-1-1.png)

- Seat rows are numbered with consecutive numbers

  Some airlines skip row numbers, especially row number 13.

  **Example**

  [Ryanair Boeing 737-800](https://www.seatguru.com/airlines/Ryanair/Ryanair_Boeing_737-800.php)

  ![Screenshot-2021-11-02-at-17.45.59](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\Screenshot-2021-11-02-at-17.45.59.png)

- Seats in a row are numbered with consecutive letter

  The "I" letter is often not used to avoid confusing it with the number 1.

  **Example**

  [Virgin Atlantic Boeing 747-400](https://www.seatguru.com/airlines/Virgin_Atlantic_Airways/Virgin_Atlantic_Airways_B747-400_LGW-1.php)

![Screenshot-2021-11-03-at-11.58.36-1](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\Screenshot-2021-11-03-at-11.58.36-1.png)

- Seat rows always have the same number of seats in a single cabin

  Sometimes, seats are missing, especially near emergency exits or in the tail section.

  **Example**

  [British Airways Airbus A321neo Layout 2](https://www.seatguru.com/airlines/British_Airways/British_Airways_Airbus_A321neo_V5.php)

![Screenshot-2021-11-02-at-17.21.07](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\Screenshot-2021-11-02-at-17.21.07.png)

- The seat in front or behind always has the same letter

  Sometimes, when there are fewer seats in a row, the letters of the aisle and  window seats are preserved, and only middle seats are removed. This is  often the case in Business Class or when there are fewer seats in a tail section.

  Lots of seat map displays make the mistake of aligning  the seats in columns by letter, which leads to misrepresentation of what the row really looks like!

  **Example**

  [American Airlines Boeing 777-200](https://www.seatguru.com/airlines/American_Airlines/American_Airlines_Boeing_777-200ER_E.php)

![Screenshot-2021-11-02-at-17.55.46](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\Screenshot-2021-11-02-at-17.55.46.png)

- Toilets and galleys are always placed before or after blocks of seats

  Sometimes toilets and galleys are placed where seats would normally be. This  often occurs in the tail section which has narrower sides but can still  provide more seats in the middle.

  **Example**

  [American Airlines Boeing 777-200

  [](https://www.seatguru.com/airlines/American_Airlines/American_Airlines_Boeing_777-200ER_E.php)

  ![Screenshot-2021-11-02-at-18.01.13-1](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\Screenshot-2021-11-02-at-18.01.13-1.png)

- Seats are aligned in rows in a cabin

  In wide-body aircrafts, the seats between the aisles are often "staggered" in respect to the seats near the windows in the same "row" to fill  cabin space more efficiently.

  **Example**

  [American Airlines Boeing 787-8

  [](https://www.seatguru.com/airlines/American_Airlines/American_Airlines_AA_Boeing_787-8_A.php)

  ![Screenshot-2021-11-02-at-18.04.57](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\Screenshot-2021-11-02-at-18.04.57.png)

- Seats are aligned in columns in a cabin

  Sometimes, when a seat is missing in a row, the remaining seats will be shifted by half a seat to keep them centered.

  **Example**

  [American Airlines Airbus A330-200](https://www.seatguru.com/airlines/American_Airlines/American_Airlines_Airbus_A330-200_C.php)

  ![Screenshot-2021-11-02-at-18.30.23-1](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\Screenshot-2021-11-02-at-18.30.23-1.png)

- Seats are aligned in columns in a cabin or shifted half a seat

  Not even that! In tail sections, rows with missing seats can start out  aligned with the other rows and slowly converge towards being shifted  half a seat across multiple rows.

  **Example**

  [Eurowings Airbus A330-200](https://www.seatguru.com/airlines/Eurowings_Airlines/Eurowings_Airbus_A330-200.php)

  ![Screenshot-2021-11-02-at-18.43.49-1](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\Screenshot-2021-11-02-at-18.43.49-1.png)

  