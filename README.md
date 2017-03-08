# An Exploratory Analysis of NFL Play-by-Play Data, 2009-2016
Michael K. McCaffrey, MSF, CFA, CAIA  
mkm1836@gmail.com  
Updated: March 8, 2017
****
This is my Capstone project for the [Galvanize Data Science Immersive](https://new.galvanize.com/austin/data-science) program, Austin December 2016 cohort.  
Expected graduation: March 10, 2017.
****
 

## Overview
Imagine yourself as the Defensive Coordinator for an NFL team. What type of play will the opposing team's Offensive Coordinator try next? Will they pass? Will they run? Predicting this has immense value for deploying a defensive counter-play. Of course, through all of this, the opposing team wants to deceive you, making this something of an adversarial process.


## Data
Some cursory Google searches yield numerous sources of football data, but most are focused on the needs of fantasy football players, which tend to focus on individual players' game-by-game statistics, rather than the individual plays within each game. Other major sports leagues offer open-source software packages with access to their sports data, but the NFL does not. Researchers are left to build their own website screen scraping tools.  

Despite this, I found a handful of potentially good data sources:

* **AdvancedFootballAnalytics.com:** The site was acquired by ESPN in January 2016, and it has not been updated since. Data is available for 2002-2012. Unfortunately, the bulk of the outcome information is the "Description" data field. This field is a test string which would require parsing to be useful. Example: *"(13:07) T.Romo sacked at DAL 19 for -8 yards (R.Bernard)."* This issue was common to most of the data sources I found.

* **SpreadsheetSports.com:** This data actually comes from www.pro-football-reference.com, but SpreadsheetSports.com had the 2013-2015 seasons in convenient Excel files. They did not have playoffs. The datafields available are acceptable, but also have many focused on fantasy football.

* **NFLSavant.com:** Also acceptable datafields available in convenient CSV format, but only covers 2014-2016.

### What I Ended Up Using
* **[nflscrapR](https://github.com/maksimhorowitz/nflscrapR):** A team of Carnegie Mellon University students, led by [Maksim Horowitz](https://www.linkedin.com/in/maksimhorowitz/) produced this exceptionally well-built R library which scrapes the NFL website. As above, the bulk of the play-by-play information is found in a "Description" text field. The nflscrapR library parses those descriptions into numerous situation and outcome columns.  

    After installing R Studio and the nflscrapR package, I learned just enough R to export play-by-play data for nearly all regular season and playoff games for 2009-2016. I am missing only the 2012 Divisional Playoff of the Baltimore Ravens at the Denver Broncos (Baltimore won, 38-25). For unknown reasons, that game produced repeated errors when I tried to pull its plays.  
    
    In addition to the data fields provided by nflscrapR, I manually added the following:
    * Playoff: 1 for playoff game, 0 for regular season.
    * Weekday: Day of the week.
    * WeekNo: 1-17 for the regular season. Playoffs were coded as weeks 18-21.
    * PosHome: 1 if the possessing (offensive) team is playing at home, 0 otherwise.
    * Season: Manually added the season year for playoff games.    

### Data Fields
#### A Priori Data Fields, a.k.a. Features, Independent Variables, X's
* Down: The down of the given play [1,2,3,4].
* PosTeam: The possessing (offensive) team. Standard NFL 2-3 letter codes.
* DefTeam: The defensive team on the play.
* Qtr: The game quarter. Overtime is coded as 5th quarter [1,2,3,4,5].
* Drive: Drive number of the game.
* YdsToGo: Number of yards needed for a first down.
* Yardline100: Distance to opponent's endzone [1-99].
* TimeSecs: Time remaining in game in seconds. Counts down from 3600 to 0; overtime is in negative seconds. 
* GoalToGo: 1 if the play is a goal-to-go situation.
* ScoreDiff: Offensive team score minus defensive team score
* PosTeamScore: The score of the possession (offensive) team
* DefTeamScore: The score of the defensive team

#### A Posteriori Data Fields, a.k.a. Labels, Outcomes, Dependent Variables, Y's (potentially)
* PlayType: The big one. [Kickoff, Punt, Onside Kick, Pass, Run, Sack, Field Goal, Extra Point, Quarter End, Two Minute Warning, End of Game, No Play, QB Kneel, Spike, Timeout].
* SP: Scoring Play; whether the play resulted in any kind of score [1,0].
* YdsNet: Total yards gained on a given drive.
* FirstDown: 1 if the play resulted in a first down, otherwise 0.
* YardsGained: Amount of yards gained on the play.
* Touchdown: 1 if play resulted in a Touchdown, otherwise 0.
* ExPointResult: Result of the extra-point: "Made", "Missed", "Blocked" or Null.
* TwoPointConv: Result of attempted two-point conversion: "Success", "Failure", or Null.
* DefTwoPoint: Result of attempted defensive two-point conversion: "Success", "Failure", or Null.
* Safety: 1 if play resulted in a safety, otherwise 0.
* Onsidekick: 1 if Kickoff was an onside kick, otherwise 0.
* PuntResult: Result of punting play. Either "Clean" or "Blocked"
* ChalReplayResult: Result of the replay review: Upheld or Overturned
* AcceptedPenalty: Binary variable indicating whether a penalty was accepted on the play.
* PenalizedTeam: The team who was penalized on the play.
* PenaltyType: Type of penalty on the play.
* PenalizedPlayer: The penalized player.
* PenaltyYards: The number of yards that the penalty resulted in.
* Passer: The passer on the play if it was a pass play.
* PassAttempt: Binary variable indicating whether a pass was attempted or not.
* PassOutcome: Pass Result: Complete or Incomplete.
* PassLength: Categorical variable indicating the length of the pass: Short or Deep.
* PassLocation: Categorical variable: left, middle, right.
* InterceptionThrown: Binary variable indicating whether an interception was thrown.
* Interceptor: The player who intercepted the ball.
* Rusher: The runner on the play if it was a running play.
* RushAttempt: Binary variable indicating whether or not a run was attempted.
* RunLocation: The location of the run: left, middle, right.
* RunGap: The gap that the running back ran through.
* Receiver: The player who recorded the reception on a complete pass.
* Reception: Binary Variable indicating a reception on a completed pass: 1 if a reception was recorded else 0.
* ReturnResult: Result of a punt, kickoff, interception, or fumble return.
* Returner: The punt or kickoff returner.
* BlockingPlayer: The player who blocked the extra point, field goal, or punt.
* Tackler1: The primary tackler on the play.
* Tackler2: The secondary tackler on the play.
* FieldGoalResult: Outcome of a fieldgoal: made, missed, blocked.
* Sack: 1 if a sack was recorded else 0.
* Fumble: 1 if a fumble occurred else 0.
* RecFumbTeam: Team that recovered the fumble.
* RecFumbPlayer: Player that recovered the fumble.


#### Irrelevant, Redundant, or Otherwise Unneeded Data Fields
* GameID: A 10-digit game ID given by the NFL website to each game.
* Date: "yyyymmdd" format.
* Time: Time at start of play, counting down for 15:00 for each quarter
* Yardline: From 0 to 50. Discarded in favor of Yardline100.
* Description: A text string description of what happened on the play.
* PlayTimeDiff: The time difference in seconds between plays.
* TimeUnder: Time remaining in game quarter, rounded up to next full minute.
* PlayAttempted: A variabled used to count the number of plays in a game (always 1).
* expectedpoints: The expected point value of the play before the snap.
* OffWinProb: The win probability of the offensive team.
* DefWinProb: The win probability of the defensive team.
* SideofField: The side of the field that the line of scrimmage is on.
* FieldGoalDistance: Field goal length in yards.
* ChallengeReplay: 1 if the play was reviewed by the replay offical on challenges or replay reviews.

#### Miscellaneous Data Notes
* Created boolean columns out of PosTeam, DefTeam, HomeTeam, and AwayTeam.
* Recoded sacks as passing plays.
* Test/Train split is the Sci-Kit Learn default 25% test.


### Model
I used a Random Forest model because it offers offers many advantages: 1) it can handle a large number of features (initially, I had 153 features), 2) it can handle correlated features, and 3) it does not require rescaling of feature variables. After experimenting with various configurations (number of trees, size of leaf nodes, number of features considered at each split), I ran a grid search over the following parameters:
    * Number of Trees: 25, 50, 100
    * Minimum Leaf Node Size: 10, 25, 50
    * Percent of Features: 10%, 20%, 30%

