# Stronghold-bot
Source code for my bot as I build it up. View in Raw.

SetTitleMatchMode=2
WinGet, client, ID, MapleStory

MsgBox, , Stronghold Bot, Unpatchable Stronghold Bot created by VoidedDarkness. `n`n This can work for other flat maps. `n Setup instructions: `n`n Time how long it takes to get from the right side to the left. `n Return to the right side of the map and set your attack to Shift. `n Click Start bot to activate, click Stop bot to deactivate.

Gui, Submit, NoHide
Gui, Show, w200 h 100, Stronghold Bot by VoidedDarkness
Gui, Add, Text, x70 y0,ID is %client%
Gui, Add, Button, x0 y0 vTest gTest ,Set focus
Gui, Add, Text, x10 y30,Test time:
Gui, Add, Edit, x55 y23 vTime,
Gui, Add, Button, x10 y50 vHoldAtt gHoldAtt ,Start bot
Gui, Add, Button, x70 y50 vPause gPause ,Stop Bot
Gui, Add, Text, ,Created by VoidedDarkness

return

Test:
{
WinActivate, ahk_id %client%
return
}

HoldAtt:
{
Gui, Submit, NoHide
movement := Time*1000
active :=true
sleep 400
WinActivate, ahk_id %client%
sleep 400
Send {Shift down}
sleep 100
Loop
{
	if active
	{
	Send {Left down}
	sleep movement
	Send {Left up}
	sleep 100
	Send {Right down}
	sleep movement
	Send {Right up}
	sleep 100
	}
	else
	Break
}
Send {Shift up}
return
}

Pause:
{
sleep 400
WinActivate, ahk_id %client%
sleep 400
Send {Left down}
sleep 100
Send {Left up}
sleep 100
Send {Right down}
sleep 100
Send {Right up}
sleep 100
Send {Shift down}
sleep 100
Send {Shift up}
sleep 100
active :=false
Exit
}

GuiClose:
ExitApp
