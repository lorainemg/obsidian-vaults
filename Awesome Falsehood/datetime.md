# Falsehoods Programmers Believe

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

## More falsehoods programmers believe about time; “wisdom of the crowd” edition

A couple of days ago I decided to [write down some of the things I’ve learned about testing][testing_post] over the course of the last [several years.][codeascraft] In the course of enumerating the areas that benefit most from testing, I realized that I had accumulated a lot of specific thoughts about how we as programmers tend to abuse the concept of _time._ So I wrote another post called **“[falsehoods programmers believe about time][original_post],”** where I included 34 misconceptions and mistakes having to do with both calendar and system time.  Most of these were drawn from my immediate experience with code that needed to be debugged (both in production and in test).

## All of these assumptions are wrong

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

## Falsehoods programmers believe about time and time zones

- Every day has 24 hours

> Counter example: Because of daylight saving time (DST) some days  could have 23 hours and some could have 25 hours. Or some other amount  of hours - whole or not.

- OK, but every day without DST changes is 86400 (60 \* 60 \* 24) seconds long

Some times the UTC offset for a time zone is changed.

- **… at least in UTC**

> [Leap seconds](http://www.nextleapsecond.com/) cause some  days to have an extra second. And theoretically there could be negative  leap seconds. Although negative leap seconds have not happened yet  because the rotation of the earth so far has been slower than UTC, as it were, and not faster.

- **Week one of a year starts in January every year**

> January 1st is not always a monday so some days of an ISO week will  be in different years. Example: 2014 December 28th belongs to week 1 of  2015.

- **If I know what time zone someone is in and they just tell  me the date and local time, I can always use software to find out what  time that is in UTC**

> If they are in the middle of changing from summertime to wintertime,  the clock will be set back one hour. This means that an hour exists  twice, so to speak. If the clock is set back to 2:00 and someone tells  you that the local time was 2:17 for instance, you do not know if he is  talking about 2:17 before the clocks were set back or 2:17 after the  clocks were set back.

- **DST always sets the clock back and forth by exactly one hour**

> Throughout history there are examples of DST rules that set the  clocks back and forth 2 hours or 30 minutes. A current example (h/t [Derick Rethans](https://twitter.com/derickr/status/560551074701275136)) is Australia/Lord_Howe which advances the clocks by 30 minutes for DST.

- **Countries that observe DST begin observing DST in the first half of the year and end observing DST in the last half of the year**

> Not in the southern hemisphere, where summer time might begin in October and end in March.

- **OK, but DST always starts around spring and continues until fall**

> Except for Morocco, where in the middle of summer, DST is suspended for a month during Ramadan (depending on which year it is).

- **If I have a timestamp for a future event, I can convert it to UTC, store it as UTC along with the time zone and be sure that I can reliably convert it back to the correct “wall time” in the future**

> If time zone rules change in the mean time for the time zone in  question, converting back from UTC to “local time” might produce a  different result. [Follow this link for a solution](http://www.creativedeletion.com/2015/03/19/persisting_future_datetimes.html).

- **Time zone rules do not change**

> In 2014 there were 10 updates to the [Olson database](https://www.iana.org/time-zones) released during the year.

- **If I keep my operating system up to date by installing updates, my operating system will have all the newest time zone updates**

> As of January 2015 the newest tzdata package for Ubuntu 14 has data  from June 2014 and not the latest 2014j release from November 2014.

- **CST is a unique identifier for a time zone (Central Standard Time in the USA)**

> CST is also used for: Cuba Summer Time, China Time, Central Standard  Time (Australia). PST is used for Pakistan Standard Time and Pacific  Standard Time. If you want a unique identifier for the time zone in the  Pacific West of the USA it looks like this: “America/Los_Angeles”.

- **If you have two UTC timestamps it is possible to calculate how many seconds will be between them even if one of the timestamps are a year into the future**

> There might be [leap seconds](http://www.nextleapsecond.com/) introduced, but you cannot be sure when or how many. However they are  announced at least 6 months in advance, so if none of the two times are  more than 6 months in the future and you keep up with news about leap  seconds you can calculate it.

- **The date-time combination 2014 March 30th 2:20:42 is always valid**

> In central European time zones such as Europe/Copenhagen, that time  does not exist in local time because of DST making the clocks being  advanced by an hour from 2:00 to 3:00. This causes an hour to be  skipped.

- **The time 23:59:60 is always invalid**

>  When leap seconds are inserted, a minute will be 61 seconds long.

- **I can trust that if someone has written a library to handle date and time, it will work reasonably well**

>  Many people write libraries without knowing much about the domain.  And developers who also do not know much about the domain will use those libraries. Often things will work fine for a long time if for instance  you only deal with timezones in a few countries where the time zone  rules do not change a lot. It works fine - until it does not. It can  become a case of the blind library developers leading the blind library  users.

This text was inspired by other “falsehoods programmers believe” posts. And also by my experiences building a [tzdata parser and date-time library for Elixir](http://github.com/lau/calendar) and using other date-time libraries through the years.

PS. This was meant as a thought provoking eye opener. But all of this might seem negative and not constructive. Pointing out problems without any solutions. What can you do, to avoid having these issues cause  problems in the systems you develop? I plan to write posts about  solutions, so check back here soon.

## Falsehoods programmers believe about Unix Time

These three facts all seem eminently sensible and reasonable, right?

1. Unix time is the number of seconds since 1 January 1970 00:00:00 UTC
2. If I wait exactly one second, Unix time advances by exactly one second
3. Unix time can never go backwards

False, false, false.

But it’s unsatisfying to say “this is false” without explaining *why*, so I’ll explain that below. If you’d like to think about it first and  make your own guess, don’t scroll past the picture of the clock! 

All three of these falsehoods have the same underlying cause: *[leap seconds](https://en.wikipedia.org/wiki/Leap_second)*. If you’re unfamiliar with leap seconds, here’s a brief primer:

There are two factors that make up UTC:

- [International Atomic Time](https://en.wikipedia.org/wiki/International_Atomic_Time), which is an average of hundreds of atomic clocks spread around the  globe. We can measure a second from the electromagnetic properties of an atom, and it’s the most accurate measurement of time known to science.
- [Universal Time](https://en.wikipedia.org/wiki/Universal_Time), which is based on the Earth’s rotation about its own axis. One complete rotation is one day.

Problem is, these two numbers don’t always match. The Earth’s rotation isn’t  consistent – it’s gradually slowing down, so days in Universal Time are  getting longer. Atomic clocks, on the other hand, are fiendishly  accurate, and consistent for millions of years.

When the two times drift apart, a leap second is added or removed to UTC to bring them back together. Since 1972, [the IERS](https://en.wikipedia.org/wiki/International_Earth_Rotation_and_Reference_Systems_Service) (who manage this stuff) have inserted an extra 27 leap seconds. The  result is a UTC day with 86,401 seconds (one extra), or 86,399 (one  missing) – both of which mess with a fundamental assumption of Unix  time.

Unix time assumes that each day is exactly 86,400 seconds  long (60 × 60 × 24 = 86,400), leap seconds be damned. If there’s a leap  second in a day, Unix time either repeats or omits a second as  appropriate to make them match. As of 2019, the extra 27 leap seconds  are missing.

And so our falsehoods go as follows:

- Unix time is the number of seconds since 1 January 1970 00:00:00 UTC, *minus leap seconds*.

- If I wait exactly one second, Unix time advances by exactly one second, *unless a leap second has been removed*.

  So far, there’s never been a leap second removed in practice (and the  Earth’s slowing rotation means it’s unlikely), but if it ever happened,  it would mean the UTC day is one second shorter. The last UTC second  (23:59:59) is dropped.

  Each Unix day has the same number of  seconds, so when the next day starts, it skips ahead by one. The final  Unix second of the shorter day never gets allocated to a UTC timestamp.  Here’s what that would look like, in quarter-second increments:

  ![unix_time_skips_forwards](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\unix_time\unix_time_skips_forwards.png)

  If you start at 23:59:58:00 UTC and wait one second, the Unix time advances by *two* seconds, and the Unix timestamp 101 never gets assigned.

- Unix time can never go backwards, *unless a leap second has been added*.

  This one has happened in practice – 27 times at time of writing. The UTC day gets an extra second added to the end, 23:59:60. Each Unix day has the  same number of seconds, so it can’t just add an extra second – instead,  it repeats the Unix timestamps for the last second of the day. Here’s  what that would look like, in quarter-second increments:

  ![unix_time_goes_backwards](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\unix_time\unix_time_goes_backwards.png)

  If you start at 23:59:60.50 and wait half a second, the Unix time goes *back* by half a second, and the Unix timestamp 101 matches two UTC seconds.

And these probably aren’t even the only weirdnesses of Unix time – they’re  just the ones I half-remembered yesterday, enough to check a few details and write a blog post about.

Time is *straaaaaange*.

## Falsehoods programmers believe about time zones

- Misconception #1: UTC offsets go from -12 to +12**

  > Turns out, UTC offsets span from -12 to +14. Yeah, +14. That's gives you 27  hours UTC can be offset by (don't forget the zero offset)
  >
  > How does it work? UTC-12 has the same time as UTC+12, but is one day behind. Same goes for UTC-11 and UTC+13, etc.
  >
  > Why that crazy range? That was a result of pacific islanders decided they  wanted to be on a specific side of the international date line. 
  >
  > It makes for a very jagged international date line
  >
  > ![pasted-image-0--1-](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\timezones\pasted-image-0--1-.png)

- Every UTC offset corresponds to exactly one time zone

  Here are 10 distinct time zones which are all at UTC+5:

  - Aqtobe Time
  - Mawson Time
  - Maldives Time
  - Oral Time
  - Pakistan Standard Time
  - French Southern and Antarctic Time
  - Tajikistan Time
  - Turkmenistan Time
  - Uzbekistan Time
  - Yekaterinburg Time

  You might be wondering: if they’re all at the same UTC offset, why couldn’t all those countries just use the same time zone? Perhaps Pakistanis  weren’t keen about being on “Yekaterinburg Time”

- **There are more countries in the world than time zones**

  >  How could this one possibly be wrong? Well...
  >
  > 1. Many countries want their very own time zone (how many do you think run on Myanmar Time?)
  >
  > 2. Some countries split themselves up into multiple time zones (e.g. eastern and western times)
  >
  > 3. Military time alone uses 25 time zones, one for each hour from UTC-12 to UTC+12
  >
  > 4. DST. More on this one below
  >
  >    All together, there are[ 244 time zones](https://www.timeanddate.com/time/zones/) used by the 195 countries in the world.

- Every time zone has exactly one agreed upon name

  > Ever notice how every time zone consists only of English words?  Awfully kind of Spanish and French speaking countries to graciously use  our language, right?
  >
  > Hah, Yeah right. 
  >
  > Eastern Standard Time, Tiempo del Este, and Heure Normale de l'Est are all different names for the exact same time zone.
  >
  > Have fun coding that into your library.

- Time zones are always offset from UTC by an integer number of hours

  > India standard time is five and a half hours off of UTC. There are many more examples

- Fine, time zones are always offset from UTC by an integer number of half-hours

  > Nepal likes to be at the 45 minute UTC offset.
  >
  > Why does that extra 15 minutes matter so much to them? Because[ they really want](https://www.bbc.com/news/world-asia-33815153#:~:text=Nepal is 5 hours and,a mountain east of Kathmandu.&text=It gets trickier in the,t officially have time zones.) their mountain to have the sun right above it at noon.
  >
  > But it makes you wonder: what would happen if the mountain ever shifted?
  >
  > ![mountain-moved-3](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\timezones\mountain-moved-3.png)

- A country stays at the same UTC offset all year long

  > Don't forget about Daylight Saving Time! Or as the Europeans call it "Summer Time."  
  >
  > Countries practicing DST change their UTC offset twice every year.

- There is a standard format for declaring time zones

  > Hah, I wish. Here are some standards I discovered, there may be more:
  >
  > **Common name**
  >
  > These are the traditional time zone names we’re used to. Example: Pacific Standard Time.
  >
  > But I don't know if there's an official term for these names, they just that unstandardized.
  >
  > **IANA zone keys**
  >
  > This is as close to the official standard as you can get. It's not at all  official, but it's something the developer community has rallied around.
  >
  > It's a [painstakingly maintained database](https://www.iana.org/time-zones) which contains all known time zone data representing the entire history of local time for places around the globe.  It doesn't give any zone a  name though, preferring to use the name of the most prominent city in  there, which leads to:
  >
  > **Prominent city based**
  >
  > This one is "[basically bad UI that derives from the IANA zone keys](https://twitter.com/pganssle/status/1319794747876253697)"
  >
  > Full time zone names come with naming complications, which we discussed  above. If that wasn't enough fun, there's also the political  implications of recognizing certain time zones such as Israel Standard  Time.
  >
  > Some developers took the safer route and identified time  zones only by the name of a prominent city in it, not bothering to map  it to a common name. That's why the Ubuntu time zone picker makes you  select "New York'' instead of Eastern Standard Time.
  >
  > **Forget time zones, use the raw UTC offset**
  >
  > W3's international standard gave up on the notion of time zones and declared that engineers should only store a timestamp's[ raw UTC offset](https://www.w3.org/TR/NOTE-datetime).
  >
  > **GPS Coordinates**
  >
  > Fun fact: Many APIs for getting a region's UTC offset only want a UTC time  and latitude/longitude coordinates. This lets them define any moment  unambiguously and not have to worry about Daylight Saving Time.
  >
  > If you squint your eyes a bit, you could consider this a fourth standard.

- Daylight Saving Time starts at the same time every year

  > Did you think this would be the one thing world powers agree on? Each country choose when to start it's own DST

- A country's time zone never changes

  > Almost every year some country will pass a law to edit their time zone.
  >
  > In a particularly memorable example, a few years ago the Samoan islands  wanted to be on the other side of the international date line to get the same weekends as their Australian trading partners. So on midnight Dec  29th, they changed their UTC offset from -11 to +13 UTC, skipping Dec  30th and going straight to Dec 31st.
  >
  > Samoan citizens had one less day to celebrate the holidays that year.
  >
  > On the plus side, just 40 miles away the American Samoa Islands stayed on  the other side of the international date line. Now Samoans can celebrate new years on the Western Island, and then boat over to American Samoa  for a second new year’s party the next night.
  >
  > ![pasted-image-0--2-](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\timezones\pasted-image-0--2-.png)

- A country stays in the same time zone during Daylight Saving Time

  > Funny thing about DST, it doesn't actually change the time zone's UTC offset.  Instead, Daylight Saving Time countries switch to a different  time zone, with a different name.
  >
  > For example:
  >
  > Texas goes from Central Standard Time to Central Daylight Time.
  >
  > Chile goes from Chile Standard Time to Chile Summer Time
  >
  > ![dst-shift](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\timezones\dst-shift.png)

- Daylight Saving Time starts around March and ends around October

  > The Southern hemisphere has their summer in the other half of the year. The pattern flips.

- Every time zone has it’s own name

  > Which country should get to claim "Eastern Standard Time"?
  >
  > North America claimed dibs by virtue of inventing the name, but do you think  no one objected? Australia thought it sounded like a fine name to use,  and so even though the rest of the world refer to their time zone as  Australian Eastern Standard Time, [some](http://disq.us/p/2cqg1bc) of it's own citizens just call it "Eastern Standard Time" (not all of them [call it that though](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9qv6cc/)).

- Every time zone has its own abbreviation

  > Which of these was meant when someone says CST?
  >
  > - Central Standard Time
  > - China Standard Time
  > - Cuba Standard Time
  >
  > And remember how the time zone name changes during Daylight Saving Time?  Many people don’t know that and keep using the wrong abbreviations  during DST months. CST might be used for Central Daylight Time.
  >
  > If there's no standard name for time zones, can you really expect one for the abbreviations?
  >
  > ![fake-franks](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\timezones\fake-franks.png)

- There is always an unambiguous conversion from one time zone to another

  > If I say I want to convert 5pm Eastern Standard Time to Pakistan  Standard Time, am I talking about the American or Australian Eastern  Standard Time?
  >
  > And is Daylight Saving Time in effect or not?
  >
  > Okay, it’s tricky. But surely if we include the date and the exact city, then we'd be able to do the conversion reliably, right?
  >
  > What if the date and time are 1:30 am on Nov 1st, 2020, right when US DST ends and the clock moves backwards?
  >
  > 1:30am occurs twice that morning, how do you know which instance was intended?
  >
  > ![deja-vu](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\timezones\deja-vu.png)

- Your time zone library can recognize any time zone (you are using a library for this, right?)

  > Remember all those different potential time zone names and formats? Most libraries will only support one.
  >
  > And they might be limited by the time zones installed on your local machine.
  >
  > Yeah, really.
  >
  > Remember, if time zones can change based on the whims of a local government, then the library will need some external dataset to base its calculations  off of. That external dataset just might be the time zones installed on  your PC.

- The entire country always shifts during Daylight Saving Time

  > In the US, Arizona doesn't practice Daylight Saving Time
  >
  > ![arizona-dst](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\timezones\arizona-dst.png)

- The entire state always shifts during Daylight Saving Time

  > Within Arizona, the Navajo Nation happily follows Daylight Saving Time
  >
  > ![navajo-nation](C:\_School\Every Programmer Should Know\Introduction\Awesome Falsehood\img\timezones\navajo-nation.png)

- Other than DST, every city within a state follows the same time zone

  > In Indiana, USA, most cities follow Eastern Standard Time but a few decided to follow Central Standard Time

- Every city sits within exactly one time zone

  > A few times in history, state line or time zone lies got drawn  without paying attention to who actually lived on that border, cutting a city in half.  [There are a surprisingly large number of examples](https://www.quora.com/Are-there-any-major-cities-divided-by-two-time-zones).
  >
  > This enables some really unusual sleep schedules. It is also why GPS coordinates are more reliable than city names to determine the time zone

- There’s a designated time zone for every location in the world

  > The north and south poles have no official time zone. Researchers there just follow their own country's time.
  >
  > There's no way that could get confusing.

- This is a comprehensive list of misconceptions

  > These are the misconceptions I've uncovered so far, but I'm sure there  are many more waiting to be discovered. Heck, I didn't even realize UTC  offsets went all the way up to +14 until just 10 hours before I  published this list!

- Daylight Saving Time starts and stops exactly once each year.

  > When the month of Ramadan starts, some Muslim countries will exit DST  time, and then re-enter DST once Ramadan ends.  It makes sunset (the  time to end your fast) arrive faster (via [matthieum](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9wf8o3/?context=3))

- DST offsets are always exactly one hour: 

  > The Lord Howe island uses a 30 minute DST offset (via [paulrpg](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9qr08v/)), and England once had a 2 hour DST offset (via [bandwidthcrisis](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9rsvzq/))

- Standard Time is the same as Time Zone.

  > They're [different concepts](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9ql7cl/) (and apparently I've been using them wrong this whole article :P) (via [lpsmith](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9ql7cl/))

- Timezones are always offset from UTC by an integer number of quarter-hours.

  > Amsterdam was once at the UTC + 19 minute, 32.13 second offset. Most of the world simplified it to [UTC+0:20](https://en.wikipedia.org/wiki/UTC%2B00:20) (via [DJDavio](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9qwqp6/))

- Everyone follows their official time zone.

  > Some western parts of China have their own unofficial time zone (via [jl2352](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9r1wxz/?context=3)), and some industries independently decide to ignore DST to mitigate the timezone madness (via [bitchkat](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9relwp/))

- You can solve your problems by saving the time as UTC.

  > Saving future timestamps in UTC can [still lead to confusion](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9r90ni/?context=3) (via [AryA_ch](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9r90ni/?context=3))

- Birth dates tell you who is older

  > [Not necessarily](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9raph0/?context=3) (via [oshkarr](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9raph0/?context=3))

- There are exactly 195 countries in the world.

  > Not exactly time zones but another misconception (via [kankyo](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/g9qztxm/?context=3))

- If you have a UTC timestamp and the GPS coordinates, you can always determine the local time

  > Palestine and Israel have different time zones. So in the West Bank, the time zone [depends on if you're Palestinian or an Israeli settler](https://www.972mag.com/the-worlds-only-ethnic-time-zone/). If you don't know which person you're computing the time zone for, the local time is ambiguous (via [haxney](https://www.reddit.com/r/programming/comments/jggx3l/falsehoods_programmers_believe_about_time_zones/gam4vvs/))

- Historical UTC offsets for a region never change

  > The 1927 time zone shift for Shanghai [has been adjusted at least twice](https://stackoverflow.com/questions/6841333/why-is-subtracting-these-two-times-in-1927-giving-a-strange-result) since July 2011 (via [JoeIngeno](https://twitter.com/JoeIngeno/status/1323429822211756034))

- Daylight Saving Time is the only timezone adjustment

  > Sometimes countries instead move their clocks backwards in the Winter and call it [Winter Time](https://en.wikipedia.org/wiki/Winter_time_(clock_lag)) (via [Radek Zajic](https://twitter.com/zajdee/status/1325039075108265985?s=21)) 

## Falsehoods programmers believe about the calendar

- Days are 86,400 seconds long

  > False. Even if you live in a place that doesn’t have [Daylight Saving Time](https://en.wikipedia.org/wiki/Daylight_saving_time), you are still subject to rogue [leap seconds](https://en.wikipedia.org/wiki/Leap_second) that get inserted into our calendars every now and then. If you care  about being precise, you care about leap seconds. And if you’re writing  software for others to use, chances are at least one of your users will  be affected by DST at some point.

- Days are 24 hours long

  > False. Many places around the world observe Daylight Saving Time,  which means that people living in these locations will sometimes  experience 23 hour days (when they “leap forward”) and 25 hour days  (when they “leap back”).

- An hour will never occur twice in a single day

  > False. On days when we “leap back” for the Daylight Saving Time shift, one hour occurs *twice*. For example, in the United States, the hour that occurs twice is the 1  AM hour. This means that on these “fall back” days,  correctly-implemented clocks will go from 1:58 … 1:59 … 1:00 … 1:01 … …  1:59 … 2:00 … 2:01 …
  >
  > This leads to some interesting questions: If a user has set an alarm  to wake up at 1 AM on that day, what happens? Does the alarm go off the  hour after the midnight hour? Or does it go off during the hour before 2 AM? Or does it go off twice? Or do you just give up and not make the  alarm go off at all and make your users miss their dead-of-night  appointment?

- Every day has a midnight

  > False. Some countries, like  and [Iran](https://www.timeanddate.com/time/change/iran), perform their DST “leap forward” transition at midnight, which means  that 11:59 PM is followed by 1:00 AM. Other countries have historically  done the same, like [Romania until 1996](https://www.timeanddate.com/time/change/romania/bucharest?year=1996) and [Brazil until 2018](https://www.timeanddate.com/time/change/brazil?year=2018)
  >
  > So if you’re writing code and are trying to use the time `00:00:00` to represent “no time”, you will be wrong in these countries.

- Days start at midnight (or as close to it as possible)

  > Mostly true. For the sake of simplifying calculations and  establishing conventions, the day-to-day rollover happens at midnight.  However, the Hebrew calendar traditionally starts its days at sunset.

- Saturday and Sunday are the weekend

  > False. Most Muslim countries use either Thursday and Friday, or Friday and Saturday as their weekend.

- Weeks start on Sunday

  > False. Weeks start on Sunday in the United States, Monday in Europe, and a couple of places start on Saturday.

- Days in a work week are always contiguous

  > False. In Brunei, the work week is Monday - Thursday and Saturday.

- Everyone uses the Gregorian calendar

  > False. Many places in Africa use one of the various [Coptic calendars](https://en.wikipedia.org/wiki/Coptic_calendar). Israel uses the [Hebrew calendar](https://en.wikipedia.org/wiki/Hebrew_calendar) for determining holidays. The [Islamic calendar](https://en.wikipedia.org/wiki/Islamic_calendar) is used all through the Middle East and other predominantly Muslim  countries. Thailand uses the Buddhist calendar. Japan uses the [Japanese Imperial calendar](https://en.wikipedia.org/wiki/Japanese_calendar) for official state business.

- Months always have 30 or 31 days in them

  > False. February. Duh.

- OK… Months always have at least 28 days in them

  > False. The month [*Pi Kogi Enavot*](https://en.wikipedia.org/wiki/Intercalary_month_(Egypt)) in the [Coptic calendar](https://en.wikipedia.org/wiki/Coptic_calendar) only has 5 or 6 days in it (depending on the year).

- Month lengths follow regular cycles

  > Mostly true, but specifically false. Traditional [Islamic calendars](https://en.wikipedia.org/wiki/Islamic_calendar) base their months on local observations of the moon. Sighting the moon  determines whether the month will be 29 or 30 days long. However, since  you can’t know ahead of time if the moon will be visible (for example:  extreme cloud cover), it’s not always possible to know ahead of time how long the month will be.

- A week is always seven days

  > Currently true, but historically false. A couple of out-of-use calendars, like the [Decimal calendar](https://en.wikipedia.org/wiki/Decimal_time) and the [Egyptian calendar](https://en.wikipedia.org/wiki/Egyptian_calendar#Lunar_calendar) had weeks that were 7, 8, or even 10 days.

- The current year is 2020

  > False. It’s the year 5780 in the [Hebrew calendar](https://en.wikipedia.org/wiki/Hebrew_calendar).

- All the important years are four digits long

  > False. It’s the year Reiwa 1 in the [Japanese calendar](https://en.wikipedia.org/wiki/Japanese_calendar).

- In a range of hours, an hour will not be missing in the middle of it

  > False. When the “leap forward” transition happens for Daylight Saving Time, an hour is missing. In the US, this is the 2 AM hour, which means that time goes from 1:58 … 1:59 … 3:00 … 3:01 …

- In a range of days, a day will not be missing in the middle of it

  > False. In 1582, the transition from the Julian to Gregorian calendars meant that there was about a week and a half that was missing for  various locations around Europe. That same switch happened in the [United States in 1752](https://en.wikipedia.org/wiki/Adoption_of_the_Gregorian_calendar).
  >
  > Additionally, in 2011, Samoa decided to jump “ahead” a full day in  order to move to the west side of the International Date Line  (previously they were on the east). This resulted in December 30, 2011  being skipped on their calendars. So for residents of Samoa, December  29, 2011 was followed by December 31, 2011. The Marshall Islands made [the same move in 1993](http://www.nytimes.com/1993/08/22/world/in-marshall-islands-friday-is-followed-by-sunday.html).

- In a range of months, a month will not be missing in the middle of it

  > False. The [Hebrew calendar](https://en.wikipedia.org/wiki/Hebrew_calendar) uses leap months, which occur [during the middle of the year](https://en.wikipedia.org/wiki/Adar).

- A year is twelve months

  > False. Calendars like the [Hebrew](https://en.wikipedia.org/wiki/Hebrew_calendar) and [Coptic](https://en.wikipedia.org/wiki/Coptic_calendar) calendars deal with years that are 13 months long.

- A year is 365 (or 366) days

  > False. The [Islamic calendar](https://en.wikipedia.org/wiki/Islamic_calendar) is 354 (or 355) days long.

- A holiday will always occur in the same part of the solar year

  > False. Because the Islamic calendar is only 354 days long, holidays  drift by about 10 days each solar year. So after eighteen years, a  holiday that used to occur during the winter will be in the summer.

- Leap years occur every four years

  > False. The year 1900 was not a leap year.

- Leap years occur every four years except when the year is evenly divisible by 100

  >  False. The year 2000 *was* a leap year.

- Leap years occur every four years except when the year is evenly divisible by 100, unless it’s also evenly divisible by 400

  > False. The [Hebrew calendar](https://en.wikipedia.org/wiki/Hebrew_calendar), which is based almost entirely off the lunar cycle, inserts leap years [7 times in a 19 year period](https://en.wikipedia.org/wiki/Hebrew_calendar#Leap_years).

- The current year only changes at “New Years”

  > False. The current year of the [Japanese Imperial calendar](https://en.wikipedia.org/wiki/Japanese_calendar) is based on the reign of the current emperor. When the emperor dies (or abdicates), the next day is reset to the year 1 (of a new era).
  >
  > For example, the Emperor Shōwa (Hirohito) passed away on January 7,  Shōwa 64 (January 7, 1989). His son, Akihito, ascended to the throne the next day, which was the date January 8, Heisei 1.

- A year only has one “New Years”

  > False. In addition to the Japanese calendar having (potentially) an unbounded number of “New Years” in a single year, the [Hebrew calendar](https://en.wikipedia.org/wiki/Hebrew_calendar#New_year) historically celebrated up to *four* different New Years in a single year.

- A specific holiday on a specific calendar falls on the same date everywhere

  > False. The [Hebrew calendar](https://en.wikipedia.org/wiki/Yom_tov_sheni_shel_galuyot) adds extra days of observance to some holidays only outside of Israel. For example, the holiday of *Shavuot* is observed for one day in Israel, but for two days in the Diaspora. Similarly, the holiday of *Purim* is observed [on a different day in Jerusalem](https://en.wikipedia.org/wiki/Purim#Shushan_Purim).

- Nobody uses the Julian calendar anymore

  > False. The Julian calendar is still used by Eastern Orthodox churches and the Julian day is used in certain kinds of astronomical  calculations. There is a [village in Wales](https://en.wikipedia.org/wiki/Cwm_Gwaun) that still [celebrates New Year](https://en.wikipedia.org/wiki/Cwm_Gwaun#New_Year_celebrations) according to the Julian calendar on January 13.

- Timezones always are on the hour mark

  > False. Many places have half-hour offsets, such as French Polynesia,  Newfoundland and Labrador, Iran, Afghanistan, India, Sri Lanka, Myanmar, the Cocos Islands, North Korea, and parts of Australia.

- OK… Timezones are always on the *half* hour mark

  > False. There are a few places that have an offset of :15 or :45  minutes, such as Nepal, part of Western Australia, and the Chatham  Islands.

- *Fine*… Timezones are always on the *quarter* hour mark

  > Currently true, but historically false. Before the advent of global  communications and standardized time keeping, the current time was  pretty much up to the local administrators. When regions were brought in line with the international time keeping standards, they’d have to do  some shifts to accomplish that, like Shanghai’s weird 343 second shift  in the early 1900s. For more examples, Liberia was [44 minutes behind UTC](https://en.wikipedia.org/wiki/UTC−00:44) up until 1972, and from 1880 to 1916, Ireland was [25 minutes and 21 seconds behind UTC](https://en.wikipedia.org/wiki/UTC-00:25:21).

- No place is ever more than 12 hours away from UTC

  > False. Parts of [Oceania](https://en.wikipedia.org/wiki/Oceania) are 12:45, 13:00, and 14:00 hours ahead of UTC.

- No location will ever change what time zone it’s in

  > False. As mentioned above, Samoa did just that in 2011. Cancún [switched timezones in 2015](http://abcnews.go.com/Travel/cancun-change-eastern-standard-time/story?id=28589197), as did [Turks & Caicos](http://www.huffingtonpost.com/2015/03/09/turks-and-caicos-time-zone_n_6832054.html).

- We’re done adding time zones

  > False. The `Asia/Tomsk` timezone [was created in 2016](http://linuxsoft.cern.ch/cern/slc57/i386/yum/updates/repoview/tzdata.html) for parts of eastern Russia.

- Time zones do not change their offset from UTC

  > False. [Eight different time zones changed their UTC offset](http://linuxsoft.cern.ch/cern/slc57/i386/yum/updates/repoview/tzdata.html) in 2016.

- The UNIX epoch is January 1, 1970

  > False. The UNIX epoch is January 1, 1970 in UTC, but is Dec 31, 1969 in Los Angeles.

- Daylight Saving Time rules do not change

  > False. They change all the time. In 2016, there were [nine different DST changes](http://linuxsoft.cern.ch/cern/slc57/i386/yum/updates/repoview/tzdata.html).

- Daylight Saving Time rules do not change on short notice

  > False. In 2016, Egypt decided to re-instate DST in June, and then reversed that decision three weeks later, [three days before the shift was supposed to happen](https://www.washingtonpost.com/news/worldviews/wp/2016/07/06/egypt-cancelled-daylight-savings-time-three-days-before-it-was-due-to-start/).

- Days don’t last longer than 25 hours

  > False. Because of time zone offsets, a single calendar day typically  lasts 50 hours. Or in other words, if you choose a date on the calendar, then there is a 50 hour window where at least some point on the earth  thinks it is that day. The day “starts” in the UTC+14 timezone and  continues for 14 hours until UTC+0 catches up to that calendar date.  That date then continues for 24 hours, at which point UTC+0 transitions *out* of that timezone, but the other timezones behind UTC are still catching up, all the way to UTC-12.

- It is normal that the Sept-, Oct-, Nov-, and Dec- months are numbered 9, 10, 11, and 12

  > False. This is very weird. They used to be months 7, 8, 9, and 10, but some [reform to the Roman calendar](https://en.wikipedia.org/wiki/Roman_calendar#Calendar_of_Numa) back in the day resulted in the creation of January and February, which messed everything up.

- Everything you know about calendars is applicable to space travel

  > False. There are many weird things about calendars and space travel.  Days are longer, days are shorter, time flows faster, time flows slower, days are longer than years, etc etc.

- “Calendrical” isn’t a real word

  > [False](https://www.merriam-webster.com/dictionary/calendrical).

- This is all really complicated

  > True!

- I never want to write code that handles all of this

  > True! You should always use the Date and Time Services provided by the [ICU Project](https://unicode-org.github.io/icu/userguide/datetime/). If you’re an iOS/macOS developer, then you should always stick to `NSCalendar` and its cohorts, which are all built on top of the ICU libraries.