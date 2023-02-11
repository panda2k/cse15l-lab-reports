# Lab 3: Researching Commands (grep)
In this lab, I researched 4 command flags that can be used with `grep`. All
the command examples will be done in the `written_2` folder from 
[here](https://github.com/ucsd-cse15l-w23/docsearch/tree/main/written_2). All 
flags were found from the [grep man page](https://man7.org/linux/man-pages/man1/grep.1.html).

## -r (--recursive)
Recursively searches through all files under a directory, regardless of folder nesting.

### Example 1
#### Command
`grep -r "Challenger"`

#### Output
`./travel_guides/berlitz2/California-WhereToGo.txt:Just north of the Pueblo are the crowded streets and Oriental architecture of L.A.’s Chinatown, while to the south is Little Tokyo, the cultural center of the Japanese community. The Japanese Village Plaza is a popular shopping spot, with twisting paths lined with bonsai trees, rock gardens, and sushi bars. Nearby is a monument to the space shuttle Challenger, including a statue of the Japanese-American astronaut Ellison Onizuka, one of the seven who died in the 1986 disaster.`

#### Explanation
This command searches all files inside of `./written_2` and its subdirectories
for the string "Challenger". This is significantly more concise than doing 
`find . -name "*.txt" | xargs grep "Challenger"`.

### Example 2
#### Command
`grep -r "Ginkgo"`

#### Output
```
```

#### Explanation
If I was looking for mentions of a Ginkgo tree, I could use this command to search
for it in all files under `./written_2`. However,
it appears that no files mention "Gingko".

## l (--files-with-matches)
This flag has `grep` search for files with matching text. However, instead of returning all matching parts
of the text, it'll simply return the file name.

### Example 1
#### Input
`grep -l "Challenger" ./travel_guides/berlitz2/*.txt`

#### Output
`./travel_guides/berlitz2/California-WhereToGo.txt`

#### Explanation
This command searches `./travel_guides/berlitz2` for `.txt` files that contain
the word "Challenger". This produces a much more concise output, which is useful 
if we dont care about the context of the text match.

### Example 2
#### Input 
`grep -rl "Japan"`

#### Output
```
./non-fiction/OUP/Berk/ch2.txt
./non-fiction/OUP/Berk/ch7.txt
./non-fiction/OUP/Abernathy/ch8.txt
./non-fiction/OUP/Abernathy/ch9.txt
./non-fiction/OUP/Abernathy/ch15.txt
./non-fiction/OUP/Rybczynski/ch3.txt
./non-fiction/OUP/Rybczynski/ch1.txt
./non-fiction/OUP/Castro/chP.txt
./non-fiction/OUP/Castro/chL.txt
./travel_guides/berlitz1/HistoryJapan.txt
./travel_guides/berlitz1/HandRJamaica.txt
./travel_guides/berlitz1/HistoryIndia.txt
./travel_guides/berlitz1/WhereToIndia.txt
./travel_guides/berlitz1/HistoryHongKong.txt
./travel_guides/berlitz1/IntroLosAngeles.txt
./travel_guides/berlitz1/WhatToFWI.txt
./travel_guides/berlitz1/WhereToMalaysia.txt
./travel_guides/berlitz1/WhereToJapan.txt
./travel_guides/berlitz1/HistoryHawaii.txt
./travel_guides/berlitz1/WhereToFrance.txt
./travel_guides/berlitz1/WhereToDublin.txt
./travel_guides/berlitz1/HistoryMalaysia.txt
./travel_guides/berlitz1/WhereToLosAngeles.txt
./travel_guides/berlitz1/IntroIndia.txt
./travel_guides/berlitz1/WhereToMadrid.txt
./travel_guides/berlitz1/WhatToJapan.txt
./travel_guides/berlitz1/WhatToHongKong.txt
./travel_guides/berlitz1/WhatToEgypt.txt
./travel_guides/berlitz1/WhereToHongKong.txt
./travel_guides/berlitz1/IntroJapan.txt
./travel_guides/berlitz1/WhatToLosAngeles.txt
./travel_guides/berlitz2/Berlin-WhereToGo.txt
./travel_guides/berlitz2/Boston-WhereToGo.txt
./travel_guides/berlitz2/California-WhereToGo.txt
./travel_guides/berlitz2/Bahamas-WhereToGo.txt
./travel_guides/berlitz2/Bali-History.txt
./travel_guides/berlitz2/Canada-WhereToGo.txt
./travel_guides/berlitz2/Bali-WhereToGo.txt
./travel_guides/berlitz2/Barcelona-WhereToGo.txt
./travel_guides/berlitz2/China-WhereToGo.txt
./travel_guides/berlitz2/California-History.txt
./travel_guides/berlitz2/Bali-WhatToDo.txt
./travel_guides/berlitz2/Nepal-History.txt
./travel_guides/berlitz2/China-History.txt
./travel_guides/berlitz2/Canada-History.txt
./travel_guides/berlitz2/Amsterdam-History.txt
./travel_guides/berlitz2/Beijing-History.txt
./travel_guides/berlitz2/Beijing-WhereToGo.txt
./travel_guides/berlitz2/California-WhatToDo.txt
```

#### Explanation
the `l` flag can be combined with the `r` flag to search all files for a phrase.
In this case, we searched for mentions of Japan. A lot of files matched Japan,
and if we hadn't used the `l` flag, the output would've been super long. This could
be combined with `wc` to count the amount of files that mention Japan.

## -L (--files-without-match
This flag is opposite to the `l` flag. Instead of listing all files with a match, it lists all files
without a match.

### Example 1
#### Command
`grep -rL "water" ./travel_guides`

#### Output
```
./travel_guides/berlitz1/HandRLasVegas.txt
./travel_guides/berlitz1/HandRIstanbul.txt
./travel_guides/berlitz1/HandRHongKong.txt
./travel_guides/berlitz1/IntroDublin.txt
./travel_guides/berlitz1/HistoryIndia.txt
./travel_guides/berlitz1/HistoryDublin.txt
./travel_guides/berlitz1/IntroIsrael.txt
./travel_guides/berlitz1/HistoryMallorca.txt
./travel_guides/berlitz1/HistoryMadrid.txt
./travel_guides/berlitz1/IntroLosAngeles.txt
./travel_guides/berlitz1/HandRMallorca.txt
./travel_guides/berlitz1/HistoryHawaii.txt
./travel_guides/berlitz1/WhatToFrance.txt
./travel_guides/berlitz1/HandRLosAngeles.txt
./travel_guides/berlitz1/HandRMadeira.txt
./travel_guides/berlitz1/HandRIbiza.txt
./travel_guides/berlitz1/HandRLakeDistrict.txt
./travel_guides/berlitz1/WhereToHawaii.txt
./travel_guides/berlitz1/HandRMadrid.txt
./travel_guides/berlitz1/IntroItaly.txt
./travel_guides/berlitz1/HandRJerusalem.txt
./travel_guides/berlitz1/HistoryEdinburgh.txt
./travel_guides/berlitz1/IntroMallorca.txt
./travel_guides/berlitz2/Costa-History.txt
./travel_guides/berlitz2/Barcelona-History.txt
./travel_guides/berlitz2/CostaBlanca-History.txt
./travel_guides/berlitz2/Beijing-History.txt
./travel_guides/berlitz2/CanaryIslands-History.txt
./travel_guides/berlitz2/Budapest-History.txt
./travel_guides/berlitz2/Paris-WhatToDo.txt
```

#### Explanation
Here we combined the `L` flag with the `r` flag to search for all files in `./travel_guides`
where "water" is not mentioned. This could be helpful if we wanted to look for a place
to go without lots of water.

### Example 2
#### Command
`grep -L "magic" ./non-fiction/OUP/Berk/*.txt`
#### Output
```
./non-fiction/OUP/Berk/ch1.txt
./non-fiction/OUP/Berk/ch2.txt
./non-fiction/OUP/Berk/ch7.txt
```

#### Explanation
This command searches for chapters inside the "Berk" book that don't mention magic.
This can be useful to avoid reading about subjects we dislike.

## -i (--ignore-case)
This flag has `grep` search for a phrase while ignoring case. So if we did `Japan`
as the phrase, it'd match all capitalizations like `jApAn` or `japan`.

### Example 1
#### Command
`grep -i "harry" ./non-fiction/OUP/Castro/*.txt`
#### Output
`./non-fiction/OUP/Castro/chM.txt:Joaquín Murrieta’s life has been depicted in novels, stories, newspaper serials, and movies. Charles E. B. Howe wrote a play about Joaquín in 1859 that covers his escapades from the spring of 1851 to July 24, 1853, the day he was captured and killed by Captain Harry Love. It is not known if the play was ever performed, but the portrayal of Murrieta is moving and especially interesting because of all the negative publicity following his capture and death. Howe portrays him as an aristocratic intelligent leader and a man who commits crimes to avenge the wrongs committed against himself and his countrymen.
./non-fiction/OUP/Castro/chM.txt:Joseph Henry Jackson’s work traces the history of the legend, claiming all the information came from the John Rollin Ridge version and that he should be credited with starting the “fictitious” legend. Although Jackson does quote from the San Francisco Alta newspaper demonstrating that many people suspected it was not Joaquín Murrieta who was killed and decapitated by Captain Harry Love, but quite possibly another Joaquín, “every murder and robbery in the country has been attributed to ‘Joaquín.’ Sometimes it is Joaquín Carrillo that has committed all these crimes; then it is Joaquín Murrieta, then Joaquín something else, but always Joaquín!” (Jackson, 13).`

#### Explanation
This command searches all the `.txt` files in `./non-fiction/OUP/Castro` for the word 
"harry" in any casing. This could be useful when searching for a name when you're unsure
if the author consistently capitalized it.

### Example 2
#### Command
`grep -riL "water" ./travel_guides`

#### Output
```
./travel_guides/berlitz1/HandRLasVegas.txt
./travel_guides/berlitz1/HandRIstanbul.txt
./travel_guides/berlitz1/HandRHongKong.txt
./travel_guides/berlitz1/IntroDublin.txt
./travel_guides/berlitz1/HistoryIndia.txt
./travel_guides/berlitz1/HistoryDublin.txt
./travel_guides/berlitz1/IntroIsrael.txt
./travel_guides/berlitz1/HistoryMallorca.txt
./travel_guides/berlitz1/HistoryMadrid.txt
./travel_guides/berlitz1/IntroLosAngeles.txt
./travel_guides/berlitz1/HandRMallorca.txt
./travel_guides/berlitz1/HistoryHawaii.txt
./travel_guides/berlitz1/WhatToFrance.txt
./travel_guides/berlitz1/HandRLosAngeles.txt
./travel_guides/berlitz1/HandRMadeira.txt
./travel_guides/berlitz1/HandRIbiza.txt
./travel_guides/berlitz1/HandRLakeDistrict.txt
./travel_guides/berlitz1/WhereToHawaii.txt
./travel_guides/berlitz1/HandRMadrid.txt
./travel_guides/berlitz1/IntroItaly.txt
./travel_guides/berlitz1/HandRJerusalem.txt
./travel_guides/berlitz1/HistoryEdinburgh.txt
./travel_guides/berlitz1/IntroMallorca.txt
./travel_guides/berlitz2/Costa-History.txt
./travel_guides/berlitz2/Barcelona-History.txt
./travel_guides/berlitz2/CostaBlanca-History.txt
./travel_guides/berlitz2/Beijing-History.txt
./travel_guides/berlitz2/CanaryIslands-History.txt
./travel_guides/berlitz2/Budapest-History.txt
./travel_guides/berlitz2/Paris-WhatToDo.txt
```

#### Explanation
Building off of the previous flags, `r` and `L`, we can use `i` to avoid travel
guides that mention water regardless of capitalization. This is useful because it also
filters sentences that start with "Water" as well as setences that use "water".

