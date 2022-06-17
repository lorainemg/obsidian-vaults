# Falsehoods Programmers Believe About Names
Creado: 2022-06-16 23:18
Tags: #every-programmer-should-know, #falsehoods, #human-identity, #names
Topic: [[Falsehoods Programmers Believe About Human Identity]]

----

## Falsehoods Programmers Believe About Names

- People have exactly one canonical full name.

  > It seems some people believe that you get a name and it never changes.  Not so, even in Western countries, where a person may change their name  when they marry. In Catholic tradition a person may get a middle name at time of confirmation.

- People have exactly one full name which they go by.

  > The author known most often as John Wyndham (author of *The Day of the Triffids*) bore the name John Wyndham Parkes Lucas Beynon Harris, and published  books under the names John Beynon and Lucas Parkes, as well as John  Wyndham.

- People have, at this point in time, exactly one canonical full name.

  > A performer may have a stage name, completely separate from the name on  their birth and marriage certificates – they may even have a passport in their stage name.

- People have, at this point in time, one full name which they go by.

  > Not so, even in Western countries, where a woman may choose to retain  her unmarried name at work (where she is already known by that name),  and use her husband’s surname on social occasions, and even on legal  documents such as mortgages and loans.

- People have exactly N names, for any value of N.

  > An English name may traditionally consider of two given names (often  called a first name and a middle name) and a surname, but that’s not  required. A person may have no middle name, or may have several. A  Portuguese name, for example, may have one or two given names, and up to four surnames (up to six in the case of a married woman), and those  surnames may be phrases, such as da Silva or dos Santos, or even Costa e Silva).

- People’s names fit within a certain defined amount of space.

  > The renowned painter, best known simply as Picasso, had the full name  “Pablo Diego José Francisco de Paula Juan Nepomuceno María de los  Remedios Cipriano de la Santísima Trinidad Ruiz y Picasso”. Try fitting  that name into a form which allows 30 characters for a name…

- People’s names do not change.

  > Given that we have already mentioned a person changing his or her name  at the time they marry, this is clearly false. Moreover, Catholics may  adopt an extra middle name at the time of their confirmation. It’s also  common for a person to add a name, or change their name entirely, when  converting to another religion – consider Cat Stevens becoming Yusuf  Islam or Cassius Clay becoming Muhammed Ali when converting to Islam.

- People’s names change, but only at a certain enumerated set of events.

  > It was common, for some people in Thailand to change names to avert bad  luck. That might happen without a recognized event. Sometimes a person  will change their name when someone else with the same name becomes  famous, or infamous – a notable example was people changing their  surname from Hitler.

- People’s names are written in ASCII.

  > Patently false, if we consider that ASCII does not include the accented  characters which appear in French and Portuguese names. Nor does it  include the Greek alphabet used in Greek names, Cyrillic characters for  Russian names. Then there are scripts like Devanagari for Indian names,  Chinese characters (hanzi) and Japanese characters (Kanji), and many  more.

- People’s names are written in any single character set.

  > People have names that mix, for example, Kanji and Latin, or Hanzi and  Latin, or Hangul and Latin characters. In many cases this is because  they have a “Western given name” to cater for those of us unable to  pronounce the given name in their native language.

- People’s names are all mapped in Unicode code points.

  > The Unicode code standards team continue to add code points to the  standard to accommodate rarer and rarer characters, and the vast  majority of names are already covered, but there are still exceptions,  such as the symbol that “the artist formerly known as Prince” adopted.  Even if we eliminate such curiosities, there are (a few) alphabets which are not yet covered by Unicode (perhaps the most realistic example is  Aymara, a script for a language spoken by well over a million people in  South America; less realistic is Klingon, or the character sets invented by J R R Tolkien for his Middle Earth). Moreover, Unicode only includes a subset of Chinese and Japanese characters, and some of the omitted  characters are used in names.
  >  To complicate matters further, there are languages which do not have  associated scripts – they cannot be written down. There are no Unicode  code points for such languages. Names in those languages might be  captured in phonetic symbols, but that’s not particularly helpful,  because the majority of people are unfamiliar with the phonetic  alphabet.

