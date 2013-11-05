<a id="2013-07-12"></a>2013-07-26
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/b1f8b3177cfe303cb401473850bbb639a5893f62)

### Modes

#### Battle
* After a team balance the players are not unspawned automatically anymore. They'll join their new team at their next respawn.

#### Combo
* The intro loops in matchmaking mode
* Fixed: the players collisions were not active in warm up
* Uses the new WarmUp2 library
* Improvements on the weapons UI
* Improvements on the matchmaking mode

#### Elite
* "Master" (MVP) integration for the matchmaking
* Displays a window introducing the mode to the new players
* Displays the sponsors of the attacker in spectator mode
* Addition of the players position in the OnShoot, OnHit and OnArmorEmpty XmlRpc callback

#### Elite practice
* "Master" (MVP) integration for the matchmaking
* Display a window introducing the mode to the new players
* The intro loops in matchmaking mode

#### Joust
* Displays the map info and players scores in the spawn screen

#### ModeSport
* The intro loops in matchmaking mode
* The match and map scores are accessible with the XmlRpc GetModeScriptVariables() method
* "WarmUp_Extend" and "WarmUp_Stop" XmlRpc script events to manipulate the warm up
 
#### Royal
* UI improvements


### Libraries

#### Clublink
* Attach()/Detach() to manipulate the Clublink UI
* SetSponsorsDisplay() to show/hide the sponsors in the UI
* GetTeamSponsors() to get the path to the sponsors logo

#### Interface
* New style for the "top" type of slide
* SetSliderAnimation() to set the start and end position of the slider animation
* Addition of a new parameter in the CreatePlayersLists() function to show/hide the teams name above the players lists.

#### LobbyMelee
* UI improvements

#### ScoresTable
* The spec button is only displayed near spawned players in the scores table
* If the player is not in spectator mode, a confirmation will be asked before switching to spectator
* The lights on each side of the team scores table are now colorized dynamically (no need to rebuild the whole scores table anymore)
* SetTabName() to set the name of the scores table tab (used by the tab library)

#### SpawnScreen
* UI improvements

#### Top2
* SetTabName() to set the name of the top tab (used by the tab library)

#### Toss
* The vote display continues to be updated after the end of the vote, so even last second vote are correctly displayed on the UI

#### WarmUp2
* UI improvements
* SetLayerPosition() to update the position of the UI on screen
* A player cans leave his slot by pressing the "0" or "Numpad0" key
* The items related events are discarded in the ManageEvents() function

---------------------------------


<a id="2013-07-12"></a>2013-07-12
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/4a59cd04afecc9536abf7b3181de5e05608fbb84)

### Modes

#### Elite
* Display a window with the rules the first time the player try the mode

#### ModeSport
* Only display the avatar above the head of our teammates
* Improvements on the matchmaking map start


### Libraries

#### Clublink
* Uses Private_ApplyDesiredTeamColors(). If the colors of the two teams are too close, they will be changed to something more discernible.

#### ElitePractice
* Fixed: runtime error on attacker spawn
* Plays a sound on pole capture
* Only display the avatar above the head of our teammates
* Displays the name and the echelon of the attacker in the bottom right corner of the screen
* The attacker is unspawned instantly after a time limit and the defenders after a pole capture
* Display a window with the rules the first time the player try the mode

#### LobbyMelee
* The players continue are not unspawned between rounds anymore

---------------------------------


<a id="2013-07-11"></a>2013-07-11
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/41f868dce48d6618e35797718daa722feffdcabd)

### Modes

#### Battle
* Fixed a bug that could happen on the coloration of the poles bases
* Better tops presentation

#### Elite
* Uses the new LobbyMelee library
* Uses the new ElitePractice library
* Displays the players who are allies in the scores table with an icon near the player ranking
* The OnNearMiss event is only process for the Laser, the rockets are discarded

#### Heroes
* The OnNearMiss event is only process for the Laser, the rockets are discarded

