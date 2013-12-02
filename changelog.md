<a id=""></a>
---------------------------------

[Commit on GitHub]()

### Major features
* new landmark API
* new action API
* nouveau tie break sur Elite
* Press f8 in Elite to customize UI
* Nouveau TitlePack Siege
* Multiclans sur Royal
* New ScoresTable lib with custo XML
* MiniMap library
* TrackMania scripts

### Modes

#### ShootMania/ModeBase
* Function MB_PlayersPresentationSequence(): can now be interrupted by a vote next/restart map. There's also a new +++PlayersPresentationLoop+++ label inside the loop.
* The outro sequence doesn't exist anymore.
* The ScoresTable2 library is now included in ModeBase by default.
* MB_SetScoresTableStyleFromXml(): allow to define a custom style for the scores table.

#### ShootMania/Battle
* Fix the UI rules bug. The rules are now reset at each new map.
* Lib ScoresTable2 integration.
* Use the new Landmark API.

#### ShootMania/Combo
* Lib ScoresTable2 integration.
* Send an XmlRpc callback on warm up start and end.
* Use the new Landmark API.
* Use the new Action API.
* Fixed the combo bug when starting a game with less players than the maximum amount.

#### ShootMania/ModeSport (Base for Elite and Heroes)
* In matchmaking mode, if all the players from a team are allied they can choose their attacking order before the beginning of the map.
* Compatibility with the temporary allies of the matchmaking lobby.
* Addition of the S_RestartMatchOnTeamChange setting (default value: False). The match will be restarted if the players from the previous map are not the same after map change.
* Hit details of each player in the EndTurn XmlRpc callback.
* Send an XmlRpc callback on warm up start and end.
* Addition of the S_UseLegacyCallbacks setting to enable the JSON callbacks (default value: True).
* Better winning condition check. There's now a double loop on the events array to discard OnHit and OnArmorEmpty events to prevent two winning conditions to be activated at the same time.
* Removal of the tie break system. It's replaced by a hard points limit, instant win for the team reaching the limit first. Default is 15 points on normal map and 20 points on decisive map (last map of a BO).
* Replacement of S_SleepMultiplier by the S_QuickMode setting (default value: False). When turned to True all waiting times will be divided by 2.
* Addition of the S_DisplaySponsors setting (default value: True). Display or not the attacker sponsor at the bottom of the screen in spectator mode.
* Addition of a #Command to force the reload of the clublinks.
* Reload the clublinks at each player change during the warm up.

#### ShootMania/Elite
* Changes from ModeSport (see above).
* Removal of the Beta2 setting.
* Default number of points to win a map is now 9 instead of 6.
* Addition of the HitDist on the OnHit XmlRpc callback of all weapons.
* Addition of the HitDist on the OnNearMiss XmlRpc callback.
* A player living a game before the end of the map won't win LP at the end.
* Correctly displays the loss of LP on the scores table.
* Correctly displays the echelons on the scores table.
* Displays the points limits in the scores table.
* Use the EliteStats library to save the end state of the turn (win/loss of atk, remaining atk armors, renaming def).
* Better UI message management. The "The goal can now be captured." message is now a StatusMessage and not a BigMessage anymore.

#### ShootMania/Heroes
* Translations fix

#### ShootMania/Joust
* Default time limit setting is now 45 seconds instead of 60 seconds.
* Lib ScoresTable2 integration.
* Send an XmlRpc callback on warm up start and end.

#### ShootMania/Melee
* It's now possible to turn off the points or time limitations in the settings.
* Lib ScoresTable2 integration.
* Use the new Landmark API.

#### ShootMania/Realm
* Lib ScoresTable2 integration.

#### ShootMania/Royal
* Multi teams mode. If there's enough players on a map they will be divided in several teams. The rules are the same than in classic Royal with some specificities:
  * There's as much team as spawns block.
  * All players are spawned at the same time in their respective team spawn block.
  * Players in the same team can't eliminate each other.
  * Once only one team remains, the game becomes again a free for all and everyone can eliminate each other.
* Lib ScoresTable2 integration.
* Small UI improvements.

#### ShootMania/RoyalExp
* Fixed a bug that could prevent players to see the level up UI.

#### ShootMania/Siege
* Complete rewrite of the Siege mode. The intermediate Goals are replaced by Gates. For each defender spawn you can now have one or several Gates that stop the progression of the attackers until they destroy it.
* The previous mode is still here but is now renamed SiegeV1. The new mode is called Siege.
* SiegeV1 will be compatible with the SiegeArena et SiegeV1Arena MapType while the new Siege will be compatible only with the SiegeV2Arena.

#### ShootMania/SiegeV1
* Lib WeaponSelection2 integration.
* New UI.
* Lib ScoresTable2 integration.
* Use the new Landmark API.
* The mode is compatible with the new Gates blocks.
* The script is now MatchMaking ready.