- People’s names are case sensitive.

  > Many character sets are not case sensitive – Chinese and Japanese, for  example – uppercase / lowercase is an idea that is simply not  applicable.

- People’s names are case insensitive.

  > Some character sets *are* case sensitive – Latin, for example.  More importantly, there are character sets where characters may be  accented in lower case, but not in upper case, so it is not possible to  provide a “round trip” from lower case to upper case and back to lower  case.
  >  Correct capitalization can be very important to some people, such as the owners of the surnames Mackenzie and MacKenzie.
  >  The correct use of case is also important with surnames such as van  Gogh, du Barry, da Costa, O’Brien, and D’Agostino, and given names like  Jean-Pierre.

- People’s names sometimes have prefixes or suffixes, but you can safely ignore those.

  > Nothing could be further from the truth. The Dutch name Pieter van der  Meer is not the same as Pieter Meer, even though “van der” is a prefix.
  >  You might consider Junior to be a suffix in Robert Downey Junior, but if you omit it, you are referring to his father, not to him.
  >  In Arabic names, the suffix al-Din means “of the faith” or “of the  religion” – names such as Taj al-Din (“crown of the faith”) or Saif  al-Din (“sword of the religion”) are not the same name when the suffix  is suppressed. An Italian name such as di Stefano is not the same as  Stefano.
  >  A Spanish woman with the surname “viuda de de la Cruz” is the widow of a man with the patronym “de la Cruz”. Omitting those prefixes changes the meaning of the name.

- People’s names do not contain numbers.

  > Even if we ignore the cases where the number is a generation (Thurston  Howell III, for example), there are cases where a number is part of  someone’s legal name. Jennifer 8 Lee chose to give herself the middle  name of 8 because 8 is associated with good fortune.

- People’s names are not written in ALL CAPS.

  > In some countries (notably French speaking) it is convention to write a  person’s surname in all caps to make it clear which part of the name is  the surname. This convention has solidified to the point that rendering  their surname not in all caps may be regarded as impolite.

- People’s names are not written in all lower case letters.

  > e e cummings preferred his name written in all lower case. So does k d  lang. It’s polite to follow the pattern used by the name’s owner.
  >  There is an Irish / British surname ffrench which is conventionally  written in all lower case, although that tradition is suffering from  poorly designed software which insists on capitalizing it.

- People’s names have an order to them. Picking any ordering scheme will automatically result in consistent ordering among all systems, as  long as both use the same ordering scheme for the same name.

  > In the Netherlands, Vincent van Gogh would be indexed and sorted under  G, for Gogh; in Belgium the same name would be indexed under V, for van  Gogh. It’s not possible to adopt a single ordering for names which will  yield a universally accepted order. The system used by many libraries is to apply the rule appropriate to the place of birth of the person in  question (not a rule I’d want to try to apply in software).

- People’s first names and last names are, by necessity, different.

  > An Australian businessman and politician called Benjamin Benjamin died  in 1905. Jerome K Jerome was an English humorous writer best known for *Three Men in a Boat*. Owen Owen was a Welshman who founded Owen Owen Ltd, operating a chain  of department stores. And let’s not even get started on the wrestlers  and actors who adopted repeated names for stage purposes.

- People have last names, family names, or anything else which is shared by folks recognized as their relatives.

  > In Java it was common for a person to be given a single name, and not to have a surname. The Indonesian presidents Suharto and Sukarno both had  no surname, for example.

- People’s names are globally unique.

  > Tell that to anyone named John Smith! I have a somewhat less common  name, yet I discovered a person with the same name working in the same  industry in the same country (Australia).

- People’s names are *almost* globally unique.

  > Even with the tendency to use unusual spellings of names, it’s extremely common to find people who share a full name – try Googling your own  name.

- Alright alright but surely people’s names are diverse enough such that no million people share the same name.

  > The Chinese name Zhang Wei is reported to be shared by over a quarter of a million people.
  >  If we limit the question to surnames, about 20% of the population of  South Korea have the surname Kim. About 10% of the population of  northern China share the surname Wang, while more than 10% of the  population of southern China share the surname Chen. Li comes next in  both northern and southern China, making it the most common surname  across the country. And nearly 40% of Vietnamese have the surname  Nguyen.
  >  Names are far from unique.