#### ModeSport (Elite & Heroes)
* Uses the new WarmUp2 library
* Forces the display of the tags above the teammates
* It's possible to set the attacking order in matchmaking with an XmlRpc callback (MatchmakingGetOrder and MatchmakingSetOrder -> format: playerA1,playerA2,playerA3|playerB1,playerB2,playerB3)
* Addition of the goal average of the players in the JSON sent by the server

#### Siege
* The OnNearMiss event is only process for the Laser, the rockets are discarded


### Libraries

#### EliteEndSequence
* Uses the new WarmUp2 library

#### ElitePractice
* New Elite Practice game mode

#### LobbyMelee
* New lobby mode

#### ScoresTable
* UI adjustement

#### SpawnScreen
* New funtions to display the rules more clearly

#### WarmUp2
* New warm up lib

---------------------------------


<a id="2013-07-02"></a>2013-07-02
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/dc5d096d6e0d2cab31518ebe8c698c9e877a7c75)

### Modes

#### Elite
* Fixed: randomly sent back to warm up in free mode when someone leaves the game.
* Plays the intro sequence at the beginning of the map.
* Plays the podium sequence at the end of the match.
* The players with the most LP attack first in matchmaking mode.
* Displays a custom manialink gauge when capturing the pole instead of the default one. The filling of the gauge is now much more fluid.
* Uses the hit difference in the formula to calculate the LP at the end of the map.
* Integration of the new #Command API. You can now:
  * Set the score of the current match
  * Set the score on the current map
  * Set the score of the previous maps
  * Set who won the toss
  * Set who will be the first attacking clan
  * Set the number of eliminated defenders during the tie break
  * Force a pause (cancel the current round and go back to warm up)
* UI improvements: 
  * Displays the number of spectators on the server on the top left of the scores table.
  * Displays the hits of the defenders next to their names in the players lists on the sides of the screens.
  * It's now possible to show/hide the players list on the side of the screen by pressing F8.
  * The players lists are in attacking order when playing.
  * Displays the number of hits done and taken in the scores table.
  * Displays the number of armors left to each player in the scores table through a gauge below their names.
  * Displays the LP and echelon progression at the end of the map.
  * Displays the echelon of each player next to their names in the scores table.

#### Heroes
* Fixed: there are 3d markers above the checkpoints when using an Elite map.

#### Joust
* Fixed: the Arrows don't work properly. You only have one ammo and no reload.

#### RoyalExp
* Fixed: it's possible to rebirth two times in a row.

#### Siege
* The players can now change their clan during a round, they won't be eliminated anymore. Instead they will continue to play with their current clan until the end of round and spawn in their new clan at the beginning of the next round.

#### ModeBase
* The S_NeutralEmblemUrl setting now work properly. Set the URL of the new emblem to use as the default one on the poles and spawns.
* MB_Yield() function and +++Yield+++ label. Useful to replace the standard yield; instruction when you want to be sure that a function or a library is updated at each frame.
* The MB_PlayersPresentationSequence() function can now take an Integer as parameter to set the duration of the player presentation sequence.
* New MB_CurrentSection variable. It saves the name of the section currently executed.


### Libraries

#### Chrono
* Show(Ident _PlayerId) and Hide(Ident _PlayerId) functions to show/hide the chrono of a player.

#### Clublink
* A clubLink will be activated only if all the players of the team share the same ClubLink and are listed as player inside it.

#### EditorDialogs
* Fixed: the script uses a deprecated class name.

#### EliteEndSequence
* New lib managing the display of the LP and echelon at the end of the map

#### Interface
* Addition of functions to easily create players lists for team mode (as in Elite)

#### ScoresTable
* FilterLogins(Text[] _Logins) to filter the players displayed in the scores table by their login.
* FilterStatus(Text _Status) to filter the players by their status (All/Playing/Alive/Spectators).
* The Build() function can now take a second parameter to force the free for all or team mode of the scores table.
* Displays the echelon of the player next to his rank.

#### SpawnScreen
* Fixed: wrong players displayed in the top3 scores when one of the top 3 player leaves the server.
* The CreateScores() function can take a parameter to change the way the score displayed in the spawn screen is calculated.

#### WarmUp
* UI update
* The SwapSlot() function can now take a parameter to force the swap of a player

