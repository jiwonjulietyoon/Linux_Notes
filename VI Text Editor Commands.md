# VI Text Editor Commands



## Basic Commands

- `vi` : launch VI Text Editor
- `vi fileName` : open _fileName_ via VI (if _fileName_ does not already exist, create a new empty file under that name)
- `:se(t) nu(mber)` : enable line numbers
- `:se(t) nonu(mber)` : disable line numbers
- `:!Cmd` : temporarily pause VI and execute command _Cmd_
- Ctrl + W + N : split window horizontally (division runs across the page)
- Ctrl + WW : switch over to next file (after splitting window)
- Ctrl + WO : close all files except for the one where the cursor is currently positioned
- `:f` : display file info (title, directory, etc.)



## Navigate (Command) Mode (No Editing)

Move cursor to the following positions:

- `h` : left ←
- `l` : right →
- `j` : down ↓
- `k` : up ↑
- `w` : beginning of next word (= for__w__ard) - lowercase w
  - reads special characters AND whitespace | 특수문자 O, 공백인식 O
  - cluster of special characters also considered a word on their own
  - cursor will stop at:
    - 1st character of a cluster of alphabets and/or numbers
    - 1st character of a cluster of special characters
    - character following any whitespace
  - `nw` : forward _n_ words (n is an integer)
- `W` : beginning of next word - uppercase W
  - does NOT read special characters; reads whitespace  | 특수문자 X, 공백인식 O
  - special characters are NOT considered independent "words"
  - cursor will only stop at each character following any whitespace
    - (alphabets/numbers/special characters NOT differentiated)
- `b` : beginning of previous word (= __b__ackward)
  - reads special characters AND whitespace | 특수문자 O, 공백인식 O
  - `nb` : back _n_ words
- `B` : beginning of previous word
  - does NOT read special characters; reads whitespace | 특수문자 X, 공백인식 O
- `e` : end of next word
  - reads special characters AND whitespace | 특수문자 O, 공백인식 O
  - e.g) `ye` : copies "Yes" from "Yes,"
- `E` : end of next word
  - does NOT read special characters; reads whitespace  | 특수문자 X, 공백인식 O
  - e.g) `yE` : copies "Yes," from "Yes,"
- `}` : forward one paragraph
  - Separator: full line break
  - cursor will move to next empty line
- `}` : back one paragraph
- `0` or `^` : beginning of current line (= home key)
- `$` : end of current line (= end key)
- `gg` or `[[` : first line (beginning of document)
- `G` or `]]` : last line (end of document)
- `H` : top of window (__H__ead)
- `M` : middle of window (__M__iddle)
- `L` : bottom of window (tai__L__)
- `:n` or `nG` : line _n_
- `[ESC]` : Enter Navigate (Command) Mode from Insert (Edit) Mode or Command Line Mode



## Entering Insert (Edit) Mode

Enter Insert Mode AFTER doing the following (from current cursor position):

- `i` : (insert from the left border of the blinking cursor)
- `a` : move one space right (= append text after cursor)
  - Usually, `a` is more intuitive than `i`
- `I`  : move to beginning of line
- `A` : move to end of line
- `o` : insert new line below (lowercase o)
- `O` : insert new line above (uppercase O)
- `s` : delete current character (lowercase s)
- `S` : delete current line (uppercase S)



## Editing Text (does NOT enter Insert Mode)

(Edit text in/from current cursor position by default, unless otherwise specified)

- `r` : edit single character, without entering insert mode
- `R` : replace (insert)
  - press 'backspace' to cancel replacement
  - press 'ESC' to apply changes
- `x` : delete single character per key press first towards the right, and then towards the left
  - `nx` : delete _n_ characters
- `X` : backspace (towards the left)
- `dd` : delete current line
- `d$` or `D` : delete remainder of the line (towards the right)
- `dE` : delete until the end of the word, right before the next space (towards the right)
- `dL` : delete from the current line to the last line
- `ndd` : delete _n_ lines
- `yy` : copy line
- `nyy` : copy _n_ lines
- `ye` : copy until the end of the word (special characters also considered independent words)
  - c.f. `yE` : copy until the end of the word (including special characters)
- `p` : paste copied line/text below (or to the right of the cursor)
  - *) "cut and paster" == "delete and paste" (VI will automatically copy whatever was just deleted)
- `P` : paste copied line/text above (or to the left of the cursor)
- `:nr ./a` : insert contents of _./a_ below line _n_
- `:.!cmd` : insert output of command _cmd_, overwriting the current line
- `:nr! cmd` : insert output of command _cmd_ below line _n_
- `u` : undo
- `U` : undo all changes made on current line
- Ctrl + `r` : redo



## Save, Exit, Open another file

- `:q` : exit file

- `:q!` : force exit file
- `:w` : save
- `:w ./test` : save as `./test`
- `:wq` or `ZZ` : save and then quit (exit)
- `:w >> ./a` : append current document content to `./a` and then save
- `:e ./fileName.txt` : open `./fileName.txt`
- `:enew` : open new file



## Find and Replace

- `/` : find (downwards by default)
  - `n` : next
  - `N` : previous
- `?` : find (upwards by default)
  - `n` : previous
  - `N` : next
- `:[range]s/[old]/[new]` : replace
  - e.g) `:5s/passwd/itbank` : replace 'passwd' in line 5 with 'itbank'
    - will only replace first encountered word
  - e.g) `:20,23s/PASS/Tiger` : replace 'PASS' in lines 20-23 with 'Tiger'
  - `:%s/old/new` : replace within entire document
  - `62s/old/new/g` : in line 62, replace all occurrences of 'old' with 'new'



## Boomark

Bookmarks are not permanent (deleted upon exiting VI editor)

- `m` + `a ~ z` or `m` + `A ~ Z` : place bookmark (total 52 bookmarks available)
- `(backquote) + a~z or A~Z : move to bookmark
- \` \` (2 backquotes) : move to previous location





