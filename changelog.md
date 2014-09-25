<a id="2014-xx-xx">2014-xx-xx</a>
---------------------------------

[Diff from previous release]()

### Modes

#### ShootMania/ModeMatchmaking
* Penalties are now managed by the matchmaking API. Thanks to that, they are now persistent and global. Persistent : if you rage quit a match and leave maniaplanet, your penalty will be applied the next time you join the lobby, even if it's one week later. Global : being penalized in one lobby means you'll be penalized in all lobbies. eg: leave a match in Elite and you will also be penalized in the Siege lobby.
* Players are not penalized for canceling a replacement anymore.
* Matchmaking api version : v7.
* Removed the following settings : S_LobbyAllowMatchCancel, S_LobbyLimitMatchCancel and S_LobbyBasePenalty.
* Removed the message warning players about matches canceling and penalties in the lobby.
* Fix : wait for player synchro before playing a new map. [see](http://forum.maniaplanet.com/viewtopic.php?p=227013#p227013)
* Fix : send the right player clan in the missing players array to avoid the SetPlayerClan() error in progressive matchmaking. [see](http://forum.maniaplanet.com/viewtopic.php?f=261&t=28998#p226648)


### Libraries

#### TrackMania/UI
* New controls on the Trackmania UI via XmlRpc. It's now possible to control (hide/show/move) most of the UI elements of Trackmania with XmlRpc. [see](http://forum.maniaplanet.com/viewtopic.php?f=470&t=28654&start=0) & [documentation](http://doc.maniaplanet.com/creation/maniascript/libraries/library-ui.html)

<a id="2014-09-10">2014-09-10</a>
---------------------------------

[Diff from previous release](https://github.com/maniaplanet/game-modes/compare/ManiaPlanet_Update_2014-07-24...ManiaPlanet_Update_2014-09-10)

### Modes

#### ShootMania/All modes
* Fix : Reset the rules in the spawn screen at the beginning of each map to avoid to fill the rules array with duplicate rules.

#### ShootMania/Battle
* Fix : Check that a player Id exists in the Players array before trying to access it. [see](http://forum.maniaplanet.com/viewtopic.php?p=227017#p227017)
* Fix : The "Attack" and "Defend" messages at the top of screen are now displayed correctly when spawning. [see](http://forum.maniaplanet.com/viewtopic.php?f=8&t=28620&p=224480#p224370)
* In spectator mode, when using the cam7 (global view) the name of the team in attack is displayed. eg : "Blue is attacking".

#### Shootmania/ModeMatchmaking
* Fix : Check that User is not Null before using it. [see](http://forum.maniaplanet.com/viewtopic.php?p=226307#p226307)
* Fix : substitutes were kicked by the match server when joining under certain conditions.

#### ShootMania/Siege
* The weapons used in atk and def during the previous round are saved even across maps.
* Fix the "LibXmlRpc_Scores" callback in Siege.

#### TrackMania/RoundsBase
* Fix the Rounds_GetPointsRepartition and Rounds_SetPointsRepartition XmlRpc callback and method. They could be invoked only during the round, now it's possible to invoke them anytime. [see](http://forum.maniaplanet.com/viewtopic.php?p=227330#p227330)

### Libraries

#### ShootMania/Debug
* New quad styles and substyles.

#### ShootMania/VoteMap
* Fix : set the correct library name in the ScriptName #Const

#### ShootMania/XmlRpc
* The "LibXmlRpc_BeginMatch" callback now return one more value. A boolean to indicate if the script was restarted or not.

#### TrackMania/XmlRpc
* The "LibXmlRpc_BeginMatch" callback now return one more value. A boolean to indicate if the script was restarted or not.


---------------------------------


<a id="2014-07-24">2014-07-24</a>
---------------------------------

[Diff from previous release](https://github.com/maniaplanet/game-modes/compare/ManiaPlanet_Update_2014-07-11...Maniaplanet_Update_2014-07-24)

### Modes

#### Shootmania/Battle
* Matchmaking enhancements : vote map, rematch and progressive matchmaking.
* The setting "S_NbPlayersPerTeam" is replaced by "S_NbPlayersPerTeamMax".
* New setting "S_NbPlayersPerTeamMin".
* "S_NbPlayersPerTeamMin" and "S_NbPlayersPerTeamMax" allow to setup the minimum and maximum number of players in a team in matchmaking.

#### Shootmania/Combo
* Matchmaking enhancements : vote map, rematch and progressive matchmaking.
* Setting "S_NbPlayersPerTeam" is replaced by "S_NbPlayersPerTeamMax".
* New setting "S_NbPlayersPerTeamMin".
* "S_NbPlayersPerTeamMin" and "S_NbPlayersPerTeamMax" controls the maximum and minimum number of players a clan must have in matchmaking.

#### Shootmania/Elite
* Setting "S_GameplayVersion" is removed. Elite now uses the same gameplay version that the other game modes.
* Matchmaking enhancement : progressive matchmaking.
* Display the matchmaking match id in the top left corner of the screen of the scores table.
* Setting "S_RequiredPlayersNb" replaced by "S_NbPlayersPerTeamMax", default value is 3.
* New setting "S_NbPlayersPerTeamMin", default value is 2.
* "S_NbPlayersPerTeamMax" and "S_NbPlayersPerTeamMin"  allow to setup the maximum and minimum number of players per team in matchmaking.

#### Shootmania/Heroes
* Rename the "S_RequiredPlayersNb" setting into "S_NbPlayersPerTeamMax" to match the one in the Elite script.

#### Shootmania/ModeMatchmaking
* New rematch feature. At the end of a match the players can vote to play another one with the same people. If enough players agree a new match starts on the same server without going through the lobby again.
* New vote map feature. At the start of the match and at the end of each map the players can vote for the next map. Each player can vote for one map, all the maps that receive a vote are placed in a pool. If a map have several votes, it will be placed the same number of time in the pool. Then one map is chosen randomly in the pool to be the next one.
* New progressive matchmaking. When there's not enough players on the lobby, the matchmaking can start a match with less players and then send substitute to complete the match line up. Eg: 5vs5 Siege need 10 players on the lobby. With progressive matchmaking, the lobby can start a match with only 4 players. Then this match will receive substitutes from the lobby until there's 10 players.
* The matchmaking function is now ran much more frequently, every 10 seconds instead of 40 seconds.
* The players connection maximum waiting time when joining the match server is reduced to 20 seconds (it was 60 seconds before the update).
* The animation of the gauge in the lobby is smoother.
* New version of the matchmaking api. The S_MatchmakingAPIUrl setting value is now "https://matchmaking.maniaplanet.com/v6".
* New setting S_MatchmakingRematchRatio, set the minimum ratio of players that have to agree to play a rematch before launching one. The value range from 0.0 to 1.0. Any negative value turn off the rematch vote. The default value is -1.0.
* New setting S_MatchmakingRematchNbMax, set the maximum number of consecutive rematch. The default value is 2.
* New setting S_MatchmakingVoteForMap, allow or not to vote for the next map. The default value is False.
* New setting S_MatchmakingProgressive, enable or disable the progressive matchmaking. The default value is False.
* Setting S_LobbyTimePerRound is removed and replaced by the S_LobbyMatchmakerTime and S_LobbyMatchmakerWait settings.
* Setting S_LobbyMatchmakerTime set the duration of the versus screen display. The default value is 8 (it was 10 before the update).
* Setting S_LobbyMatchmakerWait set the waiting time before calling the matchmaking function again. The default value is 2. So in the end the matchamking runs every (S_LobbyMatchmakerTime + S_LobbyMatchmakerWait) seconds -> 10 seconds by default.
* New setting S_LobbyMatchmakerPerRound, set how many times the matchmaking function is called before ending the current round of King of the Lobby. The default value is 6.

#### Shootmania/ModeSport
* Matchmaking enhancement : rematch and vote map.
* The duration of the podium sequence at the end of the match is not shorten by the S_QuickMode setting anymore.
* Setting "S_RequiredPlayersNb" renamed into "S_NbPlayersPerTeamMax" to match the change in the Elite script.

#### Shootmania/Siege
* Fix : when using the old capture mode, capture time won't be divided by the number of gates at the checkpoint.

#### Trackmania/TeamAttack
* Fix : use the correct ScriptName constant. Now "TeamAttack.Script.txt" instead of "TimeAttack.Script.txt". [see](http://forum.maniaplanet.com/viewtopic.php?p=221874#p221874)

#### Trackmania/TimeAttack
* Fix : the time attack mode now sends the "LibXmlRpc_BeginWarmUp" call back at the beginning of the warm up and "LibXmlRpc_EndWarmUp" at the end. Additionally it also sends all events callbacks during the warm up (eg: "LibXmlRpc_OnStartLine", "OnWayPoint", etc). [see](http://forum.maniaplanet.com/viewtopic.php?p=221954#p221954)


### Librairies

#### Interface
* Add a name to the manialink that will be displayed in the debugger.

#### VoteMap
* New library allowing to vote for the next map. The library displays a list of all the maps available on the server. Each player can vote for one map. Several players can vote for the same map. When the vote timer reach 0. Each map with at least one vote is put into a pool. If a map has several votes, it's put several times into the pool. The library will then select a random map inside the pool and set it as the next map.

#### Shootmania/Elite/EliteEndSequence
* Fix : the gauge don't increase continuously until map change under certain conditions anymore.
* Rewrite of the script animating the gauge. Added an easing and a sound on the animation.

---------------------------------


<a id="2014-07-11">2014-07-11</a>
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/8ccbd77b5a1a49edc59a586700be538eb8bb93bb)

### Modes

#### ShootMania/ModeMatchmaking
* New setting "S_LobbyBasePenalty" allowing to set a custom penalty time base. Default is now 120 instead of 90 seconds. [see](http://forum.maniaplanet.com/viewtopic.php?p=221663#p221663)


### Librairies

#### TrackMania/UI
* Fix : don't display anymore the small scores table on the right of the screen while racing in warm up mode after finishing the map a first time.

#### TrackMania/XmlRpc
* Add the total score (PlayerScore.Points + PlayerScore.PrevRaceDeltaPoints) to the LibXmlRpc_PlayerRanking callback. [see](http://forum.maniaplanet.com/viewtopic.php?p=219271#p219271)

#### ShootMania/Elite/EndSequence
* Fix : there's now an animation when loosing LP. [see](http://forum.maniaplanet.com/viewtopic.php?p=221732#p221732)
* Fix : echelon from 9.2 to 9.9 are correctly displayed. [see](http://forum.maniaplanet.com/viewtopic.php?p=221732#p221732)
* Fix : the amount of LP lost is correctly displayed.
* Fix : always display two decimals for the LP amount.

---------------------------------


<a id="2014-07-10">2014-07-10</a>
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/579c412356dfc26a257fe9b63198e721aaad2fde)

### Modes

#### ShootMania/Siege
* New setting S_AtkNbIncreaseCaptureSpeed. Select if the number of attackers on the gate increase the capture speed. It's now turned off by default.
* Fix : If a spectator was on the server at the beginning of the turn he could later join the ongoing round with 1 armor point. It's not the case anymore.
* Fix : Weapon was saved only at the end of the round and loaded after each respawn. Now weapon is saved as soon as the player change it.

#### ShootMania/Battle
* Fix : When spectating a player the "Attack/Defend" message at the top of the screen was relative to the spectator clan and not the spectated player clan. [see](http://forum.maniaplanet.com/viewtopic.php?p=221397#p221397)

---------------------------------


<a id="2014-07-09">2014-07-09</a>
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/8557231d00b773092c13dc7fe628c6af0af4e874)

### Modes

#### ModeBase
* All "synchronous" functions from the Mode library now have "asynchronous" equivalents in ModeBase. It allows to avoid calling a yield; in the library at the risk of missing important events (eg: XmlRpc events).

#### ShootMania/Battle
* The mode is now compatible with the matchmaking system, you can open your own lobby and match servers.

#### ShootMania/ModeMatchmaking
* It's now possible to show/hide on the client side the waiting screen, players list and masters list.
* Players kicked from a match won't be sent back to the match server when they rejoin the lobby. [see](http://forum.maniaplanet.com/viewtopic.php?p=219695#p219695)
* Three new XmlRpc methods to control the matchmaking function in the lobby : Matchmaking_Start, Matchmaking_Stop and Matchmaking_Force. With these it's now possible to stop/restart the matchmaking cleanly when needed (eg: before a restart/force next map).
* Fix : going to the next map after a vote won't restart the 60 seconds waiting time at the beginning of the map. [see](http://forum.maniaplanet.com/viewtopic.php?p=220073#p220073)
* Fix : going to the next map after a vote while the match was already started won't kick the players from the server anymore. [see](http://forum.maniaplanet.com/viewtopic.php?p=219976#p219976)
* Fix : a player that go from ready to unready state between the API request and response wasn't sent to its match and the match wasn't canceled. Now this player will be penalized and the match canceled properly. [see](http://forum.maniaplanet.com/viewtopic.php?p=221311#p221311)

#### ShootMania/Siege
* Each checkpoint can now be associated with one, two or three gates instead of being forced at two.
* There is 45 seconds to capture all the checkpoint's gates. A bonus of 10 seconds is awarded when capturing a gate.
* The capture time of the gates is equal to 4.5 seconds divided by the number of gates at the checkpoints. eg: 3 gates -> 1.5 seconds each, 2 gates -> 2.25 seconds each, 1 gate -> 4.5 second.
* Only 2 ammo instead of 4 for the Rocket in attack. [see](http://forum.maniaplanet.com/viewtopic.php?p=219700#p219700)
* Play a sound only on attacker elimination instead of a different sound for defender and attacker elimination. [see](http://forum.maniaplanet.com/viewtopic.php?p=219700#p219700)
* New setting S_WeaponMode. It can take one of these values : 0 -> Rocket versus Laser, 1 -> select your weapon before the turn, 2 -> switch weapon during the turn. Default value is 2.
* New setting S_GatesStopDefenders. Select if players can walk through gates or not. Default value is True, so defenders can't go through gates anymore. [see](http://forum.maniaplanet.com/viewtopic.php?p=219700#p219700)
* It's now possible to move/hide some parts of the UI by pressing F8. It's also possible to hide/show the gates/spawn markers this way. [see](http://forum.maniaplanet.com/viewtopic.php?p=219700#p219700)
* The small scores header at the top of the screen now displays the number of players remaining in each team instead of the number of checkpoints captured.


### Librairies

#### Mode
* All "synchronous" functions from this library now have "asynchronous" equivalents in ModeBase. It allows to avoid calling a yield; in the library at the risk of missing important events (eg: XmlRpc events).

#### Top2
* Fix : the library failed to access some users while updating. We now check that the user will be available before trying to access it.


### MapTypes

#### ShootMania/SiegeV2Arena
* Each checkpoint can now be associated with one, two or three gates instead of being forced at two.

---------------------------------


<a id="2014-07-02">2014-07-02</a>
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/0284efbe53c8202f79c113143f30fb40cbfedd13)

### Modes

#### ShootMania/Elite
* Initialize the dodge total from the scores table in ***InitMap*** instead of ***StartMap*** to avoid to keep the value from the previous match while waiting for the match to start in matchmaking. [see](http://forum.maniaplanet.com/viewtopic.php?p=218684#p218684)
* Use the new GetMode() function to get the current mode (free or classic) instead of accessing directly to the S_Mode setting. This function will always return a "valid" value (0 or 1) so the assert() are not necessary anymore. [see](https://github.com/maniaplanet/game-modes/issues/4)

#### ShootMania/ModeBase
* New boolean allowing to cancel an ongoing matchmaking match and start a new one.

#### ShootMania/ModeMatchmaking
* Universal lobby mode. Disable the matchmaking function on the lobby and allow players to create their own match. The lobby will then send players to a free match server.
* Fix on the "remind rules" frame of the lobby to correctly display long texts inside. [see](http://forum.maniaplanet.com/viewtopic.php?p=218668#p218668)
* Fix a bug displaying players as allies in the versus screen of the lobby even if they were not.

#### ShootMania/ModeSport
* Fix : don't restart a matchmaking match when voting for change/next map on first map. Just keep playing the same match with the same players.

#### TrackMania/ModeBase
* Replaced all calls to the Mode library "sync" functions by the same call to the new "async" function from ModeBase. It solves XmlRpc problems where call to the TriggerModeScriptEvent and TriggerModeScriptEventArray methods were ignored if they were sent a few milliseconds after map beginning/ending (during ladder communication with the master server especially).

#### TrackMania/Rounds
* Replace the custom RoundsVersion and RoundsScriptName #Const by the default Version and ScriptName. [see](http://forum.maniaplanet.com/viewtopic.php?f=489&t=27822)

#### TrackMania/RoundsBase
* New setting S_DisplayTimeDiff to hide/show time difference at checkpoint. [see](http://forum.maniaplanet.com/viewtopic.php?f=8&t=27872&p=218204#p218204)


### Libraries

#### Interface
* Fix a bug preventing to remove a slide from the slider module. [see](http://forum.maniaplanet.com/viewtopic.php?f=468&t=27899#p217310)

#### ShootMania/Debug
* New styles added to the "styles" manialink (see BgsButtons in the background category)

#### ShootMania/Elite/EliteEndSequence
* Fix: added the missing </script> node at the end of the manialink xml. That was preventing the whole UI to work as expected at the end of the map.

#### ShootMania/Elite/EliteStats
* New tracking and saving system for attack ratio.

#### ShootMania/WeaponSelection2
* Fix on the weapon selection screen. Sometimes pressing the 1, 2, 3 or 4 key didn't selected the right weapon.

#### TrackMania/TM2
* Send the "LibXmlRpc_OnStartCountDown" callback when calling the StartRace() function.
* Force the UI sequence of the player to None when spawning him on the track.

#### TrackMania/UI
* The default checkpoint crossing sound is not played anymore when the default chrono UI is hidden. So the lib now plays the sound instead.

#### TrackMania/XmlRpc
* New XmlRpc callback "LibXmlRpc_OnStartCountDown" sent when the player is spawned on the track before the 3,2,1,GO!. [see](http://forum.maniaplanet.com/viewtopic.php?f=261&t=27956&start=20#p219270)
* The "LibXmlRpc_OnRespawn" callback sends more info : player login, block id, checkpoint in race, checkpoint in lap, number of respawn. [see](http://forum.maniaplanet.com/viewtopic.php?f=261&t=27956&start=20#p219270)
* Add the total score (PlayerScore.Points + PlayerScore.PrevRaceDeltaPoints) to the LibXmlRpc_PlayerRanking callback. [see](http://forum.maniaplanet.com/viewtopic.php?f=261&t=27956&start=10#p218240)
* More details in the LibXmlRpc_PlayersRanking callback : the login, rank, best checkpoints, team id, spectator status, away status, best time, zone, points and total points of the players are separated by a colon


### Documentation
* New styles added to the "styles" manialink (see BgsButtons in the background category)

---------------------------------


<a id="2014-05-22">2014-05-22</a>
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/8e583c5b490fbc87f2b4c34d53aaaef36864b011)

### Modes

#### ShootMania/Battle
* AutoManageAFK is turned off by default.
* Fix on the U : the markers and poles helpers are now updated correctly.

#### ShootMania/Combo
* Now compatible with the new matchmaking system.
* It's now possible to hide the timers on the right of the screen while spectating.

#### ShootMania/Elite
* Display the probability that the attacker can win the round based on his number of armors, the number of defenders and the time left in the round.
* Fixed : the players lists position can now be customized during warm up.

#### ShootMania/Heroes
* Fixed : the script doesn't work on the dedicated server.

#### ShootMania/ModeBase
* Change to the S_AFKIdleTimeLimit are now taken into account in real time and not only at server restart.

#### ShootMania/ModeMatchmaking
* Players are now penalized for their first cancel by default.
* One matchmaking round last 30 seconds instead of 60 seconds.
* 60 rounds per map instead of 30.
* Canceling a match the first time is now penalized by 90 seconds of ban instead of 60 seconds.
* Each cancel after the first one will increase the penalty by 30 seconds instead of 5.
* Integration with Combo.
* Use the new version of the API (v4) with https.
* Setting S_MatchmakingErrorMessage defines a custom error message that will be displayed in the chat to inform the players when an error occurs in the matchmaking system.
* Setting S_LobbyAllowMatchCancel allows or not the players to cancel a match.
* Setting S_LobbyLimitMatchCancel, if the players are allowed to cancel a match, how many matches can they cancel before being penalized.
* Display the nickname of the player who canceled our match in the chat.
* Better management of substitutes players.
* Display the average waiting time of the players in the lobby.
* Display which players are allied in the VS screen before being sent to a match.
* Stop to ask for a substitute when a player is missing if the match end is close.
* When reconnecting to a lobby after leaving an ongoing match you'll be sent back to your match server. Canceling will result in a penalty.
* Fixed : the old scores table is not visible anymore after a map change in the lobby.
* Fixed : the players list is sorted by echelon.
* Fixed : player won't be blocked in the lobby instead of being transfered to their match server.

#### ShootMania/Royal
* AutoManageAFK is turned off by default.

#### ShootMania/Siege
* AutoManageAFK is turned off by default.
* New setting S_UseWeaponSelection : force the player to use rocket in defense and laser in defense. S_UseWeaponSwitch must be false for this setting to be taken into account.
* New setting S_CaptureThreshold : minimum time in ms a player must stand on a gate/pole to start capturing it.
* Display a gauge on the screen while capturing a gate or a pole.


### Libraries

#### CustomUI
* Setup the display key before building the UI.

#### MiniMap2
* Better initialization of the minimap.
* Functions Attach() and Detach() to control the minimap layer.

#### ShootMania/EliteStats
* New stat system : save the probability that the attacker can win the round based on his number of armors, the number of defenders and the time left in the round.

---------------------------------


<a id="2014-04-30">2014-04-30</a>
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/7ee8d63487adb32da0279a1a3c9f61a6e00853bf)

### Modes

#### ShootMania/ModeBase
* Detect map restart with the MB_MapRestarted variable.
* Added the new BeginPlaying, EndPlaying and UnloadingMap callbacks.

#### ShootMania/ModeMatchmaking
* API updated from v2 to v3.

#### TrackMania/Cup
* Support of the ForceEndRound XmlRpc script method.

#### TrackMania/Laps
* Integration of the new UI modules (chrono, checkpoint time, best and previous times).

#### TrackMania/ModeBase
* Clean the victory message at the beginning of the map. Fixed the bug where the latest winner was displayed as the winner if nobody finished the map.
* Detect map restart with the MB_MapRestarted variable.
* Added the new BeginPlaying, EndPlaying, BeginPodium, EndPodium and UnloadingMap callbacks.

#### TrackMania/Rounds
* Support of the ForceEndRound XmlRpc script method.

#### TrackMania/RoundsBase
* Integration of the new UI modules (chrono, checkpoint time, best and previous times).
* New XmlRpc script method "Rounds_ForceEndRound" to force a round to end.

#### TrackMania/Team
* Support of the ForceEndRound XmlRpc script method.

#### TrackMania/TeamAttack
* Integration of the new UI modules (chrono, checkpoint time, best and previous times).

#### TrackMania/TimeAttack
* Integration of the new UI modules (chrono, checkpoint time, best and previous times).
* Can set an infinite duration for the map.


### Libraries

#### Interface
* Clamp the team names at the correct size in the header of the players lists.

#### ShootMania/WeaponSwitch
* Don't change the weapon (and loose ammo) if the next weapon is the same as the previous one.

#### ShootMania/XmlRpc
* LibXmlRpc_BeginMap now returns the map UID and is it's a map restart or not.
* LibXmlRpc_EndMap now returns the map UID.
* New callbacks : LibXmlRpc_UnloadingMap, LibXmlRpc_BeginPlaying, LibXmlRpc_EndPlaying, LibXmlRpc_BeginPodium, LibXmlRpc_EndPodium.

#### TrackMania/UI
* Chrono module to display the timer at the bottom of the screen.
* CheckpointTime module to display the checkpoint times (with milliseconds).
* PrevBestTime module to display the previous and best time (with milliseconds).

#### TrackMania/WarmUp
* The library doesn't clear the scores anymore at the beginning and the end of the warm up.

#### TrackMania/XmlRpc
* LibXmlRpc_PlayerRanking now returns the player score and best checkpoints times.
* LibXmlRpc_BeginMap now returns the map UID and is it's a map restart or not.
* LibXmlRpc_EndMap now returns the map UID.
* New callbacks : LibXmlRpc_PlayersRanking, LibXmlRpc_PlayersScores, LibXmlRpc_PlayersTimes, LibXmlRpc_TeamsScores, LibXmlRpc_WarmUp, LibXmlRpc_TeamsMode, LibXmlRpc_UnloadingMap, LibXmlRpc_BeginPlaying, LibXmlRpc_EndPlaying, LibXmlRpc_BeginPodium, LibXmlRpc_EndPodium.
* New methods : LibXmlRpc_GetPlayersScores, LibXmlRpc_GetPlayersTimes, LibXmlRpc_GetTeamsScores, LibXmlRpc_GetTeamsMode, LibXmlRpc_GetWarmUp, LibXmlRpc_GetPlayersRanking, LibXmlRpc_SetPlayersScores, LibXmlRpc_SetTeamsScores.


### MapType

#### ShootMania/SiegeV2
* Force 2 gates per checkpoints.

---------------------------------


<a id="2014-04-24">2014-04-24</a>
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/f2618e779bd5303dc6de9272b1653990c7e351e7)

### Modes

#### ShootMania/Battle
* Check that the captured landmark is a pole in the OnCapture event.

#### ShootMania/ModeMatchmaking
* Addition of the S_LogAPIDebug setting to display the content of the API requests and responses.
* Better handling of missing players.

#### ShootMania/Elite
* The number of ForceField on the map doesn't change the capture duration of the pole anymore.
* Don't use UIManager.ResetAll() anymore.

#### ShootMania/ModeSport
* Don't use UIManager.ResetAll() anymore.

#### ShootMania/Royal
* Using a gate doesn't activate the tornado anymore.


### Libraries

#### Clublink
* Check that there's enough http slots available before creating a new request.

#### ShootMania/WarmUp2
* The UI is now hidden by default, so it's not displayed until it's initialized.

#### ShootMania/WeaponSwitch
* A lot of new functions to better control audio playback and volume.

#### TrackMania/TM2
* Force the scores table to it's default display state when using the StartRace() function.

---------------------------------


<a id="2014-04-16">2014-04-16</a>
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/1a93441022a00a68f792fc7f662113c5026b69b8)

### Modes

#### ShootMania/ModeBase
* Addition of the S_AFKIdleTimeLimit setting, allow to set a minimum idle time before the game mode set a player in spectator mode.

#### ShootMania/Elite
* Matchmaking integration.
* Removal of the UseProtectClanmates setting.
* Display the distance of the rocket dodge instead of the number of dodge.

#### ShootMania/ModeMatchmaking
* Base for creating modes with matchmaking. It's still a work in progress so it will evolve a lot in the next few weeks.

#### ShootMania/ModeSport
* Matchmaking integration.
* Addition of the S_RequiredPlayersNb setting, allow to set the number of player required to play an Elite match.
* Removal of the annoying sound after hitting a player in warm up.

#### ShootMania/Siege
* If your map contained forcefields you need to revalidate it for them to work properly.
* Matchmaking integration.
* Addition of the S_UseWeaponSwitch setting, allow the players to change weapon freely during the round instead of choosing one at the beginning.
* The map end duration is now of 25 seconds instead of 10 seconds. 
* The scores table is hidden when the podium is shown to see the players winning and loosing poses.

#### TrackMania/TeamAttack
* New mode, basically a time attack but in team.


### Libraries

#### Mode
* Addition of the EchelonToInteger() function, allow to convert an echelon to an integer (between 0 and 9).

#### ScoresTable2
* SetPlayerColor() and UnsetPlayerColor() can now take a CScore instead of a CPlayer as argument.
* The player overlay when eliminated is less opaque.
* The player map ranking is better integrated in the player card background.

#### Sound
* New library, allow to play custom sounds from a game mode script.

#### ShootMania/SM
* Addition of the GetUser() and GetScore() functions to get a CUser or a CSmScore from a player login.

#### ShootMania/WeaponSelection
* The keys to select your weapon will always be 1 or 2 and not 1 or 3 for the nucleus by example.

#### ShootMania/WeaponSwitch
* New library, allow the players to switch weapon while playing. Currently used in the new Siege mode.
* Fixed the Runtime error: [Libs/Nadeo/ShootMania/WeaponSwitch.Script.txt : 176, 33]

#### TrackMania/TM2
* Addition of the GetUser() and GetScore() functions to get a CUser or a CSmScore from a player login.

#### TrackMania/MultiClans
* New library, allow to manage more than two clans. Currently used in the new TeamAttack mode.


### MapType

#### SiegeV1
* If your map contained forcefields you need to revalidate it for them to work properly. They're not consider as gates anymore in the map type.

#### SiegeV2
* If your map contained forcefields you need to revalidate it for them to work properly. They're not consider as gates anymore in the map type.

---------------------------------


<a id="2014-04-02"></a>2014-04-02
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/b7686e32921f7a536607783d4c3a9b4bed5ebbc7)

### Modes

#### ShootMania/Elite
* Fixed a bug in the capture gauge UI script

#### ShootMania/ModeBase
* All while loop now exit if the values of ServerShutdownRequested or MatchEndRequested are set to False

#### ShootMania/SiegeV1
* Fixed the Gate.IsActivated bug
* New XmlRpc method "Siege_SetProgressionLayerPosition" to move the progression layer

#### ShootMania/Siege
* Fixed the Gate.IsActivated bug
* New XmlRpc method "Siege_SetProgressionLayerPosition" to move the progression layer

### Libraries

#### Interface
* Hide the slider background at initialization

#### Manialink
* Better draggable and tooltip modules

#### Markers
* Better documentation of the functions

#### MiniMap2
* Better Documentation of the functions

#### ScoresTable2
* Functions to hide/show the scores table individually for each player
* Functions to apply a ratio to the scores table width and height. It's now easier to change the size of the content and background together.
* Functions to change the background color of a player card.
* The customizable footer text is now top aligned instead of bottom aligned, allowing to add line breaks in the text.
* Compatibility with old user mode scripts. The library hides the default scores table in the Build() function instead of the Load() function.

#### ShootMania/XmlRpc
* New method "LibXmlRpc_GetPlayerRanking"
* New callback "LibXmlRpc_PlayerRanking"

#### TrackMania/XmlRpc
* New method "LibXmlRpc_GetPlayerRanking"
* New callback "LibXmlRpc_PlayerRanking"

---------------------------------


<a id="2014-03-25"></a>2014-03-25
---------------------------------

[Commit on GitHub](https://github.com/maniaplanet/game-modes/commit/1de5f8b9ec19ebc97c61e666ade4eb82d0bcc09c)

### Major features

#### For players
* General : New scores table (New design, display tags, display AFK, new script, ...).
* TrackMania : all game modes converted to script.
* TrackMania : basic support of clublinks.
* ShootMania : AFK management integrated in all ShootMania game modes.
* Combo : Display the respawn timers of the items in spectator mode.
* Royal : Multi teams mode. If there's enough players on a map they will be divided in several teams depending on the number of spawns (eg: 4 spawn = 4 teams).
* Siege : Complete rewrite of the mode. The intermediate Goals are replaced by Gates. For each defender spawn you can now have one or several Gates that stop the progression of the attackers until they destroy it.
* Elite : Protect your clanmates from the attacker by shooting onto them.
* Elite : More robust winning condition check.
* Elite : Removal of the tie break system. It's replaced by a hard points limit, instant win for the team reaching the limit first. Default is 15 points on normal map and 20 points on decisive map (last map of a BO).
* Elite : Save the UI (players names, scores, hits) in the replays.
* Elite : Press F8 to customize some parts of the UI.
* Elite : Removal of the Beta2 setting.


#### For scripters
* Update of the documentation on GitHub.
* New Landmark (replace the spawn/goal blocks) and Action API.
* Manialink library : easily add animations in your manialink.
* ScoresTable2 : rewrite of the previous library with more customization, flexibility and ease of use in mind.
* Layers2 library : usability improvements of the old Layer library.
* CustomUI library : create customizable user interfaces.
* Markers library : ease the creation and management of markers.
* MiniMap and MiniMap2 libraries : create and customize different types of minimaps.
* AFK library : the library can now be controlled through XML-RPC.
* Shootmania/Map library : new library to deal with the new LandMark API.
* Shootmania/MultiClans library : new library to manage more than two clans.
* TrackMania/TM2 : rewrite of the TM library with basic functions for TrackMania.


### Documentation

* [Landmarks in ManiaScript](http://maniaplanet.github.io/documentation/maniascript/general/landmarks.html)
* [Scripts XML-RPC methods and callbacks](http://maniaplanet.github.io/documentation/dedicated-server/xml-rpc-scripts.html)
* [Customize the scores table](http://maniaplanet.github.io/documentation/dedicated-server/customize-scores-table.html)
* [Script settings list](http://maniaplanet.github.io/documentation/dedicated-server/script-settings-list.html)
* [AFK library](http://maniaplanet.github.io/documentation/maniascript/libraries/library-afk.html)
* [CustomUI library](http://maniaplanet.github.io/documentation/maniascript/libraries/library-customui.html)
* [Manialink library](http://maniaplanet.github.io/documentation/maniascript/libraries/library-manialink.html)
* [Markers library](http://maniaplanet.github.io/documentation/maniascript/libraries/library-markers.html)
* [MiniMap2 library](http://maniaplanet.github.io/documentation/maniascript/libraries/library-minimap2.html)
* [ScoresTable2 library](http://maniaplanet.github.io/documentation/maniascript/libraries/library-scorestable2.html)
* [ShootMania Map library](http://maniaplanet.github.io/documentation/maniascript/libraries/library-shootmania-map.html)
* The "Styles" manialink (in-game) has been updated with 2 new categories : UIConstructionBullet_Buttons and UIConstruction_Buttons2


### Modes

#### ShootMania/ModeBase
* Function MB_PlayersPresentationSequence(): can now be interrupted by a vote next/restart map. There's also a new +++PlayersPresentationLoop+++ label inside the loop.
* The outro sequence doesn't exist anymore.
* The ScoresTable2 library is now included in ModeBase by default.
* MB_SetScoresTableStyleFromXml(): allow to define a custom style for the scores table.
* Addition of two new labels: +++BeforeLoadMap+++ and +++AfterUnloadMap+++.
* Addition of the MB_UseOnNewLabels to disable the ***OnNewPlayer/Spectator/Bot+++ labels.
* The AFK management is now integrated in this script and turn off by default with the setting S_AutoManageAFK.

#### ShootMania/Battle
* Fix the UI rules bug. The rules are now reset at each new map.
* Lib ScoresTable2 integration.
* Use the new Landmark API.
* Use the new Layers2 library.
* Moved the AFK management to the ModeBase

#### ShootMania/Combo
* Lib ScoresTable2 integration.
* Display the respawn timers of the items in spectator mode.
* Send an XmlRpc callback on warm up start and end.
* Use the new Landmark API.
* Use the new Action API.
* Use the new Layers2 library.
* Use the group timers of the WarmUp2 library.
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
* Use the new Layers2 library.
* Use the new landmark API.
* Lib ScoresTable2 integration.
* Use the groups timers functionality from the WarmUp2 library.

#### ShootMania/Elite
* Changes from ModeSport (see above).
* UseProtectClanmates activated, you can shoot on your clanmates to protect them.
* Save the UI (players names, scores, hits) in the replays.
* Display the number of rockets dodges of the attacker.
* Removal of the Beta2 setting.
* Default number of points to win a map is now 9 instead of 6.
* Addition of the HitDist on the OnHit XmlRpc callback of all weapons.
* Addition of the HitDist on the OnNearMiss XmlRpc callback.
* A player living a game before the end of the map won't win LP at the end.
* Correctly displays the loss of LP on the scores table.
* Correctly displays the echelons on the scores table.
* Displays the points limits in the scores table.
* Display the player with the most rocket dodge in the scores table.
* Displays the number of armors of the attacker on the bottom right of the screen.
* Press F8 to customize some parts of the UI.
* Better UI message management. The "The goal can now be captured." message is now a StatusMessage and not a BigMessage anymore.
* Use the new landmark API.
* Use the new Layers2 library.

#### ShootMania/Heroes
* Translations fix
* Use the new Layers2 library.
* Use the new landmark API.
* Lib ScoresTable2 integration.

#### ShootMania/Joust
* Default time limit setting is now 45 seconds instead of 60 seconds.
* Lib ScoresTable2 integration.
* Send an XmlRpc callback on warm up start and end.
* Use the new Layers2 library.
* Use the new landmark API.

#### ShootMania/Melee
* It's now possible to turn off the points or time limitations in the settings.
* Lib ScoresTable2 integration.
* Use the new Landmark API.

#### ShootMania/Realm
* Lib ScoresTable2 integration.
* User the new Layers2 library.
* Use the new landmark API.

#### ShootMania/Royal
* Multi teams mode. If there's enough players on a map they will be divided in several teams. The rules are the same than in classic Royal with some specificities:
  * There's as much team as spawns block.
  * All players are spawned at the same time in their respective team spawn block.
  * Players in the same team can't eliminate each other.
  * Once only one team remains, the game becomes again a free for all and everyone can eliminate each other.
* Lib ScoresTable2 integration.
* Small UI improvements.
* User the new Layers2 library.
* Moved the AFK management to the ModeBase.

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
* Moved the AFK management to the ModeBase script.

#### ShootMania/TimeAttack
* Lib ScoresTable2 integration.
* Lib Layers2 integration.
* Use the new landmark API.
* Attach all the layers to UIAll instead of individual players.

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

#### CustomUI
* New library allowing to create Manialinks customizable by the players. See the [documentation](http://maniaplanet.github.io/documentation/maniascript/libraries/library-customui.html) for more info.

#### Interface
* Compatibility with TrackMania.
* Improvements on the visual of the Slider module.

#### Json
* Function StringifyMinimal() for the events: do not send the MissDist parameter anymore.
* Function StringifyMinimal() for the new CSmMapLandmark class.

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
* Function DestroyAll() to destroy all the layers created with the library

#### Manialink
* Utilities functions for Manialinks. At the moment the major features are the animations, tooltips and draggable modules. See the [documentation](http://maniaplanet.github.io/documentation/maniascript/libraries/library-manialink.html) for more info.
* An example manialink is available ingame at this address : `librarymanialink`.

#### Map
* Removed and replaced by TrackMania/Map.Script.txt and ShootMania/Map.Script.txt

#### MapType
* Function SetVersion(): save the version number of the MapType in the map metadata.
* Function GetVersion(): get the version number of the MapType used from the map metadata.
* Function SetObjectivesFromAuthorTime() for TrackMania. Set the time objectives of a map based on the author time
* Function ObjectivesAreValid() for TrackMania. Check if the objectives times are valid.

#### Markers
* New library to ease the creation and management of xml markers. See the [documentation](http://maniaplanet.github.io/documentation/maniascript/libraries/library-markers.html) for more info.

#### Message
* Compatibility with TrackMania.
* Functions SetDefaultBigMessage() / SetDefaultStatusMessage() / SetDefaultAllMessages(): allow to set a default message to display when no timed message are shown.
* New overloads of SendBigMessage() and SendStatusMessage to send a message to a whole clan.

#### MiniMap
* New library to create a custom radar/minimap.
* Marker functionality to add specific points on the minimap.
* Ping functionality to highlight a point on the minimap to all the players.
* Customization of each point picture/size/color/visibility.

#### MiniMap2
* New library to create a minimap using the built-in mini map feature. See the [documentation](http://maniaplanet.github.io/documentation/maniascript/libraries/library-minimap2.html) for more info.

#### Mode
* Function PlaySound(): allow to play a sound to all players.
* Function Solo_SetNewRecord() for TrackMania.

#### ScoresTable2
* Updated version of the previous ScoresTable library.
* Compatibility with TrackMania.
* [Server side customization](http://maniaplanet.github.io/documentation/dedicated-server/customize-scores-table.html) with an XML file.
* You can now create or destroy any number of columns (even the default ones).
* Several predefined and easy to use columns are included (points, best time, nickname, maniastars, avatar, ...).
* There's also several predefined styles for the scores table. So you can in one line create a scores table with a number of default columns. eg: SetStyle("LibST_SMBaseTeams") and you'll have a scores table ready for teams mode. The styles can be combined with each other with several call to the SetStyle() function.
* Each column can have its own style (textstyle, size, color, alignment, ...).
* Each column can have a custom script associated with it if you want to create more advanced columns (eg: changing the color of the columns depending of its value, updating the columns values from the UI instead of the game mode script, ...).
* The columns can be reordered easily (points first, avatar in the middle, nickname last, ...).
* The footer only contains one customizable text now (with an optional custom script).
* The name of the server the player is playing on is displayed in the footer.
* The scores table can have any number of players columns or row given there's enough place to display them (you can create a scores table with three players columns in team mode if you want).
* The background of the scores table is customizable and you can make it change depending on the environment the player is. It's useful in TrackMania if your mode is playable in Valley, Canyon and Stadium and that you want different visual without having to write a version of the mode for each environment.
* You can add a foreground image that will be display over the scores table.
* The background and foreground are colorizable.
* Function Show() / Hide() / Attach() / Detach() to manipulate the scores table layer.
* Possibility to display the tags of the players in a column.
* Display a new icon under the players who are AFK.
* And much more ... See the [documentation](http://maniaplanet.github.io/documentation/maniascript/libraries/library-scorestable2.html) for more info.

#### TabsServer
* Compatibility with TrackMania.
* Addition of an Unload() function.

#### Tips
* This library is still a work in progress. It's used to display tips to players.

#### Top
* This library is now deprecated, use Top2 instead.

#### Top2
* Compatibility with TrackMania.
* Function UnsetRecord(): Allow to remove a player from a top.
* Share the logins of the players in the tops with the Interface library.
* UI Improvements.

#### Victory
* Function ForceMatchWinner(): Force the winner of a match.

#### ShootMania/AFK
* It's now possible to control the library through XmlRpc. Check the [documentation](http://maniaplanet.github.io/documentation/maniascript/libraries/library-afk.html).

#### ShootMania/Debug
* A toolbox for debugging ShootMania modes. It's still a work in progress.
* Direct access to the "Styles"/"ML-Styles" manialink.
* Add/Remove bots on the fly from the UI.
* Turn on/off the collisions between players.
* Turn on/off the weapons hit detection between players.
* Turn on/off the ally system.
* Change the EndTime value.

#### ShootMania/Map
* New library to deal with the new Landmark API.
* Function GetMapTypeVersion() to get the version number of the MapType used to validate the map. Be careful as it's up to the MapType to save this version number. All Nadeo MapType do it, but that might not be the case of user created scripts at first.
* Several functions to manipulate the MapLandmarks:
  * Function GetLandmarkXXX() to get a landmark with the XXX component from its Tag and Order
  * Function GetXXX() to get a XXX landmark component from its Tag and Order
  * Function GetXXXCount() to get the number of XXX landmark component in the map

#### ShootMania/MultiClans
* A library to manage more than 2 clans.

#### ShootMania/RightBoard
* A small library to display informations on the right of the screen.

#### ShootMania/ScoresTable
* This library is now deprecated, use ScoresTable2 instead.
* Check that the diodes exist on the side of the scores table before attempting to colorize them in the script.

#### ShootMania/SM
* Functions SpawnPlayer() : two versions of each function for the compatibility with the new landmark API.
* Function GetPlayer() : find a player from its login.

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
* Function SetGroupTimer(): link the number of players present/ready in groups to a timer to end the warm up.
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
* Addition of the WarmUp_GetStatus method and WarmUp_Status callback to know if a mode use the WarmUp library.

#### ShootMania/Elite/ElitePractice
* Lib ScoresTable2 integration.
* Use the new Layers2 library.
* Use the new landmark API.

#### ShootMania/Elite/EliteStats
* The EliteStats library saves the end state of the turn in Elite (win/loss of atk, remaining atk armors, renaming def).

#### TrackMania/Map
* Utilities functions for TrackMania maps.

#### TrackMania/TM2
* Rewrite the previous TM library.
* The ladder related functions are now in the Mode library.
* You'll find several functions to manage the player spawning in this lib.
* Function GetPlayer() : find a player from its login.
* Function TimeToText() : convert an Integer time (milliseconds) into a Text time (hh:mm:ss:mmm)
* Function TextToTime() : convert a Text time into an Integer Time
* Functions InjectMLTimeToText() and InjectMLTextToTime() to add this functionalities into ManiaLink scripts.

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
* Reset all the anchors to their default properties when loading the map type.

#### ShootMania/RealmArena
* Save the map type version in the metadata.

#### ShootMania/RoyalArena
* Save the map type version in the metadata.
* Small UI fix.

#### ShootMania/SiegeArena
* Removed and replaced by SiegeV1Arena and SiegeV2Arena

#### ShootMania/SiegeV1Arena
* MapType for the old Siege mode.
* Support for the new Gate block.

#### ShootMania/SiegeV2Arena
* MapType for the new Siege mode.

#### ShootMania/TimeAttackArena
* Save the map type version in the metadata.

---------------------------------


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