#### XmlRpc
* New LibXmlRpc_LoadingMap callback sent when the script call the LoadMap() function.
* New LibXmlRpc_GetScores callback to get Match and Map scores

---------------------------------


<a id="2013-05-16"></a>2013-05-16
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/5ece3de0ccbd01a068fc3777734e99edd1c8305c)

### Modes

#### All
* Scores table UI update
* Better coloration of the bases in the map

#### Combo
* Can change weapon with the scroll wheel
* Use the new object API
* The spectators can see the number of ammo max of the player they're spectating
* Fixed: The players could respawn when the storm reached its minimal radius

#### Elite
* UI update
* Fixed: the players are displayed as eliminated in the scores table at the end of the match
* Addition of a small pause and a message before a map change due to a vote
* Displays only two decimals on the LP received at the end of the match
* Displays the fame stars of the player near its avatar
* S_UseScriptCallbacks must be set to true if the mode must send/receive XmlRpc callback

#### Heroes
* Addition of the XmlRpc callbacks on events
* Displays the miss distance of the laser shots
* Displays the hit distance with the Laser
* Uses the same icons than in Elite for the poles and the Nucleus
* New scores table

#### Joust
* Addition of a "best combo" stat

#### Siege
* Displays the miss distance of the laser shots
* Displays the hit distance with the Laser


### Libraries

#### ScoresTable
* Update of the interface
* New button to automatically display the page where you're ranked (shortcut key: home)
* New function SetDisplayManiaStars() to show/hide the ManiaStars in the table
* New function SetDisplayPlayerInfo() to show/hide the player info in the footer
* New functions SetFooterCustom1() and SetFooterCustom2() to display a custom text instead of the player info in the footer
* New function SetScoreFormat() to change the text formating of the points column (just like the round points column)
* Displays the points in the footer with the same format than in the scores table

#### XmlRpc
* New actions "LibXmlRpc_DisableAltMenu" and "LibXmlRpc_EnableAltMenu" to hide/show the scores table displayed when pressing alt

---------------------------------


<a id="2013-04-24"></a>2013-04-24
---------------------------------

### Modes

#### All
* Updated the script callbacks
* Updated the scores table

#### Combo
* UI update
* You start with 1 ammo when you pick up a weapon for the first time

#### Elite
* UI update
* Fixed: the OnArmorEmpty callback doesn't return the correct WeaponNum
* Better coloration of the bases in the map

#### Joust
* UI Update
* Better coloration of the bases in the map

#### Realm
* UI Update

#### Royal
* New callback before the end of the round sending the round winner login

#### Time Attack
* UI Update


### Libraries

#### Interface
* Update of the team list UI

#### ScoresTable
* Updated the Z-index of all the elements of the scores table
* SetDisplayTeamScore() function: display/hide the teams scores

#### WarmUp
* UI Update

#### XmlRpc
* Call the SendRankings() function in EndTurn(), EndRound(), EndSubMatch(), EndMap() and EndMatch()
* New Royal_RoundWiner() callback

---------------------------------


<a id="2013-04-10"></a>2013-04-10
---------------------------------

### Modes

#### All
* Added a description of the current mode in the help menu
* Added a short description of the mode running on the server in the server browser
* Better integration of the ClubLink system
* Implementation of minimal scripts callbacks

#### Combo
* New game mode

#### Elite
* It's now possible to select the remaining defender to spectate once eliminated
* Skip the end round sequence when a team wins a map
* UI update
* Fixed: wrong callback on attacker elimination

#### Siege
* New way to determine the advantage at the end of the round. Tested in this order:
  * Team with the most points since the beginning of the map
  * Team with most capture in the last round
  * Fastest team to capture their poles during the last round
  * Keep the previous advantage
* Display a marker above the attackers that are positionned at less than 50m of the defenders spawn during 5 seconds after a pole capture
* Once eliminated you're not locked on one player anymore, you can spectate anybody in your team
* Less waiting time between the rounds/maps
* UI update
* Use the ScoresTable library

#### Joust
* Collisions between players are disabled at the start of the round until a player touch the first pole
* Use the ScoresTable library
* Can now start a map with a warm up
  
