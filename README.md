
# Homematic Lexer Plugin

This is a lexer for Homematic scripts.
It uses the same lexing formats as the [SDV 5.0 Script-Developer-CCU](https://github.com/HMMike/Script-Developer-CCU).

It is possible to use a UDL, but the strange comment sign `!` and the positions where it is allowed as a negator make it hard to lex all code correctly.
When I first started writing CCU scripts, I used `.c` extensions and a kind of “double comments”: an exclamation mark combined with C comments, like `!//`. However, I noticed that keyword parsing was strange.
So I decided to write a complete custom lexer. The color definitions are similar to SDV 5.0.

## Used code

Based on the [Notepad++ plugin template](https://github.com/npp-plugins/plugintemplate)
Thanks to the project [Notepad++ plugin with crude external lexer](https://github.com/moon6969/NPP-lexer-example), which showed me the first steps of writing a lexer.

Neither [Scintilla](https://www.scintilla.org/ScintillaDoc.html) nor [NPP](https://npp-user-manual.org/docs/plugin-communication/) provide much documentation on how to create a lexer — let alone an external one!

Some code must be copied from the Notepad++ project:

* [Scintilla files](scintilla/include/)
* [Lexilla/lexlib files](lexilla/lexlib/LexerBase.h)

For the actual lexing part, I suggest looking at the built-in [NPP lexer sources, such as the C++ lexer](lexilla/lexers/LexCPP.cxx).

### Notes

I used Visual Studio 2022 to write the plugin.
The `HomematicNPPLexerPlugin.vcxproj` file sets `<PlatformToolset>` = v145 for Visual Studio 2022.

### Installation

Copy the plugin DLL to
`plugins\HomematicNPPLexerPlugin\HomematicNPPLexerPlugin.dll`
and the XML file to
`plugins\Config\HomematicNPPLexerPlugin.xml`

“HomematicNPPLexerPlugin” should appear:

* In the *Language* menu
* At the bottom of *Settings → Style Configuration*