#### ShootMania/TimeAttack
* Lib ScoresTable2 integration.
* Lib Layers2 integration.

#### TrackMania/Cup
* Script conversion of the Cup mode.

#### TrackMania/Laps
* Script conversion of the Laps mode.

#### TrackMania/ModeBase
* Basic mode structure for TrackMania.
* Integration of the Clublink library.
* Integration of the WarmUp library.
* Automated end map sequence.

#### TrackMania/RoundsBase
* Basic mode structure for TrackMania rounds modes (Rounds, Cup, Team).
* Setting S_UseTieBreak: allow a map to end on a tie or continue to play until a winner is found.

#### TrackMania/Rounds
* Script conversion of the Rounds mode.

#### TrackMania/Team
* Script conversion of the Team mode.
* Setting S_PointsGap: minimal points gap between the two teams when one of them reach the points limit.

#### TrackMania/TimeAttack
* Script conversion of the TimeAttack mode.

### Libraries

#### Anchor
* Compatibility with TrackMania.
* Complete rewrite of the library with a lot of new functionalities. The old functions should still be working.

#### Clublink
* Compatibility with TrackMania.
* Function Updated(): return True if the clublinks were updated since the last call to this function.
* Functions Reset() and ResetAll(): allow to reset the clublink of one or all clans.

#### Color
* Function HexToRgb(): convert an hexadecimal Text color to an RGB Vec3 color.
* Function HexToHsv(): convert an hexadecimal Text color to an HSV Vec3 color.

#### Interface
* Compatibility with TrackMania.
* Improvements on the visual of the Slider module.

#### Json
* Function StringifyMinimal() for the events: do not send the MissDIst parameter anymore. 

#### Layers
* This library is now deprecated, use Layers2 instead.
* Compatibility with TrackMania.
* Function SetType(): allow to change the type of a layer.

#### Layers2
* Updated version of the previous Layers library.
* Compatibility with TrackMania.
* Functions Create() now return a CUILayer instead of a Ident.
* Function GetName() to get the name of a layer from its Id or from the Layer object.
* Functions Destroy() / Create() / Attach() / Detach() / Update() do not return a Boolean anymore (Void instead).
* Functions Attach() / Detach() / DetachAll() / IsMissing() can take a CPlayer as argument instead of an Ident of player.
* Functions AttachReplay() / DetachReplay() to add a layer in the replay layers array.
* Functions SetVisibility() / Show() / Hide() to hide or show a layer.
* Function Get() to get a layer from its name or id instead of GetFromName() and GetFrameId().

#### Map
* New library to deal with the new Landmark API.
* Function GetMapTypeVersion() to get the version number of the MapType used to validate the map. Be careful as it's up to the MapType to save this version number. All Nadeo MapType do it, but that might not be the case of user created scripts at first.
* Several functions to manipulate the MapLandmarks:
  * Function GetLandmarkXXX() to get a landmark with the XXX component from its Tag and Order
  * Function GetXXX() to get a XXX landmark component from its Tag and Order
  * Function GetXXXCount() to get the number of XXX landmark component in the map

#### MapType
* Function SetVersion(): save the version number of the MapType in the map metadata.
* Function GetVersion(): get the version number of the MapType used from the map metadata.

#### Message
* Compatibility with TrackMania.
* Functions SetDefaultBigMessage() / SetDefaultStatusMessage() / SetDefaultAllMessages(): allow to set a default message to display when no timed message are shown.

#### MiniMap
* New library to create a radar/minimap.
* Marker functionality to add specific points on the minimap.
* Ping functionality to highlight a point on the minimap to all the players.
* Customization of each point picture/size/color/visibility.
* And much more ... Read the documentation in the library to see all the possibilities.

#### Mode
* Function PlaySound(): allow to play a sound to all players.

#### ScoresTable2
* Updated version of the previous ScoresTable library.
* Compatibility with TrackMania.
* [Server side customization]({{ site.url }}/dedicated-server/customize-scores-table.html) with an XML file.
* You can now create or destroy any number of columns (even the default ones).
* Several predefined and easy to use columns are included (points, best time, nickname, maniastars, avatar, ...).
* There's also several predefined styles for the scores table. So you can in one line create a scores table with a number of default columns. eg: SetStyle("LibST_SMBaseTeams") and you'll have a scores table ready for teams mode. The styles can be combined with each other with several call to the SetStyle() function.
* Each column can have its own style (textstyle, size, color, alignment, ...).
* Each column can have a custom script associated with it if you want to create more advanced columns (eg: changing the color of the columns depending of its value, updating the columns values from the UI instead of the game mode script, ...).
* The columns can be reordered easily (points first, avatar in the middle, nickname last, ...).
* The footer only contains one customizable text now (with a optional custom script).
* The name of the server the player is playing on is displayed in the footer.
* The scores table can have any number of players columns or row given there's enough place to display them (you can create a scores table with three players columns in team mode if you want).
* The background of the scores table is customizable and you can make it change depending on the environment the player is. It's useful in TrackMania if your mode is playable in Valley, Canyon and Stadium and that you want different visual without having to write a version of the mode for each environment.
* You can add a foreground image that will be display over the scores table.
* The background and foreground are colorizable.
* And much more ... Read the documentation in the library to see all the possibilities.