#### Battle
* UI update
  
#### Realm
* Addition of a setting to limit the respawn time
* Use the new team scores table background

#### Royal
* You can create an alliance with up to two players and spawn with them at the start of the round
* Display miscellaneous top when not playing
  
#### ModeBase
* Addition of a LogVersion extend and MB_LogVersion() function to easily display in the log the versions of each scripts used in a game mode
* Label +++OnNewBot+++ called when a bot join a game


### Libraries

#### Clublink
* More stable behaviour in finding the correct Clublink to use
* SetTeamDefaultName() and SetTeamDefaultColor(): set a new default name and color for teams
* SyncUpdate(): Synchrone update of the players Clublinks
* To avoid confusion, two teams can't use the same Clublink at the same time
* Display of sponsors images for spectators and players now working
  
#### Lobby
* Fixed: the lobby is in team mode
* Fixed: the script crash if someone is hit by a disconnected player
* Fixed: the script crash after a few maps because of the spawns
* Scores/Combo/Armors are conserved when disconnecting/reconnecting to the lobby

#### ScoresTable
* Limit the ladder points display to two decimals
* Display the total amount of ladder points of the player
* Display the ManiaStars of the player

#### Interface
* Added a slider widget. Allow to display a small window with cycling tops, text and/or pictures

#### WarmUp
* Bots are automatically set in ready states
  
#### XmlRpc
* Now contains commons and mode specific script callbacks
  
#### Top2
* Added a Destroy() function to destroy a top
* Added 2 GetRecord() functions to get a specific entry in a top
* Added a GetRank() function to get the rank of a player in a top
  
#### MapType:
* Fixed the translations

---------------------------------


<a id="2013-02-06"></a>2013-02-06
---------------------------------

### Modes

#### Elite
* The defenders can choose their weapons at the start of each round
* New EliteB2 setting, to reverse to the beta 2 gameplay
* Draft at the start of a match now work in free mode too
* Possibility to launch an Elite server in lobby mode
* New capture time calculation for maps with checkpoints. Minimum capture time is 0.5 second and we add 1 second for each checkpoint not captured on the map.

#### Realm
* New mode


### Libraries

#### Settings
* New library to manage online settings

---------------------------------


<a id="2013-01-23"></a>2013-01-23
---------------------------------

### Modes

#### Elite
* Updated the script callbacks
* Display a gauge on the attacker interface when he's capturing
* Fixed "Missed by 0mm" messages
* Defenders start with a reloaded instead of half reloaded nucleus
* New "Player tagging" feature
  
#### Battle
* Scores weren't initialized after a vote nextmap

#### Melee
* Removed the "Tie the leader" messages
* Optimization of the UI code

#### Time attack
* Use the new scores table library


### Libraries

#### ScoresTable
* New scores table library

#### Rules
* The Rules library is replaced by the SpawnScreen library which offer more functionalities (mapper info, scores top 3, rules)
  
####  Tops
* New tops library

---------------------------------


<a id="2012-12-18"></a>2012-12-18
---------------------------------

###Modes

#### Royal
* New scores table UI
* Early respawn: the players can respawn until the pole is captured but with only one armor point
* A map can't end in a tie anymore, another round is  played until a player takes the lead
* The Laser can only remove one armor point by shot
* Double the radius of the ending zone from 8 to 16 meters
* Always display your rank on the spawn screen scores table

#### Elite
* New scores table UI
* Display a message when the attacker miss a shot by less than 30 centimeters (ingame distance between the laser and the targeted player)
* Updated and added XmlRpc script callbacks: BeginMatch, BeginMap, BeginSubMatch, BeginTurn, EndTurn, EndSubMatch, EndMap, EndMatch, BeginWarmup, EndWarmup, OnHit, OnArmorEmpty, OnPlayerRequestRespawn, OnCapture, OnShoot, OnNearMiss

#### ModeBase
* Added a custom sleep function allowing to call other functions while waiting for the duration passed as parameter (useful for catching UI events on the server during map or round ending by example)


### Libraries