Across all 36 permutations, the test scores were incredibly similar, which led me to run a second grid search with the goal of minimizing runtime while holding test score nearly constant:
    * Number of Trees: 200, 350, 500
    * Minimum Leaf Node Size: 5, 10, 25, 50
    * Percent of Features: 20%, 30%, 40%

Looking at 25 trees, with 10 observations per leaf, and 10% of features was the winner. If possible, I recommend using a second computer or AWS (even if your data fits on one computer) for grid searches. They are phenomenal resource hogs.


### Results
#### Vanilla plays
After narrowing the dataset down to just passing and running plays, the remaining dataset contained 269,745 observations, with 58.5% passes and 41.5% runs. I excluded play types which I felt were pretty easy to predict and/or relatively rare: field goals (2.7%), punts (6.7%), and QB kneels (1.1%). I also excluded QB Spikes, which are technically an incomplete pass. We could debate how easily predictable these situations are, but truthfully, spikes are relatively uncommon (0.2% of plays), and their execution is too quick to allow much defensive opportunity.  

I achieved 69% accuracy on the test set. This compares favorably to the 58.5% one would get from a simple "Alway Pass" prediction, but far from stellar. The most important features were Down (31%), YdsToGo (25%), TimeSecs (17%), and ScoreDiff (12%).  

