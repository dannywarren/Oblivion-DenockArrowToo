DenockArrowToo

Denock a readied arrow by pressing the ready/sheath weapon key.

version:	1.00
author:		Danny Warren
email:		danny@dannywarren.com
github:		https://github.com/dannywarren/Oblivion-DenockArrowToo


--

ABOUT:

An expert marksman would never fire an arrow blindly in to the ground!

By default, this mod uses whatever key or mouse button you have the 
"ready/sheath weapon" control set to, but you can change it to use whatever
control you prefer (see the CONFIGURATION section below).

This mod is similar to the existing "Denock Arrow" mod by scruggs, but has
been coded from scratch to take advantage of some of the newer features
available in OBSE.  Thanks scruggs!  I peeked at your code a bit while making
this, and you already did the hard work of figuring out how to cancel an arrow.

The major differences between this mod and "Denock Arrow" are:

* Uses the new OnBowAttack and OnBowRelease event handlers in OBSE, instead of
  tracking the arrow and bow state by looking at mouse clicks or key presses

* Fixes the "denock on walk backwards" bug some people (including me) were
  having with "Denock Arrow"

* Lets you configure which control key to use for denocking an arrow

* Uses oblivion's configured control scheme, so changes made to oblivion's
  controls should take effect immediately

* Tracks the denock state as a global variable, so that is persists across
  saves and reloads (I have a bad habit of saving the game with an arrow
  pointed right at an enemy, whoops)


--

INSTALLING:

This mod requires OBSE v0020 or later.
See: http://obse.silverlock.org

To install this mod, copy DenockArrowToo.esp to your oblivion data folder.


--

CONFIGURATION:

DenockArrowToo uses oblivion's currently defined controls to determine which
key or mouse button to use when denocking an arrow.

By default, it uses whatever you have the "ready/sheath weapon" key set to.

This value is global and will persist in your save files, so you should only
have to set it once if you do not like the default.

If you wish to change which control is responsible for denocking an arrow, you
can do so by setting the DenockArrowKey variable in the console.

A list of available control key codes are here:
http://cs.elderscrolls.com/constwiki/index.php/IsControlPressed#Control_IDs

For example, if you wanted to set denock to the "grab" key, open the console
and type:

  set DenockArrowKey to 28

To put it back to the default of "ready/sheath weapon" key, open the console
and type:

  set DenockArrowKey to 8

To see what the denock key is currently set to, open the console and type:

  show DenockArrowKey

A bit of warning!  You are indeed free to use any control key you want, but
be careful about using ones that still serve another purpose while an arrow
is readied.  The grab key will still grab an item if you are pointing at it,
though probably not long enough for you to even notice you grabbed it.

However, imagine what kind of trouble you could get in if you set it to one of
the walk keys, or even worse - the attack key itself.

I chose "ready/sheath weapon" as the default key for a reason, as it does
absolutely nothing while an arrow is nocked (well, that and it feels right to
me to "sheath" an arrow, and then possibly tap that key a second time to sheath
my bow as well).


--

TROUBLESHOOTING:

You can check the state of the mod by viewing the DenockArrowState variable in
the console.

Open the console and type:

  show DenockArrowState

Currently, the following values are possible:

  -1: Initial state, our script hasn't interacted with anything yet
   0: Bow is not out or arrow is not readied, denocking disabled
   1: Bow is out, arrow is readied, denocking is possible
   2: Currently denocking an arrow

If the state doesn't seem to match up with what you see on screen or is somehow
stuck, you can reset the state by opening the console and typing:

  set DenockArrowState to -1

If the attack control somehow gets stuck in a disabled state, you can force the
denocking routines to run and clean themselves up again by opening the console
and typing:

  set DenockArrowState to 2


--

CHANGELOG:

1.00  2011.04.20
  
  * initial release

