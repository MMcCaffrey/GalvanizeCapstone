# Advanded Football Analytics

From [AdvancedFootballAnalytics.com](http://archive.advancedfootballanalytics.com/2010/04/play-by-play-data.html). 
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
