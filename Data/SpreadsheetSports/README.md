# SpreadsheetSports.com

From [SpreadsheetSports.com](https://www.spreadsheetsports.com/free-tools/2013-nfl-play-play-data-excel/).  
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