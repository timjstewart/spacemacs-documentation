# Spacemacs #
## Buffers ##
### Go to the Messages buffer ###

Press `SPC b m` a to show the Messages buffer.

### Go to the Scratch buffer ###

Press `SPC b s` a to show the Scratch buffer.

### Erase the Current buffer ###

Press `SPC b e` and you will be prompted to see if you want to erase the current buffer.

#### Dedicating Buffers/Windows ####

##### Window to Buffer #####

Press `SPC w t` to dedicate the current window to the current buffer.  This is helpful when you have an important buffer that you don't want to get replaced by another buffer.

##### To dedicate a window to its Purpose #####

Press `SPC r d` to dedicate the current window to its current purpose.

### Buffer Menu ###

Press `SPC b .` to get a transient menu that has some helpful options you can run to navigate, kill, bury, and relocate buffers.

### IBuffer ###

Press `SPC b I` to open Ibuffer.  Ibuffer has lots of functionality.  You can mark buffers and save, revert, kill, etc. marked buffers.

### Toggle read-only state ###

Press `SPC b w` to toggle the read-only state of the current buffer.  This has interesting behavior in a Dired buffer.  It makes your directory editable.

### Reopen last closed buffer ###

Did you accidentally close a buffer?  Press `SPC b u` and the last buffer you closed will re-open.  This won't bring back changes made to a buffer if you didn't save them and deleted the buffer.

### Narrow ###
#### To selected region ####

Press `SPC n r` to narrow to the selected region

#### To current function ####

Press `SPC n f` to narrow to the current function.

#### Widen ####

Press `SPC n w` to widen to the entire buffer.

### Search All Buffers ###

Press `SPC r b` to search for a string in all open buffers.

### Insert from Kill Ring ##

Press `SPC r y` to select text from the kill ring and paste it into the current buffer.

## Files ##
### Delete the current file ###

Press `SPC f D` and you will be prompted to delete the current buffer's file.  If you proceed with the delete, the current buffer will be deleted.


### Yank parts of the file path. ###

To yank the full path to the current buffer's file, press `SPC f y y`.

To yank the directory of the current buffer's file, press `SPC f y d`.

To yank the file name of the current buffer's file, press `SPC f y n`.

To yank the file name (without the file extension) of the current buffer's file, press `SPC f y N`.

### Open files in an external application ###

Press `SPC f o` to open the current buffer's file in an external application.

### Rename/Move the current file ###

Press `SPC f R` and you will be prompted for a directory and filename to rename the file to.  If any directories in the path you supply don't exist, Emacs will offer to create them for you.

### Create a temp file ###

If you want to create a temp file to experiment on, press `SPC f J` and you will be prompted for a file extension.  If you enter an extension and press `ENTER`, Emacs will create a junk file for you and visit that file.

## Text Files ##
### Copy the selected lines and comment them out. ###

If you've ever wanted to make some experimental changes but "keep a backup", of the lines, select the lines you want to modify and press `g y`.

#### Hiding comments ####

Want to temporarily hide comments to focus on the code?  Press `SPC c h` to hide comments.  Press the same sequence again to reveal the comments.  Of course, this is only useful if the code has comments.

#### Errors ####

To see the list of errors for the current buffer, press `SPC e l`.  If you want to see the errors and navigate through the error list, press `SPC e L` instead.

To see a transient menu that lets you easily navigate your errors in the current buffer, press `SPC e .`.

### Dragging Text ###

#### Up ####

Press `SPC x K`.  You can repeatedly press `k` and `j` to move the text up and down respectively.

#### Down ####

Press `SPC x J`.  You can repeatedly press `j` and `k` to move the text down and up respectively.

### Exchange two regions of text ###

1. Select the first region.
1. Press `g x`.
1. Select the second region.
1. Press `g x`.

### Enter Insert Mode at Last Insertion Point ###

Press `g i`.

### Surrounding Text ###

#### In Visual Mode ####

To surround the selected text:

1. Select text in visual mode.
1. Press `s` key.
1. Press a character like '(', ')', '"', or even an XMl tag like "<div>".

For character pairs that have a different opening and closing character, use the
closing character to avoid adding additional spaces.

Examples:

The [ and ] characters represent the selected region:

```
Before:

The [quick] brown fox.

After:

The "quick" brown fox.
```

```
Before (the entire line is selcted using Shift-v):

[The quick brown fox.]

After:

"
The quick brown fox.
"
```

```
Before:

The [quick
brown] fox.

After:

The "quick
brown" fox.
```

#### In Normal Mode ####

Similar to visual mode but the key sequences are different.

1. Instead of 's' use 'ys'.
1. Instead of 'gS' use 'yS'.

To change the surrounding characters use the 'cs' key sequence.  Just put the point (represented by the '|' character) on the first of the surrounding strings.  Then press the current surrounding character and then the surrounding character you want.

Examples:

```
Before:

The |'quick' brown fox.

After:

The "quick" brown fox.

```

```
Before (type 'cs<' to change the tags and make sure to enter the angle brackets (e.g. "<quote>")):

The |<bold>quick</bold> brown fox.

After:

The <quote>quick</quote> brown fox.

```

To delete the surrounding characters us the 'ds' key sequence.

Examples:

```
Before:

The |"quick" brown fox.

After pressing the `ds"` key sequence:

The quick brown fox.

```

#### Multiple Lines ####

Unlike the last tip, this one forces the surrounding text to be on their own lines.

1. Select text in visual mode.
1. Press the `gS` key sequence.
1. Press a character like '(', ')', '"', or even an XMl tag like "<div>".

This is especially helpful for Scala pattern matching.  You can easily turn:

```
case Some(x) => Right(x)
```

into:

```
case Some(x) => {
  println(x)
  Right(x)
}
```

Just select the text: `Right(x)` and then type `gS{` and then indent the code to your liking.

Examples:

The [ and ] characters represent the selected region:

```
Before:

The [quick] brown fox.

After:

The "
quick
"brown fox.
```

```
Before (the entire line is selcted using Shift-v):

[The quick brown fox.]

After:

"
The quick brown fox.
"
```

```
Before:

The [quick
brown] fox.

After:

The "
quick
brown
"fox.
```


To wrap some text in a function call:

1. Select the argument(s) to the function call.
1. Hit the 'sf' key sequence.  Mnemonic: "surround Function"
1. Enter the function name.  Don't enter any parenthesis.
1. Press ENTER

Examples:

```
Before:

[name]

After (using foo as the function name):

foo(name)
```

```
Before:

valid = [flag];

After:

valid = bool(flag);

```

### Expanding the current region. ###

If you have a region selected, pressing `SPC v` will 1) expand the region and 2) display a transient menu that shows you other operations you can perform on the region.

This goes great with using the `o` key to position the point to the other end of the region.

### Visualizing the undo tree. ###

Sometimes your undo history branches.  With `SPC a u` you can navigate the undo tree and see what your buffer looks like each step of the way.  Press `q` to quit.

## Navigate ##
### To a visible Line ###

Press 'SPC j l' to enter an interface for selecting a LINE that's currently visible.

### To a visible Word ###

Press 'SPC j w' to enter an interface for selecting a WORD that's currently visible.

### To the Last Change ###

Press `SPC j c` to jump to the location of your last change.

### Buffer Hierarchy ###

Press `SPC b i` to open a buffer that shows the current buffer's hierarchy.  Navigate around and press `ENTER` to navigate to the selected portion of the document.

#### To Tag ####

* C-] - go to tag

### By interactive search ###

Press `SPC s s` to start searching through lines of the current buffer by text or regexp.

### By interactive search across all buffers ###

Press `SPC s C-s` to start searching through lines of the all buffers by text or regexp.

## Markdown ##
### Preview ###

Press `, c p` to preview the current Markdown buffer in your browser.

### Insert a Link ###

Press `, i l` to insert an HTTP link.  For example:

[go here](https://www.example.com)

## Projects ##
### To visit the project's TODOs.org file ###

Press `SPC p o` to open the current project's TODOs.org file.

### Visit Implementation/Test Code ###

Press `SPC p a` to toggle between implementation and test files.

## Git ##
### Grep with Git ###

Press `SPC g /` to use git to search files for strings.
Press `SPC g *` to use git to search files for the string at point.

### Git Blame ###

Press `SPC g b` to show who changed each line in the file last.

### Time Machine ###

Press `SPC g t` to enter Git time-machine.

## Helm ##
### Navigate History ###

Press `M-n` and `M-p` navigate forwards and backwards through history.

### Select multiple files ###

Press `C-SPC` to select the current file and move to the next file.

### Preview the Current File ###

Press `TAB` to preview the current file.

### Insert Selected file Names(s) ###

Press `C-c C-i` to insert the the Helm selection into the current buffer.

### Page Up/Down in the Helm buffer ###

Press `C-v` to scroll down and `M-v` to scroll up.

### Move the helm window ###

Press `C-t` to move the Helm window to a vertical window and back to horizontal.

## Evil/Holy Mode ##

### Switching from Emacs to Evil Mode ###

Press `M-m t E e` when you are in Emacs (holy) mode.

### Switching from Evil to Emacs Mode ###

Press `SPC t E e` when you are in Evil mode.

## Miscellaneous ##
### List processes Emacs is running. ###

Press `SPC a p` and you'll see a buffer with the processes listed in it.  Pressing `d` when point is on a process will kill that process without prompting you.

Press `q` to close the buffer.

## Un-filed ##

** f
   - t - find project file in Treemacs
** g - version control
   - m - magit dispatch
   - r - smerge transient state
*** f - file
    - l - log for commits for this file
*** j
    - d/D - dired same/different window
    - f - jump to lisp function
    - I - imenu all buffers (Just try it!)
*** o - org
** n - narrrow/numbering
   - + - increase number
   - - - decrease number
** p - Project
   - b - switch to project buffer
   - o - project todo list
** r - rings / registers
   - e - show registers
   - P - set window purpose
   - s - last search buffer
** s
   - s - swoop
   - C-s - swoop all buffers
   - r,b - search buffers
* g
  - p - select the last pasted region.
  - t/T - go to the next/previous tab.
  - M - go to middle of line
  - & - repeat global substitute
  - ; - go to last change
  - i - insert resume
** x - text
   - t,w - transpose words
* Org mode
** g
   - h - go up element
   - k - go backward element
   - j - go forward one element same level
** ,
*** * - toggle heading