#### Draft
* It's now possible to explicitly set the number of maps to ban and to pick (not necessary anymore to ban all the map from the server before the pick)
* Voting order changed from ABAB to ABBA
* corrected a bug when using only one map on the server

#### WaitingQueue
* Updated the UI: display the scores table on the right of the screen and don't let a single player appear multiple time after a disconnection (mode Joust)
 
#### Color
* Convert from HSV|RGB|HEX color code
* Generate equally distributed colors on a specific range
  
#### Json
* Allow to serialize useful informations about different ManiaScript entity: Events, Players, Users, Scores, Teams, BlockPole, etc
  
#### Message
* Added some utilities functions, mostly for cleaning Big and Status messages

#### Top
* Added an alternative UI style to match the one in Royal

---------------------------------


<a id="2012-10-11"></a>2012-10-11
---------------------------------

#### Battle
* Fixed: Typo on the Rules library include

#### Elite
* Use the new Draft library. The players can choose the maps from the server that will be played during the match.
* New tie-break system. When both teams reach the max points limit, the team with the best goal average since the beginning of the match wins. If the teams are tied, we play two more turns. At the end of the two turns, if both team are still tied, the team who eliminated the most defenders since the beginning of the tie break wins. If it's always a tie, we play once again two more turns until a winner is found.
* Checkpoints can't be captured anymore once the pole can
* Display the maps and points limit in the interface
* Fixed: the number of captured checkpoints wasn't set to 0 at the beginning of the turn in the interface
* Fixed: the WarmUp UI stays displayed even after the start of the match

#### Joust
* Extends from the ModeBase script
* Use icons above the poles
* Fixed: the time limit to capture a pole is not active
* Fixed: disabled the S_MatchPointsAuto option

#### Melee
* Displays various messages and plays sounds about the game progression

#### ModeBase
* New "custom event" generated when a new player or spectator appears
* Disable the logging by default

#### Royal
* Fixed: play the wrong sound at the beginning of the round

#### Siege
* Fixed: the weapon selection interface stays displayed after the beginning of the round

#### Time-Attack
* UI improvements


### Libraries

#### Message
* New library to handle BigMessage and StatusMessage

#### Draft
* New library for Elite, let the players ban and select maps at the beginning of the match

#### Achievements
* English translation of the achievements

#### Interface
* New functions to display the score ranking of the player

#### Layers
* New overload version of the Create() function to create a layer and save a manialink inside it at the same time

#### Toss
* UI improvements

#### Warmup
* UI improvements

#### WaitingQueue
* Deleted unnecessary log

---------------------------------


<a id="2012-09-25"></a>2012-09-25
---------------------------------

### Modes

#### Elite
* Include new features from Elite Exp
  * Toss
  * Checkpoints
  * Laser can hit rockets (can be turned off in settings)
  * More stamina for the defenders

---------------------------------


<a id="2012-09-06"></a>2012-09-06
---------------------------------

### Modes

#### All
* Creation of a basic game mode (BasicMode.Script.txt) from wich other modes can easely extend
* Use the correct sound for messages
* Use the new Rules library to display the rules

#### Battle
* The server goes to next map instead of keeping to throw an error if the map played doesn't have the same number of poles for each team
* Fixed: The scores table doesn't pop up automatically at the end of the rounds and matches
* Fixed: The intro of the map is not played

#### Heroes/Elite
* Defenders have 3 rockets instead of 4
* Defenders have 0.7 StaminaMax instead of 0.5
* New toss system. At the beginning of the match a team is drawn. Then this team choose if she wants to defend or attack first on the first map. On the second map it's the turn of the other team to decide. In the case of a best of 3, if the third map is played, it's the team with the best goal average who decides to start in attack or defense.
* Code rewrited to use ModeBase.Script.txt and ModeSport.Script.txt
* WarmUp and LineUp now handled by the WarmUp library
* Use the Layers library to handle the UI
* Introduced a checkpoint system (each captured checkpoint reduce the capture time of the final pole)
* Display the name of the player who elimated the attacker in Elite
* Fixed: The attacker captured the goal and was eliminated at the same time
* Fixed: can't take a slot in the line up for no apparent reason
* Fixed: A player can take the place of a ready player in the line up
* Fixed: The next map vote now behave correctly (but a restart map vote still restart the match)

