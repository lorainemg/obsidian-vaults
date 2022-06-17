# Falsehoods Programmers Believe About Software Engineering

## Falsehoods Programmers Believe About Versions

- versions always increase
- versions are numbers
- versions are strings
- versions are semantic
- versions are decimals
- a major number of 1 or above means stable api
- versions with the same major number will have the same api
- versions have numbers, periods, and maybe a preceding v
- semantic is always the best way to go
- versions are consistent within a project
- semantic versions will never see double digits or triple digits within dots
- at least if you're using a semantic version people can compare it correctly
- versions will be consistent amongst projects in a given language or community
- semantic versioning cannot be represented as number or decimal
- as long as the versions increase the length of the version doesn't matter
- if versions have the same number they are equivalent
- in a given archive all code will have the same version
- semantic versions can only have 3 positions
- dates are bad for versions
- versions always increase by exactly one
- the least significant digit, character or group is the last one
- version numbers convey no runtime information
- over-the-wire and human-readable versions are fully convertible back and forth without any loss of information
- "10" is not a valid single digit
- Latest is always set to the latest semantic versioning

## Falsehoods Programmers Believe About Build Systems

- Build graphs are trees.
- Build graphs are acyclic.
- Every build step updates at most one file.
- Every build step updates at least one file.
- Compilers will always modify the timestamps on every file they are expected to output.
- It's possible to tell the compiler which file to write its output to.
- It's possible to tell the compiler which directory to write its output to.
- It's possible to predict in advance which files the compiler will update.
- It's possible to narrow down the set of possibly-updated files to a small hand-enumerated set.
- It's possible to determine the dependencies of a target without building it.
- Targets do not depend on the rules used to build them.
- Targets depend on every rule in the whole build system.
- Detecting changes via file hashes is always the right thing.
- Detecting changes via file hashes is never the right thing.
- Nobody will ever want to rebuild a subset of the available dirty targets.
- People will only want to build software on Linux.
- People will only want to build software on a Unix derivative.
- Nobody will want to build software on Windows.
- People will only want to build software on Windows.
  (Thanks to David MacIver for spotting this omission.)
- Nobody will want to build on a system without `strace` or some equivalent.
- `stat` is slow on modern filesystems.
- Non-experts can reliably write portable shell script.
- Your build tool is a great opportunity to invent a whole new language.
- Said language does not need to be a full-featured programming language.
- In particular, said language does not need a module system more sophisticated than `#include`.
- Said language should be based on textual expansion.
- Adding an Nth layer of textual expansion will fix the problems of the preceding N-1 layers.
- Single-character magic variables are a good idea in a language that most programmers will rarely use.
- System libraries and globally-installed tools never change.
- Version numbers of system libraries and globally-installed tools only ever increase.
- It's totally OK to spend over four hours calculating how much of a 25-minute build you should do.
- All the code you will ever need to compile is written in precisely one language.
- Everything lives in a single repository.
- Files only ever get updated with timestamps by a single machine.
- Version control systems will always update the timestamp on a file.
- Version control systems will never update the timestamp on a file.
- Version control systems will never change the time to one earlier than the previous timestamp.
- Programmers don't want a system for writing build scripts; they want a system for writing systems that write build scripts.

## Falsehoods Programmers Believe about REST APIs

### Documentation

- Common features of our public application will be available in the API.
- The person implementing a client is already an expert user of our application.
- Okay, the implementor knows *something* about our application.
- Okay, the implementor has at least *heard of* our application.
- Okay, the implementor at least knows something about the problems solved by  our application.
- Any jargon on our user-facing application is the same as terminology for the  same concepts in our API. (counterexample?)
- API documentation will have a glossary of the application jargon used.
- If the documentation says that legal values for POSTing to resource B can be  found by GET to resource A, then all returned values from A will work with B.
- Documentation of old versions of the system will be preserved.
- If there are similar-sounding concepts in the system, the differences will be  well explained somewhere. We wouldn't have all of "tags" and "topics" and  "terms" and leave you to guess what they mean.

### Errors

- Successful status is always 200.
- Successful status is always one of the documented statuses.
- A 20x response indicates success.
- An API that is documented as returning errors in JSON format will always  return a parseable JSON error response.
- If there are rate limits, the rate limit error message format will be  documented.
- For that matter, all error codes emitted by the system will be documented.

### Least Surprise

- A resource which accepts a POST request and whose path ends in .json expects a  JSON-encoded body.  Obviously.
- Auth will be done by some common standard such as OAuth.
- If it's oauth, and I use a commonly available third-party oauth library, and  authentication works, it won't just stop working one day.
- If the documentation says you can upload a 3 MB PNG image, then you can  expect PNG images under 3 MB won't cause 500 errors.

### Moving Fast and Breaking Stuff

- Breaking changes will be confined to explicit versions of the API.
- There will *be* explicit versions of the API.
- Features won't just disappear from version N when version N+1 is released.
- Backwards incompatible changes will be announced long before they are  deployed.
- Well, at least more than a week before.
- Okay, at least there will be some documentation that a breaking change  occurred sometime *after* deploying the changes. We wouldn't just update the  docs and pretend the old spec never existed.
- If there *is* an announcement of breaking changes, then only the announced  things will break.
- If there *is* an announcement of breaking changes, it will explicitly call  out the changes. changed. It won't just be a dump of the entire new  documentation.
- Okay, if the announcement *is* just a dump of the entire new documentation,  it will at least be in a text format that you can run diffs against.
- Okay, if the announcement *is* just a dump in some binary format, it will at  least be in a format that you can copy/paste text out of to generate some  diffs. We wouldn't use some weird PDF generator that inserts bizarro  invisible whitespace between random characters within words.

### Bug Reports

- If you file a bug report and get an official response acknowledging it's a  bug, it will get fixed eventually.
- If you file a bug report and get an official response acknowledging it's a  bug, and we say we're removing the feature from the next version instead of  fixing it, then at least we'll update the docs for the old API version  to reflect the breaking change.
- There will be somewhere to report bugs.

### Catch-22

- If a client application requires approval to use some restricted or paid  features, it will be possible to get that approval without putting the client  into production.

