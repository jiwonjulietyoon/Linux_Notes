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



## Navigate (Command) Mode

Move cursor to the following positions:

- `h` : left ←
- `l` : right →
- `j` : down ↓
- `k` : up ↑
- `w` : beginning of next word (= for__W__ard) - lowercase w
  - reads special characters AND whitespace
  - cluster of special characters also considered a word on their own
  - cursor will stop at:
    - 1st character of a cluster of alphabets and/or numbers
    - 1st character of a cluster of special characters
    - character following any whitespace
- `nw` : forward _n_ words (n is an integer)
- `W` : beginning of next word - uppercase W
  - does NOT read special characters; reads whitespace
  - special characters are NOT considered independent "words"
  - cursor will only stop at each character following any whitespace
    - (alphabets/numbers/special characters NOT differentiated)
- 