#### Time Attack
* Extends from the new ModeBase script
* Use the Layers library to handle the UI
* Use the Chrono library to handle the timer
* Show the ranking of the first three players on the spawn screen
* Fixed: no ladder points awarded at the end of the map

#### Joust
* Code cleaning
* The player's poles are reset if he falls in an offzone or respawns

#### Melee
* Use the Layers library to handle the UI
* Show the ranking of the first three players on the spawn screen

#### Royal
* Extends from the new ModeBase script
* Show the ranking of the first three players on the spawn screen

#### Siege
* Extends from the new ModeBase script
* Autobalance team added to the options
* Fixed: Use the spectator mode to respawn during the attack phase even after loosing all its armors.


### Libraries

#### Rules
* New library to display the rules in the spawn screen

#### Toss
* New library for the toss system (see heroes/elite)

#### Chrono
* New library to create timers

#### Achievements
* New library to manage achievements during a game

#### Layers
* The library is now compatible with Spectators

#### WarmUp
* The library now include the line-up management module (as in Elite and Heroes)

#### WaitingQueue 
* Deprecating WaitingList and now using WaitingQueue for better performances

---------------------------------


<a id="2012-07-26"></a>2012-07-26
---------------------------------

### Modes

#### Siege
* Use the new Layers library to handle the UI
* Fixed: Sometimes a pole was skipped (double capture)
* Show the number of Laser, Nucleus and Rocket in your team during the weapon selection sequence

#### Royal
* Automatically activate the pole after 90 seconds (can be edited in the settings)
* Use correct sounds for messages
* Show the name of the winner at the end of the map, even if he's offline or in spectator

---------------------------------


<a id="2012-07-24"></a>2012-07-24
---------------------------------

### Modes

#### Elite
* 3 modes: normal, free, king
  * Normal: classic elite game mode
  * Free: 1 to 3 of players in teams. Players can leave and join the game when they want. The attacker has a number of armor equal to the number of defenders.
  * king: As in Joust, teams of 3 players must win 3 matches to become the king of the map. The team who wins a match stay in place, the looser give its place to a team in the waiting list. When a team become the king of the map, we change map and restart from the beginning.
* It's now possible to disable the warm up by setting it to 0 second.

#### Heroes
* 3 modes: normal, free, king
  * Normal: classic heroes game mode
  * Free: 1 to 5 players in teams. Players can leave and join the game when they want.
  * king: As in Joust, teams of 3 players must win 3 matches to become the king of the map. The team who wins a match stay in place, the looser give its place to a team in the waiting list. When a team become the king of the map, we change map and restart from the beginning.
* It's now possible to disable the warm up by setting it to 0 second.

#### Battle and BattleWaves
* Added markers above the poles to capture/defend
* Added the settings to translation
* Code cleaning

#### Royal
* Correctly end the round when there's only two players in game and one go to spectator

#### Joust
* Replace the old waiting list system by the new waiting list library

---------------------------------


<a id="2012-07-19"></a>2012-07-19
---------------------------------

### Modes

#### All
* Use of MLEncode in the ManiaLink UI

#### Elite
* Show the name of the player who has done the longest rail under the scores table
* Show a "Press F6 once you're ready" message during the warm up
* Show the correct attack order in the scores table during the warm up
* Show the ready state of the players in the scores table during the warm up
* Resume the attack order when going in warm up during a match

#### Heroes
* Show a "Press F6 once you're ready" message during the warm up
* Show the correct attack order in the scores table during the warm up
* Show the ready state of the players in the scores table during the warm up
* Deleted the attack armor count in the UI
* Show markers for the spectators (Nucleus, Goal A/B/C)
* Markers are more noticeable
* Resume the attack order when going in warm up during a match

#### Siege
* New game mode
* 3 maps

#### Time Attack
* Checkpoint are reset when going in spectator mode (could cheat because of that)
* Show the name of the winner at the end of the map, even if he's offline or in spectator
* Remove the "Rank x/x" message at the end of a map

