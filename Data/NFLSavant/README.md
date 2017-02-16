# NFLSavant.com

From [NFLSavant.com](http://nflsavant.com/about.php).
* Seasons: 2014 - 2016. 
* Observations: 137,923

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
