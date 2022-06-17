# More falsehoods programmers believe about time
Creado: 2022-06-16 22:56
Tags: #every-programmer-should-know, #falsehoods, #datetime, #time
Topic: [[Falsehoods Programmers Believe about Datetime]]

----

## More falsehoods programmers believe about time; “wisdom of the crowd” edition

A couple of days ago I decided to [write down some of the things I’ve learned about testing][testing_post] over the course of the last [several years.][codeascraft] In the course of enumerating the areas that benefit most from testing, I realized that I had accumulated a lot of specific thoughts about how we as programmers tend to abuse the concept of _time._ So I wrote another post called **“[falsehoods programmers believe about time][original_post],”** where I included 34 misconceptions and mistakes having to do with both calendar and system time.  Most of these were drawn from my immediate experience with code that needed to be debugged (both in production and in test).

### All of these assumptions are wrong

*All of these falsehoods were suggested by people who commented on the [original post](http://infiniteundo.com/post/25326999628/falsehoods-programmers-believe-about-time).  Each contributor is credited below.*

1. The offsets between two time zones will remain constant.

   > **False**: Timezone rules (and thus offsets) change _all the [time_](https://gist.github.com/thanatos/eee17100476a336a711e#id1). IANA maintains the [timezone database](https://www.iana.org/time-zones), and as of this writing in April of 2015, the current version is 2015b, meaning there have been two changes this year already. And lest you think this is only small countries changing, [the United states revised their DST dates in 2005](https://en.wikipedia.org/wiki/Daylight_saving_time_in_the_United_States#2005_revision_to_dates_of_observance).

2. OK, historical oddities aside, the offsets between two time zones won’t change in the future.

   > **False**: We proved this in the first one's argument.

3. Changes in the offsets between time zones will occur with plenty of advance notice.

   > **Vague**, but let's say **False**. First, what's advance notice? We can quibble with the defintion. [Russian made a fairly quick change recently](http://blogs.technet.com/b/dst2007/archive/2014/08/22/announcement-update-for-russian-time-zone-changes.aspx) I think, whereby the law passed in August, the change was made in October, and Microsoft had a patch in September, so judge for yourself. Where governments are involved, I'm going with "plenty of advance notice" is probably not a guarantee.

4. Daylight saving time happens at the same time every year.

   > **False**. We've established that the rules change in #1.

5. Daylight saving time happens at the same time in every time zone.

   > **False**. "same time" is debatable here: The entire US (okay, okay, the bits that observe DST! And you know what bits I mean!) starts DST at "2 am". But that's 2am local, and thus, across the four major continental timezones, that's four _different_ 2 AMs. Of course, other countries don't follow suite; one of the reasons we have the database mentioned in #1 is that nobody can agree on the rules.

6. Daylight saving time always adjusts by an hour.

   > **True**? Being on the list, I doubt my answer here, but I don't know of a case. Since I'm sure the author isn't bluffing, I'm going with he knows something I don't.

7. Months have either 28, 29, 30, or 31 days.

   > **True**, *but only within our assumption* of a [Proleptic Gregorian calendar](https://en.wikipedia.org/wiki/Proleptic_Gregorian_calendar). When [the Gregorian calendar was adopted in Britian](https://en.wikipedia.org/wiki/Adoption_of_the_Gregorian_calendar), it was necessary to correct by 11 days. Wednesday, 2 September 1752, was followed by Thursday, 14 September 1752. So, that particular month was obviously well short of the normal length. Of course, that's *just Britian*. As mentioned, others adopted at different times

8. The day of the month always advances contiguously from N to either N+1 or 1, with no discontinuities.

   > **True**, *but only within our assumption*. The discussion of #7 includes an example of a discontinuity.

9. There is only one calendar system in use at one time.

   > **Vague**. **True**, *under our assumption*, but **false** if we humor the author. Our assumption defines the calendar system in use — we're clearly cheating our way through this question. As mentioned in #7, the Gregorian calendar system was adopted at different times in different places (and some places had riots around the adoption). Religions can also involve other calendar systems.

10. [There is a leap year every year divisible by 4.](https://t.umblr.com/redirect?z=http%3A%2F%2Fsupport.microsoft.com%2Fkb%2F214326&t=NWI0NjY0ZDRmOWRkYTk2ODZkMTMwN2IzY2FkMTI1MTA3MzVhODFmNSxEM2pHdWd5WQ%3D%3D&b=t%3A7TjPV930sD0_X0RgB6y6vA&p=https%3A%2F%2Finfiniteundo.com%2Fpost%2F25509354022%2Fmore-falsehoods-programmers-believe-about-time&m=1&ts=1642612008)

    > **False**. The link is in the original text. See [the Gregorian calendar](https://en.wikipedia.org/wiki/Gregorian_calendar) here:
    >
    > > The Gregorian reform modified the Julian calendar's scheme of leap years as follows:
    > >
    > > > Every year that is exactly divisible by four is a leap year, except for years that are exactly divisible by 100, but these centurial years are leap years if they are exactly divisible by 400. For example, the years 1700, 1800, and 1900 are not leap years, but the year 2000 is.
    >
    > Our computer revolution falls at a bad (or good?) time here: the "divisible by 4" "rule" "works" from 1901 to 2099. The year 2000 would have been an exception, but the exception-to-the-exception saved us! But 1900 is not a leap year, and I can bet you all sorts of software will be breaking in 2100.

11. Non leap years will never contain a leap day.

    > **True**, *but only within our assumption*. See the link from where we made our assumption about [when the leap years were](https://en.wikipedia.org/wiki/Julian_calendar#Leap_year_error) for very early years for a counter example, but I don't feel like this counts for much.

12. It will be easy to calculate the duration of x number of hours and minutes from a particular point in time.

    > **False**. Within our assumption, leap seconds ruin this. Leap seconds are derived from measurements of the earth's movement, and this movement is not predictable. They're announced beforehand, but not by a whole lot. Thus, offsets into the future can change when leap seconds are allowed.
    >
    > If this question means something like "what is the datetime x + the offset y?", even just the rules of the Gregorian calendar don't make this easy. Leap years, months with different lengths, yikes! Often times, the offset too is problematic. What is "today + 1 month"? Is a month a constant number of days? Do you just increment the number of the month, modulo 12? (but then, what is Jan 31 + 1 month? Feb 31?)

13. The same month has the same number of days in it everywhere!

    > **True**, *but only within the assumption*. Again, the Gregorian reform.

14. Unix time is completely ignorant about anything except seconds.

    > [Unix time](https://en.wikipedia.org/wiki/Unix_time),
    >
    > > Unix time (also known as POSIX time or Epoch time) is a system for describing instants in time, defined as the number of seconds that have elapsed since 00:00:00 Coordinated Universal Time (UTC), Thursday, 1 January 1970, not counting leap seconds.
    >
    > I'm going *mostly* with **true**. Note the next few lines,
    >
    > > it is neither a linear representation of time nor a true representation of UTC
    >
    > I usually think of Unix time as **a duration**. It's "the number of seconds" (a duration) *since a fixed point* — which thus gives you time, with **huge** amends to the note above.

15. Unix time is the number of seconds since Jan 1st 1970.

    > **True**. See #14. I will note: since *midnight* Jan 1st 1970 *UTC*.

16. The day before Saturday is always Friday.

    > **True**. Definitely within the assumption, I think, but even outside, I'm not sure when this wouldn't be, honestly. Fill me in?

17. Contiguous timezones are no more than an hour apart. (aka we don’t need to test  what happens to the avionics when you fly over the International Date  Line)

    > **False**. Well, there IDL represents one example. There's a [3 hour jump between the border of China and Pakistan](https://en.wikipedia.org/wiki/Time_zone#/media/File:World_Time_Zones_Map.png), mostly due to China being a single timezone.

18. Two timezones that differ will differ by an integer number of half hours.

    > **False**. Some timezones are offset from UTC by 15 minute intervals. See, for example, [the westernmost third of Australia](http://en.wikipedia.org/wiki/Time_zone#/media/File:World_Time_Zones_Map.png).

19. Okay, quarter hours.

    > **False**, at least historically. See for example [UTC−00:25:21](https://en.wikipedia.org/wiki/UTC−00:25:21). I think at the time of this writing, quarer hours is true, for present-day timezones. So if you have no historical data… and the laws never change…

20. Okay, seconds, but it will be a consistent difference if we ignore DST.

    > **Vague**. I'm not sure what "consistent difference" means here.

21. If you create two date objects right beside each other, they’ll represent the same time. (a fantastic Heisenbug generator)

    > **False**, of course, and for the reasons stated. Assume a clock with second granularity (ha!): creating the object must consume some CPU, so if you two in a row, at some point, you're going to get lucky, and the next one will be on (at least) the next second. Most clocks have much better resolution, of course, and they're probably only going to get better.

22. You can wait for the clock to reach exactly HH:MM:SS by sampling once a second.

    > **False**, and whats "exactly" here? A second is a whole second long. (Well, usually.) System clocks can very easily skip right over your desired time: clock adjustments from NTP servers, the machine was asleep, hibernated, off, or your process just didn't get CPU time, or even leap seconds can all cause you to miss your desired timestamp. Just try for the best, and work with what you get.

23. If a process runs for n seconds and then terminates, approximately n  seconds will have elapsed on the system clock at the time of  termination.

    > **False**, see #22, as most of the reasons apply here. Did I mention you can get no CPU time?

24. Weeks start on Monday.

    > **False**. According to ISO-8601, the week starts on Monday. Of course, in my country, the week starts on Sunday. The world seems to agree that it's either Saturday, Sunday or Monday. See [Week](https://en.wikipedia.org/wiki/Week#Week_numbering).

25. Days begin in the morning.

    > **False**. If you're on a pole, the sun might never set or rise in certain parts of the year, so what is "morning"?

26. Holidays span an integer number of whole days.

    > I don't actually know this one, but I'm sure someone has an example, and if not, I'm sure someone will invent one.

27. The weekend consists of Saturday and Sunday.

    > I don't actually know this one either. In my culture, this is true, but it wouldn't shock me.

28. It’s possible to establish a total ordering on timestamps that is useful outside your system.

    > **True**, *but only within our assumption*, even then, it is tenuous. And really, I think it depends on your timestamps and what you mean by total ordering. UTC timestamps should be orderable, but they're only as accurate as the machine that stamped the time, and I have see clock drifts of well over a minute. That might matter to you. If you have Unix timestamps, this isn't true. Remember that weird note?
    >
    > > it is neither a linear representation of time
    >
    > Unix timestamps will repeat during a leap second, so two timestamps within those leap seconds can't be reliably ordered, because we don't know which of two actual instants in time the timestamp refers to. As another example, consider having a local time of 2:15am and 2:20am during a DST fallback from 3am to 2am. If I don't tell you which or both of 2:15 and 2:20am were before or after the fallback, you cannot order them. You can defeat the DST fallback problem by recording which side of the fallback you're on (and some libraries do this).

29. The local time offset (from UTC) will not change during office hours.

    > **Unanswerable**. I'm not even going to guess what your office hours are. (This probably means it is a falsehood then, if you belive it…)

30. Thread.sleep(1000) sleeps for 1000 milliseconds.

    > **False**: this runs into the same issues as #22. Also, how precise is your clock? Is it *perfectly* precise? Because if not, we can quibble about what 1000 milliseconds is.

31. Thread.sleep(1000) sleeps for >= 1000 milliseconds.

    > **False**. Clocks are imprecise, and if your clock is fast, then this won't hold. (It occurs I could perhaps throw relativistic effects into the discussion here, but let's not.)

32. There are 60 seconds in every minute.

    > **False**. Leap seconds can make this 59 or 60. Clock adjustments can mess with you further.

33. Timestamps [always advance monotonically.](https://href.li/?http://www.metafilter.com/117073/Falsehoods-Programmers-Believe#4405410)

    > **False**: have I mentioned clock adjustments?

34. GMT and UTC are the same timezone.

    > **True**, according to the IANA timezone database! There's some historical differences, of course, and the names are different.

35. Britain uses GMT.

    > **False**. Britian observes British summer time, which is their name for DST, during which they're offset from GMT.

36. Time always goes forwards.

    > **False**. Well, true in the real world, so far as we know. Clock adjustments, once again, can mess with you. POSIX timestamps during a leap second insertion will go backwards.

37. The difference between the current time and one week from the current time is always 7 * 86400 seconds.

    > **False**. In UTC, leap seconds, again. In a local time, DST spring-forward and fall-back will ruin this as well. Rule adjustments in a timezone will also mess around with this.

38. The difference between two timestamps is an accurate measure of the time that elapsed between them.

    > **False**. How accurate are your clocks? Are you using Unix timestamps, which as we discussed above, do funny stuff during leap seconds?

39. 24:12:34 is a invalid time

    > *Eh.* Some people seem to think this is valid. This gets used to attach a time to a particular day that isn't really part of a particular day. ISO-8601 allows 24:00, but *only* that, I believe — i.e., the example in the article isn't valid within ISO-8601.

40. Every integer is a theoretical possible year

    > **False**. The universe began at some point, so there exists negative integers for which this isn't true. (Or at least, we have no idea whether it is true.) The universe might end someday. Also, year 0 didn't occur on some calendars.

41. If you display a datetime, the displayed time has the same second part as the stored time

    > I don't know this one. This depends on so many things, such how you stored the time, and how you're displaying the time.

42. Or the same year

    > **False**: Look to [ISO week numbers](https://en.wikipedia.org/wiki/ISO_week_date) for an example. For example, `2009-W01-1` corresponds to `2008-12-29`. Those are both ISO-8601 dates, and they represent the same thing, but have different year components.
    >
    > Also, if your internal stored format is UTC (which is common), and you display that timestamp as a local time, timezone adjustments can of course throw it into the next or previous year.

43. But at least the numerical difference between the displayed and stored year will be less than 24

    > Well, the difference between 1 BC and 1 AD (adjancent years) is exactly two in integral form, and the question stipulates "less than 2". Don't really know here.

44. If you have a date in a correct YYYY-MM-DD format, the year consists of four characters.

    > **False**, once you hit the year 10000 AD.

45. If you merge two dates, by taking the month from the first and the day/year from the second, you get a valid date

    > **False**. `1 Feb`, `31 Jan`… `31 Feb`.

46. But it will work, if both years are leap years

    > **False**, same example. (Just append a leap year to both dates: you still end up with `31 Feb`.)

47. If you take a w3c published algorithm for adding durations to dates, it will work in all cases.

    > I don't know here. I don't know what the “w3c published algorithm” is, and I'm going to leave it as an exercise to you, reader, to look it up. It's late here.

48. The standard library supports negative years and years above 10000.

    > **False**. I usually work in Python, and according to [the standard library's documentation](https://docs.python.org/2/library/datetime.html):
    >
    > ```
    > datetime.MINYEAR
    > ```
    >
    > The smallest year number allowed in a date or datetime object. `MINYEAR` is 1.
    >
    > ```
    > datetime.MAXYEAR
    > ```
    >
    > The largest year number allowed in a date or datetime object. `MAXYEAR` is 9999.

49. Time zones always differ by a whole hour.

    > **False**. We showed in #18 that quarter-hour offsets from UTC exist in timezones, so it should be obvious that if hour-aligned and non-hour-aligned timezones exist, that this cannot be true.

50. If you convert a timestamp with millisecond precision to a date time with  second precision, you can safely ignore the millisecond fractions.

    > I'm presuming because they'll be 0, is the assumption here? I'm not entirely sure what's going on. In our assumption, I think this should hold **true**.

51. But you can ignore the millisecond fraction, if it is less than 0.5.

    > I'm now lost as to the exact operation we're preforming on this poor timestamp.

52. Two-digit years should be somewhere in the range 1900-2099

    > **False**. And Y2.1k was thus born…

53. If you parse a date time, you can read the numbers character for character, without needing to backtrack

    > This really needs to be put within the context of what language we're attempting to parse, otherwise, it is unanswerable.
    >
    > Even in ISO-8601, stumbling upon a `W` might be exciting, in that you're now parsing a week-date, and the year you just parsed might not actually be the year. Or if you hit a third digit in what you thought might be a month component, and thus you now know you're parsing an ordinal date.

54. But if you print a date time, you can write the numbers character for character, without needing to backtrack

    > **Maybe.** (so I guess false.) If you have a date stored as a UTC ISO timestamp in YYYY-MM-DD and you want it displayed the same… then yes, just output it!

55. You will never have to parse a format like `---12Z` or `P12Y34M56DT78H90M12.345S`

    > I really hope not.

56. There are only 24 time zones

    > **False**. See the IANA timezone database. There's a ton. Way more than 24.

57. Time zones are always whole hours away from UTC

    > **False**, see #18.

58. Daylight Saving Time (DST) starts/ends on the same date everywhere

    > **False**. The DST start/end date is set by governments, and they'll never agree on such a thing. Even without that, you can reason through this: DST starts in the spring, with the "spring forward" event. Spring is in the first half of the year in the northern hemisphere, but the latter half for the southern hemisphere.

59. DST is always an advancement by 1 hour

    > **True**. Right? Please? I'm curious to know who doesn't now…

60. Reading the client’s clock and comparing to UTC is a good way to determine their timezone

    > **False**. You can try this, but an offset at a particular time can map to multiple timezones. In fact, the mapping between offsets and what timezones are in that offset changes during the year as people go in and out of DST and laws change.

61. The software stack will/won’t try to automatically adjust for timezone/DST

    > **False**. Windows will adjust automatically in most cases. Linux, running with a TZ of UTC won't.

62. My software is only used internally/locally, so I don’t have to worry about timezones

    > **False**. It's only a matter of *time*.

63. My software stack will handle it without me needing to do anything special

    > **False**. The C standard library, for example, is pretty oriented towards some concept of the local time of the system, which isn't useful if you're writing a web server handling requests from users in a multitude of timezones.

64. I can easily maintain a timezone list myself

    > **False**. See question #1: there were *already* two updates this year alone.

65. All measurements of time on a given clock will occur within the same [frame of reference.](https://href.li/?http://www.reddit.com/r/programming/comments/v8s0y/falsehoods_programmers_believe_about_time/c52kqpa)

    > **False?** Are we bringing relativity into this? Dammit Jim I'm a software engineer, not a quantum physicist.

66. The fact that a date-based function works now means it will work on any date.

    > **False**, but mostly on the basis that we *really* need to qualify the "date-based function" under consideration here to understand the implications of saying anything about it.

67. Years have 365 or 366 days.

    > **True**, *but only under our assumption*. The lost days during the adoption of the Gregorian calendar apply yet again. Also, if you define day as 60 * 60 * 24 seconds, then leap seconds ruin this as well.

68. Each calendar date is followed by the next in sequence, without skipping.

    > **True**, *but only under our assumption*; again, the adoption of the Gregorian calendar.

69. A given date and/or time unambiguously identifies a unique moment.

    > **True-ish**, *but only under our assumption*. Again, we get back to how Unix timestamps get all weird during leap seconds. Also again, if your definition of "date and/or time" refers to a local time in a timezone with DST and you don't specify whether you're in DST or not, the fallback will cause issues.
    >
    > Outside our assumption, the adoption of the Gregorian calendar (are you tired of hearing that yet?) was not uniform (different places did so at different times), and thus, you need to know what calendaring system was effectively in use.

70. Leap years occur every 4 years.

    > **False**, on so many levels. See the discussion about the rules for leap years in #10. 1896 was a leap year. 1900 *wasn't*. 1904 was, thus putting 8 years between leap years.
    >
    > Further, we also have the problem of really early leap years, as discussed in #11 and the intro.
    >
    > But we also have Sweden. Yes, Sweden. During the adoption of the… oh, you know the drill. Anyways, Sweden is *very special*. I'm just going to quote the whole thing, because it is so special.
    >
    > > Sweden's relationship with the Gregorian calendar was a difficult one. Sweden started to make the change from the Julian calendar and towards the Gregorian calendar in 1700, but it was decided to make the (then 11-day) adjustment gradually by excluding the leap days (29 February) from each of 11 successive leap years, 1700 to 1740. Meanwhile, the Swedish calendar would be out of step with both the Julian calendar and the Gregorian calendar for 40 years; also, the difference would not be constant but would change every four years. This system had potential for confusion when working out the dates of Swedish events in this 40-year period. To add to the confusion, the system was poorly administered, and the leap days that should have been excluded from 1704 to 1708 were not excluded. The Swedish calendar (according to the transition plan) should have been 8 days behind the Gregorian but was 10 days behind. King Charles XII recognised that the gradual change to the new system was not working, and he abandoned it. Rather than proceeding directly to the Gregorian calendar, it was decided to revert to the Julian calendar. This was achieved by introducing the unique date 30 February in 1712, adjusting the discrepancy in the calendars from 10 back to 11 days. Sweden finally adopted the Gregorian calendar in 1753, when Wednesday, 17 February, was followed by Thursday, 1 March. Since Finland was under Swedish rule at that time, it did the same.[7] Finland's annexation to the Russian Empire did not revert this, since autonomy was granted, but government documents in Finland were dated in both the Julian and Gregorian styles. This practice ended when independence was gained in 1917.
    >
    > Mind you, I only come up with 10 leap years between 1700 to 1740, so I'm not sure it would have worked out anyways.

71. You can determine the time zone from the state/province.

    > **False**. Texas, for example, straddles the Central and Mountain timezones in America.

72. You can determine the time zone from the city/town.

    > **False**. Let's go find some town on the border.

73. Time passes at the same speed on top of a mountain and at the bottom of a valley.

    > Now I know you're trying to bring relativity into this.

74. One hour is as long as the next in all time systems.

    > **False**, leap seconds.

75. You can calculate when leap seconds will be added.

    > **False**, unfortunately they're measured. Or, if *you* can, you should share this exciting discovery.

76. The precision of the data type returned by a getCurrentTime() function is the same as the precision of that function.

    > **False**, and is basically as it says on the tin. The data structure will have its own precision: maybe it can store the time out to the nanosecond. The function will access some clock, and that clock's accuracy probably doesn't match the datastructure. Different computers might include clocks from different manufacturers, which have different precisions. I'd bet even hardware all made by the same manufacturer can have different precision.
    >
    > And if your function returns the time out the nanosecond (not uncommon), it probably took more than a nanosecond to set up the function call in whatever calling convention you have, make the actual call, make a system call, read the hardware, encode the result…

77. Two subsequent calls to a getCurrentTime() function will return distinct results.

    > **False**. Maybe your clock is only precise to the millisecond, but the CPU is capable of performing this function 20 times per millisecond.
    >
    > Also, clock adjustments.

78. The second of two subsequent calls to a getCurrentTime() function will return a larger result.

    > If 77 is false (and it is), then this must by definition be **false** as well. If you try to correct with "equal or larger", but clock adjustments still render this false.

79. The software will never run on a space ship that is orbiting a black hole.

    > I really hope not.


## Referencias
[[Falsehoods programmers believe about time]]