- My system will never have to deal with names from China.

  > Migration has spread names from every culture to (almost) every country. The days when immigrants were renamed on entry to a country have  passed, mostly (for example, Vietnam still requires that an applicant  for citizenship takes a Vietnamese name). It is unrealistic to expect to avoid names from other countries, although you may see them in a  transliterated form.
  >  So a Chinese name like [周](https://en.wiktionary.org/wiki/周)[潤](https://en.wiktionary.org/wiki/潤)[發](https://en.wiktionary.org/wiki/發) may appear in your system as Chow Yun-fat, or Chow Yun Fat, or even Yun Fat Chow (Chow is his surname).

- Or Japan.

  > see above.

- Or Korea.

  > see above.

- Or Ireland, the United Kingdom, the United States, Spain, Mexico,  Brazil, Peru, Russia, Sweden, Botswana, South Africa, Trinidad, Haiti,  France, or the Klingon Empire, all of which have “weird” naming schemes  in common use.

  > see above.

- That Klingon Empire thing was a joke, right?

  > It’s difficult to find examples of people using Klingon names as their  official names, but should we stop someone doing so? Once we can handle  the things required for other cultures (such as the embedded apostrophe  for “O’Brien”), we can support Klingon names without extra work.

- Confound your cultural relativism! People ***in my society\***, at least, agree on one commonly accepted standard for names.

  > And will your software only be dealing with people named by your society?

- There exists an algorithm which transforms names and can be  reversed losslessly.  (Yes, yes, you can do it if your algorithm returns the input.  You get a gold star.)

  > There is no algorithm (short of remembering the original format) which can transform a name in a guaranteed reversible way.

- I can safely assume that this dictionary of bad words contains no people’s names in it.

  > This is a common mistake – many “bad words” are not bad words in other  languages, and some are used in names. Moreover, not every society  restricts what words may be used in a name; it’s perfectly possible that someone’s name may have been established in such a jurisdiction.

- People’s names are assigned at birth.

  > Births are recorded in most countries, but the effectiveness of the system varies.
  >  The exact rules vary by jurisdiction, but all allow for some delay in  registering a birth. The length of the allowed delay varies from at  least as short as 3 weeks (Scotland) to at least 2 months (Australia),  and there is provision for registering births later.
  >  The child’s name may be recorded at the time that the birth is  registered, but it doesn’t always happen (birth registrations with a  name like “Baby Boy” or “Baby Girl” still happen, when the parents have  trouble choosing a name, or the child is a foundling, for example).

- OK, maybe not at birth, but at least pretty close to birth.

- Alright, alright, within a year or so of birth.

- Five years?

- You’re kidding me, right?

  > There are cultures where a person’s adult name is not chosen until  puberty. Prior to this the child may have a “milk name”, or a temporary  name.

- Two different systems containing data about the same person will use the same name for that person.

  > If this were true, then there would be no market for software which reconciles different databases.
  >  In my own case, some systems contain my formal name, including my middle name. Others have just my first given name and surname, or my nickname  and surname. And I’m a simple case. My wife was in some systems with her maiden name, in others with her married name, with or without her  middle name, with her full first given name or with either of two  spellings of her nickname.

- Two different data entry operators, given a person’s name, will by necessity enter bitwise equivalent strings on any single system, if the system is well-designed.

  > Imagine what happens when a name is entered by a person hearing it over  the telephone. Consider cases like Thomson and Thompson; or Johnson,  Johnston, Johnstone, and Jonsson.

- People whose names break my system are weird outliers. They should have had solid, acceptable names, like 田中太郎.

  > No, your system is badly designed.
  >  This particular example name is perhaps best known as the name of an  alien in an anime series (and a manga). There have also been real people with this name.

- People have names.

  > This one is perhaps the most difficult for which to give solid examples. There was an isolated culture in which no one had names – they referred to everyone in relative terms, such as “my mother’s eldest sister”.


## Referencias