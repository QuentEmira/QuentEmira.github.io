Internationalization, or I18n, is the a way of designing and programming a game so that it can be localized in other languages.
Internationalization can be broken down into two part:
- I18n architecture, where the file structure, assets, memory usage and naming conventions are designed for easy localization. For file structure, it would be separation files of different localizations into different folders to avoid confusion and make it easier for the people localizing to understand the game. Naming conventions refers to easily understandable and convertible names.
- I18n programming, where ui, text, regional settings are handled. This is where the translation of the string text is done.

Now, the translator aren't just going to go through the game files and translate where ever necessary. It needs to be a simpler process.

A way to handle it is to have a separate structure (a table or a text files) where strings are linked with their string id. Then create a function which takes a string id, and returns the string.
The translation for the different string can be done separately in the string table or text file, thus making it easier to localise.

[[Strings]]