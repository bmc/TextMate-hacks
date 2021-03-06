# Some TextMate Hacks

This repo contains various quick-and-dirty TextMate hacks, mostly for rebinding
keys. There are several subdirectories here:

* `bundle-hacks` contains hacks to various TextMate bundles (keybindings,
   mostly).
* `themes` contains themes I use.

## Bundle Hacks (`bundle-hacks`)

Within the `bundle-hacks` directory, each subdirectory corresponds to an
existing (stock) TextMate bundle. For example, `bundle-hacks/Source` corresponds
to the TextMate `Source.tmbundle` bundle. Underneath the subdirectory, you'll
find a `Macros` directory, containing one or more XML files, each representing
Mac `plist` source for a TextMate macro. These macros are intended to augment an
existing TextMate bundle.

Installation is straightforward enough. First, ensure that you have a local
directory for the bundle:

	$ mkdir -p ~/Library/Application\ Support/TextMate
	$ cd ~/Library/Application\ Support/TextMate
	$ mkdir -p Bundles/BUNDLE.tmbundle/Macros
	
Replace BUNDLE with the bundle name (e.g., `Source`).

Then, install the macros, one by one, using `plutil`. For instance:

	$ plutil -convert binary1 Bundles/Source.tmbundle/Macros/MoveBackwardWord.plist /path/to/this/repo/bundle-hacks/Source/Macros/MoveBackwardWord.xml

Do this for every macro you want to install. Then, either restart TextMate or
tell it to reload its bundles. To force TextMate to reload its bundles, you can
use the *Bundles > Bundle Editor > Reload Bundles*, or you can simply run this
command:

	$ osascript -e 'tell app "TextMate" to bundles'

### Specific Macros

`Source/Macros/MoveWordLeft.xml`

Assigns the *Command-B* shortcut, in source and text files, to move one word
left, Emacs-style.

**NOTE**: Some bundles, like the Markdown bundle, override this binding. In
addition, both the `Xcode` and `Make` bundles map that key binding to the
*Build* action. If you want this keybinding to take effect, you have to unmap
*Build* in those bundles.

`Source/Macros/MoveWordRight.xml`

Assigns *Command-F* to move one word right, Emacs-style. This replaces the
default binding of Search, so youll have to rebind that key.

`Source/Macros/CtrlHBackspace.xml`

Assigns *Control-H* to `deleteBackward` (i.e., the same thing the Apple
keyboard's *Delete* key does).

**NOTE**: Numerous TextMate bundles already use *Control-H* for
help or documentation. To get this rebinding to work, you have to go through
each bundle, in the Bundle Editor, and rebind those mappings. (I rebind them to
*Command-H*.)

`Source/Macros/CmdDDeleteWordForward.xml`

Assigns *Command-D* to `deleteWordForward`, Emacs-style.

## Themes

The themes are easy enough to use: Simple download the raw `tmTheme` file
and double-click it.

### Using a theme with Sublime Text 2

[Sublime Text 2][] can also use TextMate themes. To install a theme in
Sublime Text 2, download the `thTheme` file and install it in your
`Packages/User` directory. Then, select it, under
*Preferences > Color Scheme > User*. The `Packages/User` directory is
located here:

* Linux: `~/.config/sublime-text-2/Packages/User/`
* Mac: `/Users/bmc/Library/Application Support/Sublime Text 2/Packages/User`
* Windows: `C:\Users\username\AppData\Roaming\Sublime Text 2\Packages\User` 
  (**NOTE**: That's the path on *my* Windows 7 machine, with `username` 
  replaced by my user name, and using the non-portable version of 
  Sublime Text 2. YMMV.)

[Sublime Text 2]: http://www.sublimetext.com/2