Interestingly, many of the things that announcers like to hype just didn't matter: 
* Late in the season? Pfffft.
* Playing at home? Whatevs.
* Monday Night Football!!! So what?
* PLAYOFFS!!!!! Meh.

![image](https://github.com/MMcCaffrey/GalvanizeCapstone/blob/master/Images/VanillaFeatureImportances.png)

#### Fourth Downs
Fourth down plays represent a tremendous "make or break" opportunities for both the offensive and defensive teams. Obviously, the down number is now irrelevant to the model. Here, I achieved a test split accuracy of 82%, which also compared favorably to the naive method of always picking the majority class (Pass, at 62.9%). As expected from the broader analysis, the most important features were YdsToGo (39%), TimeSecs (14%), ScoreDiff (13%), and DefTeamScore (11%).

![image](https://github.com/MMcCaffrey/GalvanizeCapstone/blob/master/Images/FourthDownFeatureImportances.png)

#### Two-Point Conversions
Two-point conversions also represent opportunities for both teams. These plays typically happen when the score is relatively close. On average, the offensive team trails by 3.1 points when attempting a two-point conversion. Unfortunately, the model largely picked the majority class everytime (Pass, at 73.6%). So that's disappointing.


#### Season-by-Season

![image](https://github.com/MMcCaffrey/GalvanizeCapstone/blob/master/Images/AccuracyPassPctbySeason.png)

#### Team-by-Team
Examining each team separately yields a fairly constant test accuracy, despite variations in passing percentage.

![image](https://github.com/MMcCaffrey/GalvanizeCapstone/blob/master/Images/AccuracyPassPctbyTeam.png)  
.  
.  
.  
### OK, so what else could we do with this dataset in the future?
* Add coaching data (head coach, offensive & defensive coordinators).
* Look at each team by each down, e.g., Dallas on 1st down.
* Add some recent event functionality.
    * What happens on the play following a sack?
    * How do number of prior interceptions and/or fumbles in a game affect playcalling?


