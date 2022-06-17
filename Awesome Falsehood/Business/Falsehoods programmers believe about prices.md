# Falsehoods programmers believe about prices

Creado: 2022-06-16 22:44
Tags: #every-programmer-should-know, #falsehoods, #business
Topic: [[Falsehoods Programmers Believe about Business]]

----
## Falsehoods programmers believe about prices

1. You can store a price in a floating point variable.
2. All currencies are subdivided in 1/100th units (like US dollar/cents, euro/eurocents etc.).
3. All currencies are subdivided in decimal units (like dinar/fils)
4. All currencies currently in circulation are subdivided in decimal units. (to exclude shillings, pennies) (counter-example: MGA)
5. All currencies are subdivided. (counter-examples: KRW, COP, JPY... Or subdivisions can be deprecated.)
6. Prices can't have more precision than the smaller sub-unit of the currency. (e.g. gas prices)
7. For any currency you can have a price of 1. (ZWL)
8. Every country has its own currency. (EUR is the best example, but also Franc CFA, etc.)
9. No country uses another's country official currency as its official currency. (many countries use USD: Ecuador, Micronesia...)
10. Countries have only one currency.
11. Countries have only one currency currently in circulation. (Panama officially uses both PAB and USD)
12. I'll only deal with currencies currently in circulation anyway.
13. All currencies have an ISO 4217 3-letter code. (The Transnistrian ruble has none, for example)
14. All currencies have a different name. (French franc, "nouveau franc")
15. You always put the currency symbol after the price.
16. You always put the currency symbol before the price.
17. You always put the currency symbol either after, or before the price, never in the middle.
18. There's only one currency symbol for any currency. (元, 角, 分 are increasing units of the Chinese renminbi.)
19. For a given currency, you always, but always, put the symbol in the same place.
20. OK. But if you only use the ISO 4217 currency codes, you always put it before the price. (Hint: it depends on the language.)
21. Before the price means on the left. (ILS)
22. You can always use a dot (or a comma, etc.) as a decimal separator.
23. You can always use a space (or a dot, or a comma, etc.) as a thousands separator.
24. You separate big prices by grouping numbers in triplets (thousands). (One writes `¥1 0000`)
25. Prices at a single company will never range from five digits before the decimal to five digits after.
26. Prices contains only digits and punctuation. (Germans can write `12,- €`)
27. A price can be *at most* 10^N for some value of N.
28. Given two currencies, there is only one exchange rate between them at any given point in time.
29. Given two currencies, there is at least one exchange rate between them at any given point in time. (restriction on export of MAD, ARS, CNY, for example)
30. And the final one: a standalone `$` character is always pronounced dollar. (It's also the peso sign.)

## Referencias