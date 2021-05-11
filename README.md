sent is a simple plaintext presentation tool.

sent does not need latex, libreoffice or any other fancy file format, it uses
plaintext files to describe the slides and can include images via farbfeld.
Every paragraph represents a slide in the presentation.

The presentation is displayed in a simple X11 window. The content of each slide
is automatically scaled to fit the window and centered so you also don't have to
worry about alignment. Instead you can really concentrate on the content.


Dependencies

You need Xlib and Xft to build sent and the farbfeld[0] tools installed to use
images in your presentations.

Demo

To get a little demo, just type

	make && ./sent example

You can navigate with the arrow keys and quit with `q`.


Usage

	sent [FILE]

If FILE is omitted or equals `-`, stdin will be read. Produce image slides by
prepending a `@` in front of the filename as a single paragraph. Lines starting
with `#` will be ignored. A `\` at the beginning of the line escapes `@` and
`#`. A presentation file could look like this:

	sent
	
	@nyan.png
	
	depends on
	- Xlib
	- Xft
	- farbfeld
	
	sent FILENAME
	one slide per paragraph
	# This is a comment and will not be part of the presentation
	\# This and the next line start with backslashes
	
	\@FILE.png
	
	thanks / questions?

Colors
Line color support has been added with the special combination "c#".
Each text line supports only one color: the default or the special one (you cannot have text with two different colors in the same line).
The special color must be entered at the beggining of the line.
Example slide:
```
sent
c#00ff00 with 
c#0000FFcolors
```
Will print "sent" in the default foreground color (defined in `config.h`), "with" in green and "colors" in blue.
Note that the word "colors" has no space between the hex color and itself. This is because a single space after the color is optional and ommited when printing. Using multiple spaces (like `c#0000FF    colors`) will ignore the first one after the last F and print the rest.

Development

sent is developed at http://tools.suckless.org/sent


0: http://tools.suckless.org/farbfeld/
