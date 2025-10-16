
[Vim Cheat Sheet 1](https://vim.rtorr.com/)
[VIm Cheat Sheet 2](https://devhints.io/vim)
[The Primeagen Playlist](https://www.youtube.com/playlist?list=PLm323Lc7iSW_wuxqmKx_xxNtJC_hJbQ7R)


When entering vim, you are in normal mode. You can change modes by pressing
1. 'i' to insert before the cursor
2. 'a' to insert after the cursor
3. 'shift + i' insert mode and moves to beginning of current line
4. 'shift + a' insert mode and moves to end of current line
5. 'shift + s' insert mode and removes current line
6. 'v' for visual mode
7. 'shift + v' for visual line mode
8. ':' to write a command in command mode
and then press 'esc' to come back to normal mode.


To write any command you need to come back to normal mode and type 
':{command}'
commands can be :-
1. :q -> quit vim
2. :w -> write the changes to file(basically saving changes)
3. :wq -> save changes and quit vim (same as :x)
4. :q! -> quit without saving
5. :! *terminal_commands* -> to run terminal commands in vim
6. :VimBeGood -> start game to learn vim (made by ThePrimeagen)
7. :enew -> new empty buffer(tabs basically)
8. :e {filename} -> opens file in new buffer
9. :bp -> buffer previous (switches to buffer on left)
10. :bn -> buffer next
11. :bd -> delete buffer (close)
12. :vsplit {filename} -> open 2 files in same buffer (vertically, use ctrl + ww to move to next file)
13. :{line_number} - go to that line
14. /{char/word} - searches for that char (press n to got to next result of this and shift+n to go to previous result)
15. ?{char/word} - searches but n and N operations reversed


### Motions(move cursor)
- j - move down in normal and visual mode
- k - move up in normal and visual mode
- h - move left in normal and visual mode
- l - move right in normal and visual mode
- w - hops over words towards right in normal and visual mode(forward)
- b - hops over words towards left in normal and visual mode(backward)
- e - jump forward to end of current word
- 0 - jump to 0th column of the line
- _ - jump to first letter of the first word in the line(the first character except whitespace)
- $ - opposite of _ 
- { - moves cursor to just above a paragarph
- } - just below a paragraph
- ctrl + d - jump half page down
- ctrl + u - jump half page up
- shift + g - go all the way down to bottom of page
- gg - all the way to the top

### Commands
- d
- c
- y
- v(for select)

### {Command} -> {Count} -> {Motion}
- d{motion} - delete operation based on the motion in normal mode
- d - delete selected text in visual mode
- shift + d - delete till end of line
- x - delete one letter in normal mode
- y - copy(yank)
- p - paste in normal and visual mode after cursor
- shift + p - paste before cursor
- u - undo in normal mode
- ctrl + r - redo in normal mode
- ctrl + 0 - puts you in normal mode for one command and then immediately bring you back to insert mode
- c - change
- shift + 4 - jump to end of the line
- 8k - move 8 lines up in normal and visual mode (8 is referred to as count)
- 16j - move 16 lines down in normal and visual mode
- dd - delete a single line in normal mode
- dw - delete a word in normal mode
- db - delete a word backwards in normal mode
- d3j - delete current line and 3 lines below it in normal mode
- d2w - delete 2 words in normal mode
- y5j - yank 5 lines starting with current line in normal mode
- diw - delete inner word. deletes word under cursor without deleting surrounding whitespaces
- daw - delete a word. deletes the entire word under the cursor, plus the trailing whitespace
- d$ - delete from cursor to end of line
- caw - deletes word under the cursor and puts you in insert mode
- gg - takes you to top of file
- shift + g - takes you to end
- > - to indent selected lines in visual mode(basically shift text)
- < - shift text right
- yiw - yank inner word under cursor
- yy - yank a line
- o - add new line below cursor and go into insert mode
- shift + o - add new line above cursor and go into insert mode
- f{char} - move cursor to the first position of {char} in the line in forward direction(ex:- 'f(' moves to the first opening bracket in the line.)
- t{char} - moves to just before the character but not on
- , - repeat f{char} or t{char} in backward direction
- ; - repeat f{char} or t{char} in forward direction
- shift + f{char}(F{char}) - f{char} operation backwards
- T{char} - t{char} backwards
- df{char} - delete everything from current position upto char and including char
- dt{char} - delete everything from current position upto char but not including char
- d{F/T}{char} - delete
- y{f/t/F/T}{char} - yank
- v{f/t/F/T}{char} - select
- zz - centres your view(cursor is in middle of page)
- * - if on a word and press this, it puts the word in the search term(/{word})
- {#} - if on a word and press this, it puts the word in the search term(?{word})(ignore '{}')



You select text in visual or visual line mode. Go to visual mode and use {count}motions to move and select text in file and press 'y' to yank it or 'd' to delete it. Pressing 'y' or 'd' puts you in normal mode. Here you can now press p to paste what you yanked or deleted.
Entering visual line selects the current line.
You can even paste in visual mode what you yanked or deleted.
You can paste over a highlighted region.

A paragraph is basically contiguous non whitespace text. Paragraphs are separated by empty lines.