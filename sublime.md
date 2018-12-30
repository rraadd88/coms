## installing
	sudo mv Sublime\ Text\ 2 /opt/sublime2
	sudo ln -s /opt/sublime2/sublime_text /usr/bin/sublime


## integrating in ubuntu 
## First, make sure that /usr/share/applications/sublime_text.desktop exists (sublime-text.desktop on some systems):

	ls /usr/share/applications/sublime_text.desktop

## Then, open /usr/share/applications/defaults.list with Sublime:

	sudo subl /usr/share/applications/defaults.list

## Search for all instances of gedit and replace them with sublime_text. Save the file, log out and back in, and you should be all set.

## If for some reason /usr/share/applications/sublime_text.desktop (or sublime-text.desktop) doesn't exist, create it:

	sudo touch /usr/share/applications/sublime_text.desktop

## Open it in Sublime:

	sudo subl /usr/share/applications/sublime_text.desktop

## and paste the following into it:

	[Desktop Entry]
	Version=1.0
	Type=Application
	Name=Sublime Text
	GenericName=Text Editor
	Comment=Sophisticated text editor for code, markup and prose
	Exec=/opt/sublime_text/sublime_text %F
	Terminal=false
	MimeType=text/plain;
	Icon=sublime-text
	Categories=TextEditor;Development;
	StartupNotify=true
	Actions=Window;Document;

	[Desktop Action Window]
	Name=New Window
	Exec=/opt/sublime_text/sublime_text -n
	OnlyShowIn=Unity;

	[Desktop Action Document]
	Name=New File
	Exec=/opt/sublime_text/sublime_text --command new_file
	OnlyShowIn=Unity;
	However, if you installed Sublime Text using the .deb file downloaded from sublimetext.com, the file should already exist.

## user setting

	{
	"color_scheme": "Packages/Color Scheme - Default/Cobalt.tmTheme",
	"font_size": 13,"font_options":["bold"],"font_face": "Courier New"
	}

	{
	"color_scheme": "Packages/Color Scheme - Default/Cobalt.tmTheme",
	"fade_fold_buttons": false,
	"font_face": "Monaco",
	"font_options":
	[
		"bold"
	],
	"font_size": 9.5,
	"highlight_line": true,
	"highlight_modified_tabs": true,
	"ignored_packages":
	[
		"Vintage"
	],
	"tab_completion": false
	}