#### TabsServer
* Compatibility with TrackMania.

#### Tips
* This library is still a work in progress. It's used to display tips to players.

#### Top
* This library is now deprecated, use Top2 instead.

#### Top2
* Compatibility with TrackMania.
* Function UnsetRecord(): Allow to remove a player from a top.
* Share the logins of the players in the top with the Interface library.
* UI Improvements.

#### Victory
* Function ForceMatchWinner(): Force the winner of a match.

#### ShootMania/ScoresTable
* This library is now deprecated, use ScoresTable2 instead.
* Check that the diodes exist on the side of the scores table before attempting to colorize them in the script.

#### ShootMania/Debug
* A toolbox for debugging ShootMania modes. It's still a work in progress.
* Direct access to the "Styles"/"ML-Styles" manialink.
* Add/Remove bots on the fly from the UI.
* Turn on/off the collisions between players.
* Turn on/off the weapons hit detection between players.
* Turn on/off the ally system.
* Change the EndTime value.

#### ShootMania/MultiClans
* A library to manage more than 2 clans.

#### ShootMania/RightBoard
* A small library to display informations on the right of the screen.

#### ShootMania/SM
* Functions SpawnPlayer(): two versions of each function for the compatibility with the new landmark API.

#### ShootMania/SpawnScreen
* Better scores sorting in the small scores table.

#### ShootMania/WaitingQueue
* Small UI fix on text size.

#### ShootMania/WarmUp
* This library is now deprecated, use WarmUp2 instead.

#### ShootMania/WarmUp2
* Functions Enable() / Disable(): allow to enable or disable the order selection for a group.
* Function GroupExists(): check if a group exists.
* Function DestroyGroup(): destroy a group.
* Function Stop(): now return True if the a map vote or server stop is requested.
* Better reset of the ready state of the players after a script restart.
* Small UI fix.

#### ShootMania/WeaponSelection
* This library is now deprecated, use WeaponSelection2 instead.

#### ShootMania/WeaponSelection2
* Rewrite of the WeaponSelection library. It now works like the WarmUp2 library. You can create groups of players that will have to choose a weapon in defined list.

#### ShootMania/XmlRpc
* Functions BeginWarmUp() / EndWarmUp(): send a callback at the beginning and the end of the warm up.
* Function Siege_OnCapture(): specific callback for the capture of a Gate/Goal in Siege.
Function OnCapture(): now use the Landmark API.

#### ShootMania/Elite/ElitePractice
* Lib ScoresTable2 integration.

#### ShootMania/Elite/EliteStats
* The EliteStats library saves the end state of the turn in Elite (win/loss of atk, remaining atk armors, renaming def).

#### TrackMania/TM2
* Rewrite the previous TM library.
* The ladder related functions are now in the Mode library.
* You'll find several functions to manage the player spawning in this lib.

#### TrackMania/UI
* Several UI modules to use in TrackMania.
* SmallScoresTable module: displays the small scores table on the right side of the screen at the end of the round.
* TimeGap module: displays the time gap between the players on the bottom of the screen.

#### TrackMania/WarmUp
* WarmUp library for TrackMania. It's included by default in ModeBase.

#### TrackMania/XmlRpc
* TrackMania counterpart of the ShootMania XmlRpc library.
* Send a script callbacks for the different TrackMania events: OnStartLine, OnWayPoint, OnGiveUp, OnRespawn, OnStunt.
* Send a script callback at the beginning and end of each ModeBase section.

### MapTypes

#### ShootMania/BattleArena
* Save the map type version in the metadata.

#### ShootMania/ComboArena
* Save the map type version in the metadata.

#### ShootMania/EliteArena
* Save the map type version in the metadata.

#### ShootMania/HeroesArena
* Save the map type version in the metadata.

#### ShootMania/JoustArena
* Save the map type version in the metadata.

#### ShootMania/MeleeArena
* Save the map type version in the metadata.

#### ShootMania/RealmArena
* Save the map type version in the metadata.

#### ShootMania/RoyalArena
* Save the map type version in the metadata.
* Small UI fix.

#### ShootMania/SiegeV1Arena
* MapType for the old Siege mode.
* Support for the new Gate block.

#### ShootMania/SiegeV2Arena
* MapType for the new Siege mode.

#### ShootMania/TimeAttackArena
* Save the map type version in the metadata.






<a id="2013-07-26"></a>2013-07-26
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

