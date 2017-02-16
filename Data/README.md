# NFL Play by Play

Possible datasets, in no particular order:

1) From [AdvancedFootballAnalytics.com](http://archive.advancedfootballanalytics.com/2010/04/play-by-play-data.html). 
* Seasons: 2002 - 2012. 
* Observations: 473,591

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


2) From [NFLSavant.com](http://nflsavant.com/about.php).
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


3) Collected by [Maksim Horowitz](https://github.com/maksimhorowitz/nflscrapR) from a web scraper built in R. The [CSV file published by Kaggle](https://www.kaggle.com/maxhorowitz/nflplaybyplay2015) only covers 2015. Notes in Horowitz's GitHub indicate he pulled at least 2009 and 2015, if not 2009 through 2015.
* Seasons: 2015 (ex playoffs?), possibly 2009-2016
* Observations: 46,129 (2015)

COLUMNS (2015):
* ??:  Integers, not sure what these are.
* Date:  dd/mm/yyyy format
* GameID:  yyyymmdd## format
* Drive: 
* qtr: 
* down: 
* time: 
* TimeUnder: 
* TimeSecs: 
* PlayTimeDiff: 
* SideofField: 
* yrdln: 
* yrdline100: 
* ydstogo: 
* ydsnet: 
* GoalToGo: 
* FirstDown: 
* posteam: 
* DefensiveTeam: 
* desc: 
* PlayAttempted: 
* Yards.Gained: 
* sp: 
* Touchdown: 
* ExPointResult: 
* TwoPointConv: 
* DefTwoPoint: 
* Safety: 
* PuntResult: 
* PlayType: 
* Passer: 
* PassAttempt: 
* PassOutcome: 
* PassLength: 
* PassLocation: 
* InterceptionThrown: 
* Interceptor: 
* Rusher: 
* RushAttempt: 
* RunLocation: 
* RunGap: 
* Receiver: 
* Reception: 
* ReturnResult: 
* Returner: 
* BlockingPlayer: 
* Tackler1: 
* Tackler2: 
* FieldGoalResult: 
* FieldGoalDistance: 
* Fumble: 
* RecFumbTeam: 
* RecFumbPlayer: 
* Sack: 
* Challenge.Replay: 
* ChalReplayResult: 
* Accepted.Penalty: 
* PenalizedTeam: 
* PenaltyType: 
* PenalizedPlayer: 
* Penalty.Yards: 
* PosTeamScore: 
* DefTeamScore: 
* ScoreDiff: 
* AbsScoreDiff: 
* Season: 




4) From [SpreadsheetSports.com](https://www.spreadsheetsports.com/free-tools/2013-nfl-play-play-data-excel/).  
* Seasons: 2013-2015, Sept 2016. DOES NOT include playoffs.
* Observations: 100,894

COLUMNS:
* Date: Date of Game
* Tm: Offensive Team of Play
* Opp: Defensive Team of Play
* Quarter: Game Quarter
* Time: Time of Quarter
* Down: Down of Play
* ToGo: Yards to Go
* Side of Field: Team abbreviation of the side of field where the play started
* Yard Marker: Yard Marker of the Field (0-50)
* Tm Score: Score of offensive team during the play
* Opp Score: Score of defensive team during the play
* Detail: Raw text of what happened during play
* Yds: Yards gained during play (incomplete passes are null)
* Play Type: Run, Pass, or Sack
* Pass Result: Complete or Incomplete
* Pass Distance: Short or Deep
* Pass Location: Left, Middle, or Right
* Run Location: Location of the run (direction and line gap)
* Turnover: 1 = Turnover, 0 = No Turnover (all fumbles get recorded as turnovers regardless of who recovers)
* Fumble: Fumble (regardless of who recovers), null = no fumble
* Interception: Interception, null = no interception
* Passer: Passer on the play
* Intended Receiver: Receiver whom pass was intended for on an incomplete pass
* Receiver: Receiver who caught the pass on a complete reception
* Targeted Receiver: Targeted reciever regardless of pass result
* Rusher: Ball carrier on a rushing play
* Touchdown: Touchdown if the play results in a TD, null if no touchdown
* First Down: First Down if the play results in a first down, null if no first down
* Time Under: Time rounded up to the nearest whole minute
* Score Differential: Score at the time of the play expressed as Offensive team score - Defensive team score
* Absolute Score Differential: Absolute value of score differential
* Game Week: Week of season during which game was played
* Team Game Location: Currently blank for all rows - data unavailable
* Rush Attempt: If play = Rush then 1 else 0
* Pass Attempt: If play = Pass then 1 else 0
* Reception: If play = Pass and Pass Result = Complete then 1 else 0
* Interception Thrown: If Interception occurs then 1 else 0
* Target: If play = Pass then 1 else 0
* Fumble Count: If Fumble occurs then 1 else 0
* Sack: If Play Type = Sack then 1 else 0
* Len: Number of characters in the Detail column
* Yard Line: Yard line of the play (0-100 where 5 means the opponent 5 yard line and 95 is the team's own 5 yard line)
* Playmaker: Ball carrier or targeted receiver on the play
* Touches: Rush Attempt column + Reception column (essentially 1 if a player touches the ball)
* Play Attempts: Value of 1 for every row in the dataset (allows for a count of every play)
* Playmaker Position: Offensive position of the playmaker
* Yards Gained: Yards Gained during play (incomplete passes and other plays for no gain are recorded as 0)
* Play Location: Combination of Rush Location and Pass Location to get a location on every play
* Touchdown Count: 1 if play results in a touchdown else 0
* Play Percent of Goal: Yards Gained / ToGo
* First Down Count: 1 if play results in a first down else 0
* Conversion Count: Combination of Touchdown Count and First Down Count (so 1 if play results in a touchdown or first down)
* Goal To Go: 1 if ToGo = Yard Line else 0
* Success Count: If Down = 1, then play needs to be at least 40% of ToGo for success (success = 1, no success = 0), if Down = 2 then play needs to be at least 50% of ToGo for success, if Down = 3 or 4 then play needs to be at least 100% of ToGo for success
* Penalty Removed Detail: Detail column with penalties removed from text
* Len Penalty: Count of characters of Penalty Removed Detail
* Playmaker Fantasy Points: Fantasy points (based on 1 point per 10 rushing/receiving yards, 6 points for rushing/receiving touchdown, 0.5 points per reception, 4 points per passing touchdown) for the playermaker of the play
* Passer Fantasy Points: Fantasy points for the passer on the play
* Fantasy Points Rushing Yards : Fantasy points attributed only to rushing yards on the play
* Fantasy Points Receiving Yards : Fantasy points attributed only to receiving yards on the play
* Fantasy Points Receptions : Fantasy points attributed only to receptions on the play
* Fantasy Points Rushing TD : Fantasy points attributed only to rushing td on the play
* Fantasy Points Receiving TD : Fantasy points attributed only to receiving td on the play
* Fantasy Points Playmaker Fumble: Fantasy points attributed only to playmaker fumble (-2 points) on the play
* Fantasy Points Passer Yards : Fantasy points attributed only to passer yards on the play
* Fantasy Points Passer TD : Fantasy points attributed only to passer td on the play
* Fantasy Points Passer Interception : Fantasy points attributed only to passer interception (-2 points) on the play




5) [Jesse Anderson](https://vision.cloudera.com/data-insights-from-the-nfls-play-by-play-dataset/) took the data from (1), added player arrests, stadium and weather data, but... I'm not seeing on [his GitHub](https://github.com/eljefe6a/nfldata) a completed final file.


# I'm thinking the best bet may be to try merging some of these datasets, even if it only yields 2-3 years.



