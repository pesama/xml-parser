xml-parser
==========

XML Parser converts any XML formatted file into a set of Java Objects, with all attributes and relationships configured.

## How does it work? ##
The parser works in a pretty easy way. It all starts at an entry point called *Lexical Analyzer*, and then declare the *Syntactical Analyzer*.


### Lexical Analyzer ###
The lexical analyzer analyzes the file looking for lexical tokens (e.g. '<', '/>'...) and therefore converts the file into a sorted set of tokens.
It helps finding lexical discrepancies that may crash the parser, and (if any) throws the appropriate Lexical exceptions.

### Syntactical Analyzer ###
This analyzer takes as entry point the set of lexical tokens and looks through them to build syntactical tokens. A syntactical token covers a XML strucure (i.e. from opening to closure) and finds and parse all attributes and object hierarchy.

### Result ###
Once these processes finish the result will be a Syntactical Token (i.e. the XML parent Object) containing all syntactical children in a sorted hierarchic way. 
With these results the main object can be used for any purpose.

## Usage ## 
This repository contains a full Eclipse Project called EDI. Inside the 'main' package you'll find three files:
* *Main.java*: This file contains a GUI, useful for XML Graphical analysis. 
* *MainFrame.java*: Main container of the GUI, with connections with all graphical utilities.
* *Main2.java*: Console-based UI for parsing XML files.

To start an analysis, you need to declare the following:

```
  LexicalAnalyzer lexical = new LexicalAnalyzer(new URL( // Initialise the Lexical Analyzer
  				"URL_TO_THE_XML_FILE"));
	Object[] tokens = lexical.getTokens(); // Create an Array with all Lexical Tokens
	
	SyntacticalAnalyzer syntactical = new SyntacticalAnalyzer(tokens); // Initialise the Syntactical Analyzer
	System.out.println(syntactical.isXML()); // Find out if the file contains a correct marked XML (this sentence makes all analysis and parsing)
	System.out.println("Finished");
```

## License ## 
This project is released under MIT license, and thus you have no restrictions of usage.
