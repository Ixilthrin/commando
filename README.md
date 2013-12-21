commando
========

This is a Java application using swing.  It compiles with Java 7, but should still compile on older versions.

The GUI is set up with text fields for the current command, current working directory, and standard input stream.

The right side of the GUI is the text output from the commands.  You can cycle through the different output windows
at any time.

There is also a text area that represents the standard error output.


You can run commands from the local shell, or use built-in commands written in Java, or write your own.

Commands can also be piped together following the standard *nix model.  Internally these are built from

small Java programs, called Filters, that are connected using Java pipes.

To create your own filter, simply subclass the Filter class.

To compile this program:
In the filters directory type:
javac *.java

To run this program:
java -cp filters.CommandGui

A typical filter will be compiled to a class file, such as LineNumbers.class.  When you run this in commando
the usage will be something like the following:

ls | LineNumbers

Commando will add the extension, run the system ls command, pipe the output to LineNumbers.class, 
and send the output to the current output window in the GUI.

In order to allow for easier editing of a chain of filters, there is an interface for creating a list 
of filters, which are piped together when "Execute Chain" is pressed.

There is also a text field that reads from the clipboard and writes to the clipboard.  This allows you
to use text directly from the clipboard.

There are filters related to the clipboard, called ClipboardInput and ClipboardOutput.
These can be used in a filter chain also.
