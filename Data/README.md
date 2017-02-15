# NFL Play by Play

Possible datasets, in no particular order:

1) From [AdvancedFootballAnalytics.com](http://archive.advancedfootballanalytics.com/2010/04/play-by-play-data.html), covering 2002-2012. 473,591 obs.

COLUMNS:
* gameid: Game identifier with date and teams, e.g., "20020905_SF@NYG". Also indicates home-away teams.
* qtr: Game quarter [1,2,3,4]; overtime period labeled as "5".
* min: Minute of game time; counts down from 60 to 0; overtime labeled as negative numbers, i.e., counting *up*.
* sec: Second of game time; overtime labeled as negatives.
* off: Offensive team on the play.
* def: Defensive team on the play.
* down: Indicates down [1,2,3,4]. Blank for kickoff, PAT, and 2pt conversion plays.
* togo: Yards required for first down.
* ydline: 0 to 100; blank in five obs. which can probably be manually input from the description field.
* **description: Text of what happened on the play, e.g., "(14:25) K.Collins pass incomplete to J.Shockey (D.Smith)."**  
**This column is the bulk of the information, and it's an unholy mess.**

* offscore: Current score of the play's offensive team.
* defscore: Current score of the play's defensive team.
* season: Season label; note that January & February playoff games are labeled as the previous calendar year's season.


2) From [NFLSavant.com](http://nflsavant.com/about.php). Covers 2014-2016. 137,923 obs.

COLUMNS:
* GameId: e.g., 2014090400
* GameDate
* Quarter: [1,2,3,4,5] 5 = overtime.
* Minute
* Second
* OffenseTeam
* DefenseTeam
* Down: [0,1,2,3,4]; 0 for certain plays.
* ToGo
* Yardline: 0 to 99.
* SeriesFirstDown: [0,1] Not sure. Denotes 1st play of series?
* NextScore: **Every value is 0. WTF?**
* **Description: Yeah... same shitshow as above.**
* TeamWin: **Again, all 0's. WTF?**
* SeasonYear
* Yards: -23 to 102.
* Formation: Field Goal, No Huddle, No Huddle Shotgun, Punt, Shotgun, Under Center, Wildcat, blank.
* PlayType: various -- Rush, Punt, Pass, Timeout, etc.
* IsRush: [0,1]
* IsPass: [0,1]
* IsIncomplete: [0,1]
* IsTouchdown: [0,1]
* PassType: Could be useful(e.g., Short Left, Deep Middle, etc.), but also has some mess.
* IsSack: [0,1]
* IsChallenge: [0,1]
* IsChallengeReversed: [0,1]  ** So how often do coaches successfully challenge?**
* Challenger: all blanks... WTF?
* IsMeasurement: **All 0's. AYFKM?**
* IsInterception: [0,1]
* IsFumble: [0,1]
* IsPenalty: [0,1]
* IsTwoPointConversion: [0,1] Attempted two point conversion.
* IsTwoPointConversionSuccessful: [0,1]
* RushDirection: 8 possibles; Left Tackle, Center, etc.
* YardLineFixed: 0 to 50
* YardLineDirection: "OPP" or "OWN". OWN = offensive team?
* IsPenaltyAccepted: [0,1]
* PenaltyTeam: 2-3 letter code for team name.
* IsNoPlay: [0,1]
* PenaltyType: Various, but finite. Some mess, but not a lot, e.g., "YAC 14. A FLAG WAS THROWN".
* PenaltyYards: 0 to 66.


3) Collected by [Maksim Horowitz](https://github.com/maksimhorowitz/nflscrapR) from a web scraper built in R. The [CSV file published by Kaggle](https://www.kaggle.com/maxhorowitz/nflplaybyplay2015) only covers 2015. Notes in Horowitz's GitHub indicate he pulled at least 2009 and 2015, if not 2009 through 2015.

COLUMNS:
* d
* d
* d



4) From [SpreadsheetSports.com](https://www.spreadsheetsports.com/free-tools/2013-nfl-play-play-data-excel/). 2013-2015, and some of 2016. Might not include playoffs.

COLUMNS:
* d
* d
* d



5) [Jesse Anderson](https://vision.cloudera.com/data-insights-from-the-nfls-play-by-play-dataset/), [his GitHub](https://github.com/eljefe6a/nfldata) took the data from (1), added player arrests, stadium and weather data, but... I'm not seeing on his GitHub a completed final file.


# I'm thinking the best bet may be to try merging some of these datasets, even if it only yields 2-3 years.



