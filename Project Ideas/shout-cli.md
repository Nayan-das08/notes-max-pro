%% project description %%
a notepad like terminal-based app where one can type the text and have it displayed with an ascii art design in real time as they type.

---
## requirements
### what needs to be studied
- [x] `ncurses` for terminal text-based terminal UI
- [x] `std::map` for mapping the design to the corresponding character
- [x] makefiles [[cpp.canvas|cpp]]
### resources required

---
## notes
- [x] install `ncurses` on WSL
- [x] create a charmap
- [x] tinker with `ncurses`
- [x] print single ASCII characters
- [x] loop for input from user and print below the previous character
- [x] use `move()` and `getyx()` to reposition the cursor
- [x] print multiple ASCII characters next to each other
- [x] print space
- [x] improve charmap
	- using `struct`
- [x] moving text to next line at the end of the current line
	- [x] `new line` or `line feed` 
- [x] backspace
	- need to use a stack for storing the characters
	- [x] normal for single line deletion
	- [x] complex for single line deletion of multiple letters
	- [x] complex for new line
		- use stack for last column value when pressing LF
- [x] numbers
- [ ] special characters
- [x] window setup
