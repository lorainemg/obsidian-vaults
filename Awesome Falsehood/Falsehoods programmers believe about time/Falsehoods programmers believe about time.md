# Falsehoods programmers believe about time
Creado: 2022-06-16 22:55
Tags: #every-programmer-should-know, #falsehoods, #datetime, #time
Topic: [[Falsehoods Programmers Believe about Datetime]]

----

### Falsehoods programmers believe about time

Over the past couple of years [I have spent a lot of time](http://infiniteundo.com/post/25230828820/things-you-should-test) debugging other engineers’ test code.  This was interesting work, occasionally frustrating but always informative. One might not immediately think that test code would have bugs, but of course *all* code has bugs and tests are no exception.

I have repeatedly been confounded to discover just how many mistakes in *both* test *and* application code stem from misunderstandings or misconceptions about *time.*  By this I mean both the interesting way in which computers handle time, and the fundamental gotchas inherent in how we humans have constructed our calendar – daylight savings being just the tip of the iceberg.

In fact I have seen so many of these misconceptions crop up in other people’s (and my own) programs that I thought it would be worthwhile to collect a list of the more common problems here.

All of these assumptions are wrong

1. There are always 24 hours in a day.

   > **Maybe**, but probably **false**. It depends on what we call an hour. If we allow for some hours to not be exactly 60 * 60 seconds long (such as "hours" with a leap second, but we could still consider it an hour), then yes, in UTC / the Gregorian calendar.
   >
   > Local times don't work here, because spring-forward and fall-back times make the days 23 and 25 hours long.
   >
   > And if you're on another planet, then your definition of the day might be even weirder.

2. Months have either 30 or 31 days.

   > February.

3. Years have 365 days.

   > Leap years and not leap years

4. February is always 28 days long.

   > Leap years and not leap years

5. Any 24-hour period will always begin and end in the same day (or week, or month).

   > but I'm not sure I understand the assumption here. Clearly, a 24 hour period straddling a day cannot start and end in the same day, and such simple counter examples break the rest too.

6. A week always begins and ends in the same month.

7. [A week (or a month) always begins and ends in the same *year.*](https://href.li/?http://www.reddit.com/r/programming/comments/v8s0y/falsehoods_programmers_believe_about_time/c52k8m9)

8. The machine that a program runs on will always be in the GMT time zone.

   > *My* machine isn't.

9. Ok, that’s not true. But at least the time zone in which a program has to run will never change.

   > **False**, for many programs that need to deal with input in a multitude of timezones. Such as Google Calendar.
   >
   > If we still mean the machine the program is running on, the user can always pop open their preferences and change their timezone. *Something* is running at that point, even if it is the clock in the corner of your screen.

10. Well, surely there will never be a change to the time zone in which a program hast to run *in production.*

11. The system clock will always be set to the correct local time.

    > **False**. I run a lot of machines in UTC, that aren't anywhere near Greenwich.

12. The system clock will always be set to a time that is not wildly different from the correct local time.

    > Define "wildly different".

13. If the system clock is incorrect, it will at least always be off by a consistent number of seconds.

    > **False**. The very nature of clock "drift" is that it is a slow and gradual effect. The longer you let an imprecise clock run without adjusting it, the more it will drift off the actual value.

14. The server clock and the client clock will always be set to the same time.

    > **False**. What is the "same time": to what degree of accuracy?

15. The server clock and the client clock will always be set to *around* the same time.

16. Ok, but the time on the server clock and time on the client clock would never be different by a matter of *decades.*

    > **False**. Inside most desktop computers, there is a small watch battery. Among other things, it keeps the clock alive, and ticking. These batteries do die. When they do, the clock can stop ticking when the machine is off. It might also just reset to something like 1970.

17. If the server clock and the client clock are not in synch, they will at least always be out of synch by a consistent number of seconds.

    > **False**, mostly a combination of #13 and #11.

18. The server clock and the client clock will use the same time zone.

    > **False**. There are people all over the country, let alone the world, on the Internet.

19. The system clock will never be set to a time that is in the distant past or the far future.

    > **False**, see #16 for "distant past", and see a local troll for the distant future.

20. Time has no beginning and [no end.](https://href.li/?http://en.wikipedia.org/wiki/Year_2038_problem)

    > **False**. The big bang, and follow the link for the end.

21. One minute on the system clock has exactly the same duration as one minute on [any other clock](https://href.li/?http://en.wikipedia.org/wiki/Atomic_clock)

    > **False**. Not all clock drifts are the same. Atomic clocks are remarkably accurate, which is why we build them. My Macbook, without the crutch of an NTP server, is not so accurate.

22. Ok, but the duration of one minute on the system clock will be *pretty close* to the duration of one minute on most other clocks.

    > **False**. Again with the "pretty close". An NTP clock adjustment to that imprecise Macbook will prevent this from being true.

23. Fine, but the duration of one minute on the system clock would never be more than an hour.

    > But by now, I hope you see that there's probably a better solution to your problem.
    >
    > I honestly can't see when this would be false, honestly. Maybe if we take that machine with the depleted CMOS battery and keep rebooting it such that it never leaves 1970.
    >
    > Or my VCR, which is still flashing 12:00.

24. You can’t be serious.

    > Kids these days. Don't know what a VCR is. Or how to program one.

25. The smallest unit of time is one second.

    > **False**, because

26. Ok, one millisecond.

    > **False**. Nanoseconds. (And don't stop there.)

27. It will never be necessary to set the system time to any value other than the correct local time.

    > **False**. A lot of servers run UTC, because it is more useful than some very arbitrary local time.

28. Ok, *testing* might require setting the system time to a value other than the correct local time but it will never be necessary to do so *in production.*

    > **False**. That last example was production…

29. Time stamps will always be specified in a commonly-understood format like 1339972628 or 133997262837.

    > **False**. I personally dislike these. Do you know what times those represent? No, you don't. An ISO-8601 YYYY-MM-DDTHH:MM:SS is so much more readable.

30. Time stamps will always be specified in the same format.

    > **False**. We just mentioned two above.

31. Time stamps will always have the same level of precision.

    > **False**. Some things store it in seconds. Some in nanoseconds. Some in microseconds, some in milliseconds…

32. A time stamp of sufficient precision can safely be considered unique.

    > **False**. Two machines get really lucky.

33. A timestamp represents the time that an event actually occurred.

    > **False**. Generating a timestamp takes time. Your clock can also be wrong.

34. Human-readable dates can be specified in universally understood formats such as 05/07/11.

    > **False**, while I figure out if that's the fifth of July or the seventh of May. Or the seventh of November. Or the 11th of July.



## Referencias