## Falsehoods Programmers Believe About CSVs

- All CSVs are ASCII
- All CSVs are Win1252
- All CSVs are in 8-bit encodings
- All CSVs are UTF-8
- All CSVs are UTF-16
- All CSVs contains a single consistent encoding
- All records contain a single consistent encoding
- All fields contain a single consistent encoding
- All CSVs contain records
- All records contain fields 
- Fields never contain record separators 
- Fields never contain delimiters 
- Fields never contain control characters
- Delimiters are escaped with a `\`
- All fields are enclosed by double quotes
- All records are a single line
- All lines contain a single record
- All records contain the same number of fields
- All records contain the same number of fields as the header
- All records contain the same number of fields or fewer than the header
- All CSVs contain a header
- All record separators are CRLF
- All record separators are LF
- All record separators are a single byte
- All record separators are a single rune
- All newlines are a single byte
- All CSVs are delimited with a comma
- All CSVs are delimited with a comma, tab or semicolon
- TSV isn't CSV
- All delimiters are a single byte
- All commas are a single byte
- All CSVs are readable with Excel
- Excel is a good tool for working with CSVs
- Excel is an OK tool for working with CSVs
- Excel can losslessly save CSVs it opens
- Using `="{value}"` is a *good* way to get around Excel auto-formatting
- The first line will never be a poorly supported instruction header
- Using `sep={char}` is a *good* way to get Excel to accept your delimiter
- Prepending a BOM is a good way to get Excel to read your encoding
- You can safely name your first column "ID"
- All CSVs follow [RFC4180](https://tools.ietf.org/html/rfc4180)
- Most CSVs follow [RFC4180](https://tools.ietf.org/html/rfc4180)
- All CSVs follow the same defined standard
- All CSVs follow a defined standard
- All CSVs have a `.csv` extension
- All CSV is human readable

## Falsehoods Programmers Believe About Package Managers

### Packages

1. A package has a name.
2. A package has only one name (see [#26](https://github.com/kdeldycke/meta-package-manager/issues/26)).
3. A package name is unique.
4. Package [names are composed of ASCII characters](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/homebrew.py#L205-L206).
5. A package name is the same as its ID (see [#11](https://github.com/kdeldycke/meta-package-manager/issues/11)).
6. There is only one way to install a package.
7. Only one version of a package is available on a system.
8. Package [upgrades can be automated](https://en.wikipedia.org/wiki/Dependency_hell).
9. All [packages have a version](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/mas.py#L71-L75).
10. [Versionned packages are immutable](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/homebrew.py#L230-L231).
11. Packages can’t upgrade themselves.
12. A package can be reinstalled.

### Package managers

1. Package managers provides the latest version of packages.
2. Package managers provides clean packages.
3. Package managers provides stable softwares.
4. Only [one instance of a package manager exist on the system](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/gem.py#L47-L51).
5. You can downgrade packages.
6. A package manager [can update itself](https://twitter.com/kdeldycke/status/772832404960636928).
7. A package is found under the same name in different package managers.
8. Package managers [can resolve dependencies](https://github.com/pypa/pip/issues/988).
9. All dependencies are provided by the package manager.
10. Package managers have a CLI.
11. Package managers behave the same across OSes and distributions.
12. Package managers [tracks installed versions](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/homebrew.py#L219-L221).
13. Package managers [can track removed packages](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/homebrew.py#L239-L242) (see [#17](https://github.com/kdeldycke/meta-package-manager/issues/17)).
14. Package managers are documented.
15. A package manager has a version.
16. A package manager check package integrity.
17. Package managers are secure.
18. Package managers can be unittested.
19. Package managers [can upgrade all outdated packages](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/pip.py#L94-L97).
20. Package managers are forbidden to upgrade other package managers.
21. Packages are only managed by one package manager.
22. Installing a package doesn’t require a reboot.
23. Package manager [output is consistent](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/mas.py#L42-L44).
24. A package manager can upgrade a package installed by the user.
25. All [users on the system have access to the package manager](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/gem.py#L95-L100).
26. Package managers do not remove user data.
27. Package managers [can bootstrap themselves](https://github.com/Homebrew/brew/blob/master/docs/Common-Issues.md#brew-complains-about-absence-of-command-line-tools).
28. Package managers supports multiple architectures.
29. You [only need one package manager](https://utcc.utoronto.ca/~cks/space/blog/tech/PackageManagersTwoTypes).

### Meta

- Implementing a meta package manager [is not a futile pursuit](https://xkcd.com/1654/).

## Falsehoods Programmers Believe About Search

- Search engines work like databases
- Search can be considered an additional feature just like any other
- Search can be added as a well performing feature to your existing product quickly
- Search can be added as a well performing feature to your existing product with reasonable effort
- Choosing the correct search engine is easy and you will always be happy with your decision
- Once setup, search will work the same way forever
- Once setup, search will work the same way for a while
- Once setup, search will work the same way for the next week
- The default search engine settings will deliver a good search experience
- Customers know what they are looking for
- Customers who know what they are looking for will search for it in the way you expect
- Customers who don’t know what they are looking for will search accordingly
- A customer using the same query twice expects the same results for both searches
- Customers only search for a few terms
- Customers only search for less than some set number of terms
- Customers never copy and paste a whole document into a search bar
- Customers balance quotes and parenthesis
- Customers that don’t balance quotes or parenthesis don’t expect phrasing or grouping
- You can pass the customer query directly into your search engine
- You can write a query parser that will always parse the query successfully
- You will never have to return a query parse error to the customer
- When you find the boolean operator ‘OR’, you always know it doesn’t mean Oregon
- Customers notice their own misspellings
- Customers don’t expect your search to correct misspellings
- It is possible to create a list of all misspellings
- It is possible to create an algorithm to handle all misspellings
- A misspelled word is never the same as another correctly spelled word
- All customers expect spelling correction to work the same
- All customers want their misspellings corrected
- A search should always return results, no matter how absurd
- If you don’t have any results to show, customers won’t mind
- When the perfect results are shown to the customer, they will notice it
- You don’t need to monitor search queries, results, and clicks
- Customers won’t get nervous that you are logging their search activity
- Search queries are not affected by GDPR
- Looking at the data, it is always possible to tell whether a customer found what they were looking for
- Customers will click on what they are looking for when they’ve found it
- You can build a search that works like Google
- You can build a search that works like Google sometimes
- You should use Google as a target for your search
- Customers don’t mind if your search doesn’t work like Google
- Customers don’t expect your search to work like Google
- Customers won’t compare you to Google
- A bad search, no matter how minor nor how rare, will never reflect poorly on your product
- Since Google doesn’t use facets, customers don’t need them
- Facet hit counts are always correct
- Facets have no impact on performance
- You can just cache queries to get performant facets
- Personalized search is easy
- Learning to rank is easy and just requires a plugin
- You have enough data for learning-to-rank
- Over time, you can curate enough data for learning-to-rank
- You don’t need to spend lots of time formatting content for it to work well in your search engine
- Text extraction engines will always produce text that doesn’t need to be post-processed
- All your markup will be stripped as you expect it to be
- Content is well formed
- Content is mostly well formed
- Content is predictably well formed
- Content, sourced from a database and templates, are formed the same
- Content teams treat search as their top priority
- Manually changing content to improve search is easy
- Improving content can be automated with reasonable effort
- Queries for ‘C programming’ and ‘C++ programming’ will produce different results
- Queries for ‘401k’ and ‘401(k)’ will produce the same results
- Tokenization as it works out of the box is right for your content and queries
- Tokenization can be changed to meet the needs of your entire corpus and all queries
- Tokenization can be changed to meet the needs of most of your corpus and most queries
- Tokenization can be conditional
- You should roll your own tokenizer
- You will never have a debate about tokenization
- Regular Expressions for tokenization is a good idea
- Regular Expressions have minimal performance impact
- You will never have a debate about regular expressions
- You should remove stop words
- You should not remove stop words
- You know what the list of stop words should be
- Stop words will never change
- When you find the stopword ‘in’, you know it doesn’t mean Indiana
- It’s easy to make certain things case sensitive
- Case sensitivity is a good idea
- Synonyms are easy
- Synonyms will improve recall in the way you want
- Synonyms have the same relevance in all documents
- Synonyms for Abbreviations and Acronyms always work as you expect
- Synonyms can be extracted from your corpus with natural language processing
- Using Word2Vec for synonyms is a good idea
- Stemming will solve your recall problems
- Lemmatization will solve your recall problems
- Lemmatization dictionaries are static
- Languages don’t change
- Natural language processing (NLP) tools work perfectly
- Incorporating NLP into your analysis pipeline is straightforward
- Search queries are complete sentences and can be accurately tagged with parts of speech
- Showing a list of search suggestions is easy
- Suggestions should just use the out of the box search engine suggestions
- Suggestions should incorporate customer query logs
- Customers would never type anything offensive into your search bar
- Customers would never try to hack you through your search bar
- Customers don’t need highlighting to find what they’ve searched for
- Default highlighters are good enough for all your content and queries
- Making a custom highlighter isn’t too difficult. It’s just matching strings right?
- Making a custom highlighter that is better than the default version will take less than a year
- Turning on caching will solve your performance issues
- Customers don’t expect near real time updates
- 30 second commit time is short enough for everyone

## Falsehoods Programmers Believe About Bitcoin

### Blocks

1. **Block height will only increase.**

   Not the chain with the highest number of blocks is considered as the majority chain (honest chain), but the chain with the most cumulated [*chainwork*](https://github.com/bitcoin/bitcoin/blob/df536883d263781c2abe944afc85f681cda635ed/src/chain.h#L162). As the work needed to find a valid block proof is dependent on the block [target](https://en.bitcoin.it/wiki/Target) (see also [difficulty](https://en.bitcoin.it/wiki/Difficulty)), it is possible that a chain with a higher number of blocks than the majority chain exists, if the difficulty was lower in this chain. If a client for some reason first only sees the minority chain (with higher block count) and then gets presented the majority chain (with a higher chainwork) it will drop the minority chain in favor of the majority chain. In this case the valid block height (as seen by this node) might actually decrease.

   It is a very difficult exercise to even imagine a scenario of how this could happen.

   *Thought experiment*: Suppose a miner with massive  hash power outperforming the majority chain, but not publicly announcing the blocks. After 2016 blocks a difficulty adjustment takes place and the difficulty on the hidden chain increases by a lot. All blocks mined now on the hidden chain contain more chainwork than  corresponding blocks on the public chain. The miner produces a few more blocks, stops mining and waits for the  other chain to catch up to his blocksize + 1 and then announces his  blocks. All nodes will follow the chain with lesser blockheight because it  includes more chainwork.

   It is left as an exercise for the reader to imagine how likely the occurrence of this case may be.

   A curious situation that impacted applications relying on a constantly increasing block height is the [March 2013 Chain Fork](https://github.com/theborakompanioni/bitcoin-spring-boot-starter/blob/master/docs/FALSEHOODS.md#Bitcoin-never-had-a-double-spend). If you can come up with an additional scenario, please - for the sake of Satoshi - create a PR!

2. **Block time will only increase.**

   No. That's not how time works in Bitcoin. A block does not necessarily have to have a higher timestamp than its predecessor. The network has no physical connection to the real world - so how does it know what time it is? The only way for Bitcoin to know is by integrating a concept of time in the consensus rules.

   Clocks are imprecise and [time is a difficult concept](https://github.com/kdeldycke/awesome-falsehood#dates-and-time). There is no single source of truth. It is even stated in the comment of function [`GetTimeOffset()`](https://github.com/bitcoin/bitcoin/blob/ad90dd9f313aa4a2f87675b4392b85c0b06a5a83/src/timedata.cpp#L21-L32):

   > Never go to sea with two chronometers; take one or three.

   A beautiful explanation on why this has no negative impact on the proper functioning of the network has been described by [dergigi](https://dergigi.com):

   > For Bitcoin, the fact that our human timestamps are  imprecise doesn’t matter too much. It also doesn’t matter that we have  no absolute reference frame in the first place. They only have to be  precise enough to calculate a somewhat reliable average across 2016  blocks. To guarantee that, a block’s "meatspace" timestamp is only  accepted if it fulfills two criteria:
   >
   > 1. The timestamp has to be greater than the median timestamp of the previous 11 blocks.
   > 2. The timestamp has to be less than the network-adjusted time plus two hours. (The “network-adjusted time” is simply the median of the  timestamps returned by all nodes connected to you.)

   The whole article ["Bitcoin is Time"](https://dergigi.com/2021/01/14/bitcoin-is-time/) by dergigi is well worth reading.

   It is these rules that allow a block with a lower timestamp than its predecessor to be considered valid.

   However, if a block violates these rules either `"time-too-old: block's timestamp is too early"` or `"time-too-new: block timestamp too far in the future"` validation errors in [`ContextualCheckBlockHeader()`](https://github.com/bitcoin/bitcoin/blob/a12962ca894075ae203ab808db4ba5dab23346d1/src/validation.cpp#L3361-L3367) will keep it from being accepted.

   Bitcoin has three sources of time:

   - System clock
   - Median of other nodes clocks (see [`GetMedianTimePast()`](https://github.com/bitcoin/bitcoin/blob/92fee79dab384acea47bf20741a9847a58253330/src/chain.h#L270-L284))
   - The user (asking the user to fix the system clock if the first two disagree)

3. **When a miner finds a valid block, it is guaranteed to be included in the blockchain.**

4. **Okay, but when a miner finds a valid block single-handedly, it is guaranteed to be included in the blockchain.**

   Not if the block's hash [collides with the hash of an earlier block](https://bitcoin.stackexchange.com/a/38385). As the [inventory vector](https://en.bitcoin.it/wiki/Protocol_documentation#Inventory_Vectors) of the described new block would be a duplicate of an already known block, no other node  would request this block. It would just be ignored, as if never discovered in the first place. Everybody would be  convinced that no new block has been found at that height yet.

5. **Each block always generates `${CURRENT_BLOCKREWARD}` amount of new Bitcoin.**

   In [block 124724](https://blockchair.com/bitcoin/block/124724) the coinbase transaction is missing one Satoshi. [Block 501726](https://blockchair.com/bitcoin/block/501726) is even missing the whole block reward.

6. **The more leading `0`'s a block hash has (i.e. the lower the hash is), the more does the block contribute to total chainwork.**

   It's a common misbelief that blocks with a lower block hash (i.e. more leading zeros) contribute more to the cumulated [chainwork](https://github.com/bitcoin/bitcoin/blob/df536883d263781c2abe944afc85f681cda635ed/src/chain.h#L162) than a block with a larger hash (less leading zeros). Calculating the block hash consists of many (independent) SHA256 hashing operations until a hash is found which is lower than the current [target](https://en.bitcoin.it/wiki/Target) (which is stored in the [`nBits`](https://github.com/bitcoin/bitcoin/blob/df536883d263781c2abe944afc85f681cda635ed/src/chain.h#L180) field of the blockheader and gets adjusted every 2016 blocks as part of the difficulty adjustment algorithm). Each of this hashing operations is independent of all hashing operations before. As the result of SHA256 is pseudorandomly distributed the probability of finding a hash meeting the *target* requirements is only dependent on the current *target* value itself. Any hash below  the *target* will be considered as a valid block proof, but the probability of finding such a hash is the same **for all values below the \*target\*** (no matter if it has 15 or 30 leading zeros). For this reason only the difficulty value (`= highest target / current target`) which was active at the time of block generation is accounted to the amount of total work (see [validation.cpp#L3138](https://github.com/bitcoin/bitcoin/blob/20677ffa22e93e7408daadbd15d433f1e42faa86/src/validation.cpp#L3138) to see where the work of current block is added to `nChainWork` and see [`GetBlockProof(…)` in chain.cpp](https://github.com/bitcoin/bitcoin/blob/aaaaad6ac95b402fe18d019d67897ced6b316ee0/src/chain.cpp#L122-L135) to see how the block work is calculated only from the blockheader's `nBits` (=current target) header field).

7. **Difficulty adjustment is based off of the previous 2016 blocks.**

   The difficulty adjustment algorithm has an off-by-one bug  that leads to the calculation based off of the previous 2015 blocks,  rather than precisely 2016.

8. **Empty blocks are empty.**

   Empty blocks still contain data. They aren't devoid of data, they simply do not have transactions other than the coinbase transaction in them. Since an empty block does not contain any transactions from the mempool, it is considered to be empty. Empty blocks are still computationally expensive because miners still have to produce a Proof of Work. They still have block headers which are 80 bytes and have all the fields that non-empty blocks do.

## Transactions

1. **Once a valid transaction is in the mempool, it will end up in the blockchain.**

   Transactions can be dropped from the mempool. A node's mempool can only occupy as much memory as is configured through `maxmempool`. When this limit is reached, it will drop the transactions with the lowest feerate and increase its `mempoolminfee`. It will communicate its new `mempoolminfee` to its peers, basically telling peers not to forward transactions below that feerate for the time being. Note that every node does this individually, so a node with a larger mempool or different architecture may drop transactions earlier or later.

2. **Before a transaction becomes part of the blockchain it must be in the mempool.**

3. **If I see a transaction in my mempool I can be sure it is in all nodes' mempool.**

   No.

   - Transactions need time to be propagated to every node. If you see it, it does not mean everybody sees it.
   - Every node is configured differently and has certain constraints (e.g. `maxmempool` size reached).
   - A node is not obligated to include a transaction in the mempool and can decline to do so at will.

4. **If a transaction is not accepted in the mempool it cannot be accepted as valid in a block.**

   There are various reasons a transaction might not be accepted, propagated or requested by nodes, e.g. a transaction has a fee rate below the `minrelaytxfee`.

   The `minrelaytxfee` specifies a feerate acting as a lower bound for a node's mempool. A node will not admit unconfirmed transactions below that feerate to its mempool and thus will not relay them to its peers. The `minrelaytxfee` is a configuration setting and can be specified by each node operator independently.

   This does not mean it is invalid or cannot be included in a block.

5. **Yeah, but once it is in a block, it will stay in the blockchain forever.**

6. **Each transaction has exactly one receiver.**

7. **Each transaction has exactly one sender.**

8. **The destination of a Bitcoin transaction (output) is always an address.**

9. **A miner will always select the transactions with the highest fees.**

10. **All transaction hashes in the blockchain are unique.**

11. **Fees are a specified explicitly in a transaction.**

12. **If I make a RBF marked transaction I can always replace it by a different one, as long as it is still unconfirmed.**

13. **If I see a none-RBF marked transaction with enough fee, I can be pretty sure it will end up in the blockchain as it is.**

14. **If I see an unconfirmed payment to an address of mine, I can store the transaction ID as it will never change.**

15. **If the transaction ID of an unconfirmed payment has changed, it was clearly a malicious double-spend attempt.**

### Wallets

1. **All wallets support p2pkh transactions.**

2. **All wallets use standardized derivation paths.**

3. **Brain wallets are secure.**

4. **The 12 (or 15, 18, 21, 24) words of my seed phrase are everything I need to recover my wallet.**

5. **There is only one standard for mnemonic seed phrases (12/24 words).**

6. **Each derivation path (eg. `m/44'/0'/0'/0/0`, `m/44'/0'/0'/0/1`, ...) is guaranteed to derive a valid address.**

   BIP 32 key derivation consists of applying HMAC-SHA512 (see [BIP 32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki) for all details) and using the first 256 bits of the result as key material. Bitcoin uses the `secp256k1` elliptic curve for its underlying signature operations. Not all numbers from 0 to 2^256 are valid keys for `secp256k1`, especially the number 0 and all numbers `> n` (where `n` is the order of the curve) are not valid keys (per definition of secp256k1). As `n` of the `secp256k1` curve is very close to the possible maximum of 2^256 it is very unlikely (probability of less than 1 in 2^127) that the value  derived as part of BIP 32 key derivation is not a valid private key. If such a case ever happens BIP 32 specifies that a wallet should just  skip this index and proceed with the next higher index (see [specification of key derivation](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#private-parent-key--private-child-key) for details).

   So it is possible that wallets exist where the index of  derived keys might have a gap. For these missing indexes then simply no  address exists, and the missing index should be silently ignored by wallets. However, this  case is so highly unlikely it's very likely that nobody will ever see this case in practice. (*Trivia: The author of [pycoin](https://github.com/richardkiss/pycoin) even prepared a [very special error message](https://github.com/richardkiss/pycoin/blob/9837d456a8b7cd8ef5f170b7bc41858957cc5e96/pycoin/key/bip32.py#L12) for the case should this ever happen. :)* ).

7. **If I sweep only parts of the funds on a paperwallet, the remaining rest will always stay on the paper wallet.**

8. **But if I use a wallet providing a dedicated "sweep paperwallet" function and spend only parts of the funds, the remaining  funds will always end up at the exactly same address printed on the  paper wallet.**

#### Keys

1. **Each private key corresponds to exactly one address.**
2. **Compressed WIF Bitcoin private keys are shorter than uncompressed keys.**
3. **Every integer from 1 to 2^256 is a valid private key for a Bitcoin address.**
4. **It is possible to convert an existing Bitcoin private key to a BIP39 mnemonic seed (12/24 words seed).**
5. **It is safe to handout the single private key of an address which was (non hardly) derived from an extended key (xpub/xprv) to a person who also knows the xpub (not the xprv) from which the  address was derived from.**

#### Addresses

1. **Each Bitcoin address has exactly one private key.**
2. **It is always possible to derive an address from an input (or output).**
3. **All Bitcoin addresses have the same length (number of characters).**
4. **All Bitcoin addresses are case-sensitive.**

### Privacy

1. **Bitcoin is anonymous.**

   All coins have a clear and visible history of ownership tracing back to their creation. In addition, the blockchain allows all transactions to be viewed by anyone in the network, so transactions, addresses, and supply can be easily audited by any and all network participants.

   Addresses are merely strings of letters and numbers, and are not inherently connected to a given user or wallet. Both users and wallets can use an arbitrary number of addresses to store bitcoin, and multisig addresses can hold bitcoin belonging to multiple users. Thus, Bitcoin is most accurately defined as pseudonymous rather than anonymous.

2. **All coins spent within a single transaction (inputs) are controlled by the same entity (owned by the same person).**

### Exchanges

1. **Exchanges will always allow withdrawal of funds.**
2. **The coins in my exchange account are mine.**
3. **The coins in my exchange account actually exist.**
4. **Orders which are successfully placed on exchanges are guaranteed to be executed.**
5. **Ask price will always be equal or higher than bid price.**

### Misc

1. **There are exactly 21 million bitcoin to ever exist.**

   The total number of bitcoins has an asymptote at 21 million, due to a side-effect of the data structure of the blockchain – specifically the integer storage type of the transaction output – [the exact value would be 20,999,999.9769 bitcoin](https://en.bitcoin.it/wiki/Controlled_supply#Projected_Bitcoins_Long_Term). However, due to miner underpayment, the total number is even less.

   It is therefore impossible to know exactly how many bitcoin will exist in the year 2140, but it will be less than 21 millions.

2. **Okay, but at least I can be sure the supply is never going to be greater than 21 million.**

   Well.. no.

   Back in August 2010 there was an incident at blockheight [#74638](https://blockchair.com/bitcoin/block/74638): Someone discovered that transaction amounts had no overflow check  implemented (back then) and created a transaction which included 2 outputs each with  92233720368.54277039 BTC (92 billion!). This transaction was considered  as valid by all nodes in the network, because the sum of the inputs (+ fees) *seemed* to be equal to the sum of these 2 outputs (because the sum caused an integer overflow). This [was recognized quickly by the Bitcoin community](https://bitcointalk.org/index.php?topic=822.0) and within a few hours a [bugfix was developed](https://github.com/bitcoin/bitcoin/commit/2d12315c94f12d62b2f2aa39e63511a2042fe55d). As soon as the majority of miners ran the bugfixed version, the chain  containing this block was rejected as invalid and dropped by all nodes, and the new majority chain did no longer contain this block (so you will not see  this block anymore in today's blockchain). You can still see the traces of this incident in the blockchain by  looking at the timestamps of [block 74637](https://blockchair.com/bitcoin/block/74637) (*2010-08-15 17:02*) and [block 74638](https://blockchair.com/bitcoin/block/74638) (*2010-08-15 23:53*). They are several hours apart because that is the time in which the chain with the invalid transaction existed until it was later discarded in favor of the honest majority chain.

   So, technically, there was a short period in time, where  the total amount of Bitcoin was higher than 21 million. If the RPC call `bitcoin-cli gettxoutsetinfo` would already have existed in 2010, it would have returned a total amount of over 184 billion total BTC between 17:02 and 23:53 on 2010-08-15.

3. **All UTXOs are spendable.**

   Some outputs are provably unspendable (for example the [50 BTC output in the genesis block can never be spent](https://bitcoin.stackexchange.com/a/10019/109728)) as well as all [outputs with a `OP_RETURN` script](https://en.bitcoin.it/wiki/OP_RETURN) and others where it is highly likely the coins can never be spent (for example addresses which look "generated" in a  way that somebody just tried to find a valid checksum for the address  string, but it is very, very unlikely that the address really resulted from an actual random hashing operation).  Examples: [1CounterpartyXXXXXXXXXXXXXXXUWLpVr](https://www.blockchain.com/btc/address/1CounterpartyXXXXXXXXXXXXXXXUWLpVr) or [1BitcoinEaterAddressDontSendf59kuE](https://www.blockchain.com/btc/address/1BitcoinEaterAddressDontSendf59kuE). One can safely assume, that these coins are unspendable forever. Besides all this, there are lots of addresses where the private key is lost.

4. **Bitcoin never had a double spend.**

   Ouch! There was a little problem on March 11, 2013, starting at blockheight [#225430](https://blockchair.com/bitcoin/block/225430) during an upgrade from v0.7 to v0.8 ...

   A user described an interesting situation on that day that led to [OKPay suffering a $10,000 double spend](https://bitcointalk.org/index.php?topic=152348.0).

   > 08:08 – Well before I knew what later have happened,  [...], I paid OKPAY address 12z2n8YCJw1BEsJhhQPLCTuLqwH341nKnE 211.9093  BTC and 0.0005 BTC as transaction fee.
   >
   > 09:30 – The transaction was included in version 0.8's fork, block 225446
   >
   > 10:08 – Deposit completed [...]
   >
   > 12:53 – After some study, I recognized, the transaction,  though included in version 0.8's fork, was never confirmed by the  pre-0.8 fork, so I decided to make two double spend transactions on two  of the vins of the OKPAY transaction [...]
   >
   > 13:01 – The double spend transaction was included in pre-0.8 fork block 225446

   Even waiting for confirmations would not have mitigated this scenario and could have had even bigger impacts by making hostile miners more motivated to attempt a [Goldfinger attack](https://www.jkroll.com/papers/oakland15_bitcoin-sok.pdf). After five years, no block explorer shows the original transactions  anymore. That's why it's up for debate whether it was a real double  spend. See [March 2013 Chain Fork Post-Mortem (BIP50)](https://github.com/bitcoin/bips/blob/master/bip-0050.mediawiki) or read the [full story of the 2013 Bitcoin fork](https://freedom-to-tinker.com/2015/07/28/analyzing-the-2013-bitcoin-fork-centralized-decision-making-saved-the-day) - it's fascinating.

## Falsehoods Programmers Believe about Garbage Collection

- **GC always means long large pauses**

  While this was true for the first GCs, it hasn’t been true of most modern GCs for a long time. Many GCs are at least *Incremental GCs*, meaning they do their work in incrementally, doing some work, allowing the program to run, then doing a little more work. Long pauses (due to non-incremental GC) is best if what you care about is throughput (such as in some batch processing use case). Incremental GCs can comfortably manage pauses of less than 10ms, which is fine for most interactive applications (but not games or multimedia, read on for those) much shorter pauses also possible.

- **GC sometimes means long pauses**

  Some incremental GCs can still get stuck with performing some actions in a non-interruptible way.  The initial scan of the program stack is often done in one shot. However, even scanning the call stack can be made incremental. A *good* incremental GC should be able to guarantee a maximum pause time (with the exception of page faults and other things out of its control).

- **But I write games, even short pauses are bad**

  10ms is a long time to interrupt a video game which has a frame budget of at most 16ms. These programs can use a very good incremental GC with shorter pauses, but they’re better off using a *concurrent* GC. In concurrent GC most of the work is done in another thread and therefore the main thread is only paused for hand-offs: when collection starts, when collection stops and when they both try to use the same object. These pauses can be kept well under than 1ms. This does affect throughput, point is, you can’t always assume that GCs always pause.

### More about pauses

The characteristics, including pause times, of a GC is a trade off between multiple factors.  The two main factors are probably pause time and throughput.  Depending on what kind of system you’re building, you may prefer to have longer pauses in return for better throughput.

The first GC I worked on was the BDW GC, we used it for batch processing and therefore didn’t need to use its incremental mode.  Pauses where as long as 500ms, but it didn’t matter, the user never observed this.

The GC I’m working on now is the one built into Firefox’s JS engine.  When I started we had a default incremental budget of 10ms, now it’s 5ms and that seems to be good for most web apps.  I’m sure we could reduce it farther if we tweaked other parameters, such as how frequently it pauses.

### More falsehoods

- **Reference counting (RC) never pauses**

  If a large graph of memory objects is referred to by a single reference, and that reference is deleted, then all those objects need to be freed. Depending on the implementation this can pause while each object’s reference is decremented then the object’s memory is returned to a free list.

- **RC is predictable**

  I’ll concede that it’s deterministic (can be tested).  But I wouldn’t call it predictable.  I couldn’t look at some code and say "Here’s where it’ll pause".

- **GC is not predictable**

  GC can also be deterministic, but it’s sometimes better when it’s not (see [FreeGuard](https://arxiv.org/abs/1709.02746)). If you really need predictable GC, there’s a whole field of real-time GC.

- **RC is simpler, that makes it better!**

  Both RC and GC can be very simple (and have long pauses and other problems), or amazingly detailed (and have better performance). In fact, some of the improvements made to RC and GC are analogies of each other, such as delayed decrementing of reference counts vs lazy sweeping or incremental GC.

- **Allocation the main cost to avoid in GC’d environments**

  The claim is that things should be stack allocated rather than heap allocated.  This is not always a win.  First a stack allocated thing may actually live longer than it needs to, and either requires the programmer to perform their own escape analysis (as in C) or requires language support (as in Rust). Next a *Generational GC* will usually use bump-pointer allocation (slightly slower than stack allocation) to allocate the object. Provided the object isn’t moved out of the nursery it has no further cost; not even freeing it has a cost. The main difference between stack and nursery allocation is therefore what the data is co-located with and therefore how the cache behaves. What *does* have a cost for GC is objects that survive collections and are moved either within the nursery or into the main heap. During collection live objects are traced (marked or moved), this is their main cost.

- **GC won’t collect my objects in a timely manner**

  This one is true!  But why should it matter.  If you’re not low on memory, then why do you need to reclaim that memory right away? (Don’t use GC to manage non-memory resources!) In fact, some GCs perform lazy sweeping: even after they finish their GC cycle they might not sweep some blocks (which frees memory in those blocks) if there’s no allocation pressure for the kinds of objects that need to be allocated in those blocks. In fact a new collection may occur because of pressure elsewhere and those blocks still haven’t been swept, doesn’t matter, they’ll get more up-to-date mark bits and if there’s sufficient memory pressure later on then they might be swept.

- **GC won’t always collect my objects**

  Why is this still a problem? (Don’t use GC to manage non-memory resources!) Some GCs are conservative, meaning they guess whether something is a pointer or not (if they’re unsure then they’ll answer "yes" so as not to free any memory they shouldn’t). This means that sometimes something will look like a pointer, even when it’s not, and the memory it looks like it points to may be retained even when it should have been freed. Don’t use GC to manage non-memory resources! This also sounds like it could be

- **Memory usage**

  A sometimes cited claim is that a garbage collector requires more memory than a traditional heap. The most obvious example is a semi-space copying GC which will require at most 2x the peak heap size (but in practice only 2x the working set) in reserve. To maintain adequate throughput a garbage collector will often use more memory, allowing the heap to grow larger before a GC occurs. And usually this is preferred, but if its not your GC should allow you to tune these parameters. Many GCs can also perform compacting, semi-space copying GCs come by this naturally. Therefore, even if more virtual memory is used it may be possible for a GC to compact the set of working memory into less memory, leading to better cache and TLB efficiency. I previously wrote about memory fragmentation in BDW GC in this [initial article](https://paul.bone.id.au/blog/2016/10/08/memory-fragmentation-in-boehmgc/) and a [follow-up](https://paul.bone.id.au/blog/2016/12/29/more-about-memory-fragmentation/)).

## Falsehoods Programmers Believe About File Paths

- **Paths fit in `PATH_MAX`.**

  This seductively named constant does not mean the full length of a path.

  It was only ever meant to be maximum size of an individual component.

- **Path components fit in `PATH_MAX`**

  We no longer live in those times.

  You can use [pathconf(3)](http://man7.org/linux/man-pages/man3/pathconf.3.html) to determine this limit, but you cannot rely on it, since a different filesystem may be mounted, or a symlink changed, at any time between checking this and using it.

  It is better to dynamically allocate memory for strings on the heap in a [realloc(3)](http://man7.org/linux/man-pages/man3/realloc.3.html) loop.

- **Two files with different paths refer to different files**

  Apart from `/..` being the same path as `/`, hard links, symbolic links and bind-mounts all allow different file names to resolve to the same file.

- **Two files with the same path refer to the same file**

  The same process at different times may see a different file, since another process may have moved it, changed a symbolic link, or mounted a filesystem.

  The process itself may have used [chroot(2)](http://man7.org/linux/man-pages/man2/chroot.2.html) to change its view of the filesystem.

  Different processes can have different views of the filesystem at the same time, since they may occupy different mount namespaces, different roots, or refer to different paths in [proc(5)](http://man7.org/linux/man-pages/man5/proc.5.html), which shows different values of `/proc/self` to each process, and shows different processes in different process namespaces.

- **All files have visibly distinct file paths**

  When file paths are interpreted as unicode different sequences of bytes can produce identical looking strings.

- **File paths are case insensitive**

- **File paths are case sensitive**

  Paths are case sensitive in POSIX file systems, and insensitive on Mac and Windows file systems.

- **File paths are unicode**

- **File paths have an encoding**

  Under Linux, file paths are any sequence of bytes terminated with a `NUL`.

- **File paths have no encoding**

  Under Windows, file paths are Unicode.

- **File paths cannot contain whitespace**

  Shell scripts often get this wrong, but there's nothing preventing you putting spaces in.

- **File paths cannot contain `:` characters.**

  POSIX shells use `:` as the path separator. `make` uses `:` to separate build targets from dependent rules. Old versions of `tar` would interpret a file paths with `:` in file names as a remote tape address.

- **File paths cannot contain `*` or `?` characters**

  If you make use of your shell's globbing feature, you need to escape or quote glob characters.

- **File paths can contain `*` or `?` characters**

  Windows does not allow you to create files with glob characters in.

- **Paths may contain only printable characters.**

  You can have fun and embed a newline character in a file name, which makes old versions of [ls(1)](http://man7.org/linux/man-pages/man1/ls.1.html) appear to print two file names.

- **File path components can contain any string**

  The path separator cannot be part of a path component (excepting filesystem corruption).

  The names `.` and `..` are reserved for current directory and previous.

- **File path components can contain any string except `"."`, `".."`, or `"/"`.**

  Windows reserves CON, PRN, AUX, NUL, COM1, COM2, COM3, COM4, COM5, COM6, COM7, COM8, COM9, LPT1, LPT2, LPT3, LPT4, LPT5, LPT6, LPT7, LPT8, and LPT9.

- **File paths have 1 `.` separating the name from the file extension.**

  You may have a file without an extension, and you may have multiple `.`.

- **File name extensions are 3 characters long.**

- **Path components are separated with `/`.**

  Windows used to only support `\`, now it supports it in addition. More obscure operating systems like RISC OS use `.` as a path separator.

- **Absolute paths start with a `/`.**

  Windows has drive path (e.g. `C:\`), and UNC paths which start with `\\`.

- **`foo` and `foo/../foo` always point to the same directory.**

  If the first `foo` is a symbolic link, then following it takes you to the directory it is in. The `..` takes you to the parent directory of that, which may contain an entirely different directory called `foo`.

- **[Symbolic links may not be empty](https://lwn.net/Articles/551224/)**

- **Symbolic links point to a file that exists.**

  You can put any text that is also a valid file path in a symbolic link. That text may not refer to a file that currently exists. This is called a dangling symbolic link.

- **Symbolic links that don't point to a file that exists are dangling.**

  There're magic symlinks in [proc(5)](http://man7.org/linux/man-pages/man5/proc.5.html), that when read with [readlink(2)](http://man7.org/linux/man-pages/man2/readlink.2.html) display an ID and type, which if you were to pass to [open(2)](http://man7.org/linux/man-pages/man2/open.2.html) would create a new file, but if you [open(2)](http://man7.org/linux/man-pages/man2/open.2.html)'d the file directly would give something else.

### More Falsehoods

- **On MacOS 9 the path component separator was :.** 

  The path component separator is always / or .

  You should add a list of all the reserved characters on Windows,  as well as the COM*, etc. already listed. From  https://msdn.microsoft.com/en-us/library/windows/desktop/aa365247(v=vs.85).aspx#:

  -   < (less than)

  -   > (greater than)

    (colon) " (double quote) / (forward slash) \ (backslash) | (vertical bar or pipe) ? (question mark)

  - (asterisk)

- **Windows UNC paths \FOO refer to a network server.** 

  \.\COM1.

- **Absolute Windows paths always begin with DRIVELETTER**. 

  \?\C:\Foo. This is the long path support, the \?\ prefix  is used to indicate the application can support long paths.

- **Windows UNC paths begin with \SERVERNAME**

  Counterpoint: \?\UNC\SERVERNAME. \?\UNC\ is the long path UNC prefix.

- **A subdirectory of a directory is on the same physical  storage on Windows.** 

  Counterpoint: Drives can be mounted at arbitrary  directories, not just at drive letters.

- **Barring symlinks and hardlinks, a file has only one path  which can access it.** 

  Counterpoint: File paths can contain redundancies  like /./, leading to an arbitrary number of strings accessing the same  file.

- **Barring symlinks and hardlinks and with paths normalised  to remove redundancies, a file has only one path which can access it.**  

  Counterpoint: The same filesystem can appear at different mountpoints on *nix using bind mounts. On Windows, junctions can be used, which  function similarly to directory symlinks, but which are not symlinks and which are substantially more transparent.

- **If a Windows path has a drive letter, it must be an  absolute path.**

  Counterpoint: C:foo.txt (or C:bar\foo.txt or  C:..\bar\foo.txt) is relative to the current working directory which was last set for C:, which may be different to the current working  directory for the current drive letter.

- **Barring symlinks or hardlinks, a file has only one name.** 

   Counterpoint: Short names on Windows. C:\LongFilename.txt is reduced to  C:\LongFi~1.txt for legacy access.

- **A short name will always end in ~1.EXT.** 

  Counterpoint: If  C:\LongFilenameX.txt and C:\LongFilenameY.txt both exist, one will be  C:\LongFi~1.txt and one will be C:\LongFi~2.txt. Which is which is  indeterminate.

- **Opening a path successfully means you've opened a file.**  

  Counterpoint: Directories (and sockets, and so on) can be opened on  *nix. On Windows, alternate file streams are addressed with the colon,  which are subcomponents of files.

- **A file only has one stream of data associated with it.**  

  Counterpoint: Windows has alternate file streams. MacOS has resource  forks.

- **A filesystem supports filenames longer than 8+3  characters.** 

  Counterpoint: DOS is limited to 8 characters before the file extension and 3 after.

- **If you write to a file with provided normalised path X  and then delete normalised path Y, where Y != X, X will still exist.**  

  Counterpoint: On Windows, if X is an alternate file stream path  (C:\Foo.txt:sub1), and Y is the file path (C:\Foo.txt), deleting Y will  delete X. Also if Y != X is a case sensitive comparison and the  filesystem is case insensitive.

- **The types of objects which can appear on a filesystem is  limited to files and directories.**

  Counterpoint: Windows has files  (including hardlinks), directories, symlinks, junctions. *nix has files  (including hardlinks), directories, symlinks, sockets, FIFOs, character  devices, block devices. Some *nixes may have other object types, like  Solaris doors.

- **A platform provides or doesn't provide mandatory locking**

  Counterpoint: Windows does and it is used by default. Linux doesn't  provide mandatory file locking.

- **A filesystem mounted on *nix is always case sensitive.** 

  Counterpoint: Linux can mount FAT32, NTFS, etc.

- **A filesystem mounted on Windows is always case  insensitive.** 

  Counterpoint: Windows can be configured to make its  filesystems case sensitive.

- **The separators between multiple directory components are  the same as that used to separate the directory components and the  filename.** 

  Counterpoint: OpenVMS paths look like this:  SYS$SYSDEVICE:[DIR1.DIR2.DIR3]FILENAME.EXT;FILEVER.

## Falsehoods Programmers Believe About Pagination 

- The number of items on a page is fixed for all time.
- The number of items on a page is fixed for one user.
- The number of items on a page is fixed for one result set.
- The pages are only browsed in one direction.
- No item will be added to the result set during retrieval.
- No item will be removed from the result set during retrieval.
- Item sort order is stable.
- Only one page of results will be retrieved at one time.
- Pages will be retrieved in order.
- Pages will be retrieved in a timely manner.
- No problem will result from two different users seeing different pagination of the same items at about the same time.  (From [@ronburk](https://twitter.com/ronburk/status/1072706694545780736))