Runabc
======
2002-03-17

Preface
-------

If you are just a user of runabc.tcl, the information in
this document is probably of no interest to you. The
purpose of this document is to describe some of the obscure
sections of the script to the programmer who may be interested
in modifying or adding more code to this program.

Runabc has been in use as well as evolving over the past few
years. At this point, it consists of 4684 lines of code and
comments. If you are planning to extend this program you
need to avoid using certain variable names that are used
globally. This file lists these variables and describes
their functions, providing a little understanding on how this
program works. This description assumes that you are already
quite familiar with the operation of the program.

You should note that this document may not be up to date when
you may be reading it. The program is still growing, and
keeping the information in this file up to date to the latest
changes is a big task. Nevertheless, the program evolves slowly
a much of the information is probably valid.

Global variables and their functions
------------------------------------

`runabc_version` - contains the version number of this
program. It is written in the runabc.ini file and printed
when you press the help button when you are viewing the
table of contents. 

`runabc-date` - the date of this version. 
 
`midi`  -  This is an array used for storing all state information
that is preserved in the runabc.ini file. It contains a lot of
information set in the configuration menus and many property
pages of the program. The name of this variable is probably
not appropriate, but it would be a big job to change it. 
This global variable is used throughout the script to pass
configuration information to the many functions in the program.

`df` - Specifies the default font to use. The font is included
in every widget that shows text.

`globsel` - This variable contains the last selected item in the
table of contents list. It was used to address a bug in the
program or Tcl/Tk, when the focus was shifted away from the
table of contents list and the selected item was lost. This
problem is now gone, but this code element persists.

`exec_out` - The variable contains the return message or
messages when one or more external programs (eg. abc2ps) are
executed. These return messages are printed out when you
click the console button.

`files` - Contains the list of midi files in the tmp directory
(or midi(`midi_dir`)) that are to be played.

`yaps_ptsize` - This is a list or table of the possible page dimensions
that yaps will use to produce a PostScript file. These dimensions
match the gv (gview) page shapes (eg. letter, legal, A4, tabloid...).

`midi_type` - This is a list with a particular format which tells,
`tk_getSaveFile` to only display or write files with a "mid" extension.

`type` - Similar to `midi_type`, but specifies a file with a "abc"
extension.

`history_index` - This variable is associated with the menu items 
displayed when you click the file button.

`active_sheet` - The variable specifies which property sheet, (eg.
table of contents, config options, console, help, etc) that is
currently being displayed. The variable is used to determine which
help page to display when the help button is pressed and to remove
the old property sheet when a switch to another sheet occurs.

`fileseek` - This is an array indicating the location in the file
(in bytes) of the start of every tune in a multitune abc file.
The array is set up by the `title_index` procedure whenever a
an existing abc file is opened using the file button. This array
is used to access the information from a particular tune selected
by the user.

`hlp_overview`, `hlp_editor`, `hlp_config\_1`, etc.. contain the
text to be displayed when the help button is pressed. There
are different texts depending on the context (`active_sheet`) of
the program.

`midi_subsection`,`cfg_subsection` -- specify the choice of property
sheets associated with the ac2midi options and config menu items.

The following globals are used by "my selection editor":
 
`find_string` -  This string contains the contents of the find
entry box.

`find_barnum` - The contents of the barline entry box.

`body_start`, `body_end` - They are set by the `tag_text` procedure and
indicate the start and end of the tune's body displayed in the
abcedit window.

`keyorder`, `keymap` - They are tables used to work out assumed accidentals
associated with key signatures.

`notekey` - A table used when transposing abc tunes.

End of "my selection editor" globals
 
`window`, `chan` -- provides a method of passing a program selection
menu and channel number between procedures voice\_button and program\_select

Other globals
-------------
    drumpatches
    drumprog
    ndrums
    file_index
    gfiles
    locator
    listbox_line
    stopsearch
    matchlist
    mlocator
    barloc
