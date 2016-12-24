<!------------------------------------------------------------------------------->
# <a name="basica"></a>basica
basica is an editor + interpreter + compiler of the Basic language for Android devices.

**Dogmata**
* the syntax should be as close to other Basic dialects as possible, especially Visual Basic which has a large coders base
* the command names should indicate as much as possible the order of the parameters:
  * e.g. `GR.TEXT.DRAW grObjId, text$, drawX, drawY ' GR->grObjId ; TEXT->text$ ; DRAW->draw coordinates`
  * e.g. `IS_IN(sub, main) ' "IS sub IN main ?"` (IS_IN is a refactor of INSTR, which also remains available)
  * e.g. `ARRAY.LEN arr[], len` or `LIST.LEN listId, len`
* the power (and the responsibility) of basica should be given to the user at all time (when pressing Run or Compile):
  * for a sensitive command to work, permissions should be declared with the `PERMISSION` statement
  * resources should be called while respecting their exact filename case
* the editor should be as intuitive and powerful as a source code editor can be:
 * multi tab
 * syntax highlighting
 * built-in manual / keyword reference with quick access to contextual help
 * bottom panel for tips and Run/Compile log
* basica should be *maintained*: there should be not more than 3 months between each official release
* basica should be free and open source

<!------------------------------------------------------------------------------->
# <a name="summary"></a>Command summary
The following is a list of the commands built into basica and separated into 16 groups of related commands, which can assist with identifying the best command for the task at hand.  Some commands may appear in more than one group.

* [Array Operations](#array)
* [Communication Control](#communication)
* [Compiler Operations](#compiler)
* [Console Commands](#console)
* [Debugging and Error Control](#debugging)
* [File Commands](#file)
* [Flow Control](#flow)
* [Graphic Commands](#graphic)
* [Html Commands](#html)
* [Input Commands](#input)
* [Memory Management](#memory)
* [Numeric Operations](#numeric)
* [Operating System](#operating)
* [String Operations](#string)
* [Time Commands](#time)
* [Misc Operations](#misc)

**See also**
* [Format and typefaces](#format)
* [Keyword Reference](#keyword)

<!------------------------------------------------------------------------------->
# <a name="format"></a>Format and typefaces
Every basica command is listed alphabetically, as a separate topic. Each entry contains a brief explanation of what the command does, a description of its syntax, clarifying remarks and restrictions, plus examples of use. The examples are designed to be indicative of syntax and usage only.

The syntax section of each entry describes the available options and format each command may use, as follows:
 
* *Italic*:
Indicates areas within commands that you need to fill in with application-specific information, such as variable names, numeric or string values, etc. For example: y = VAL(*string$*)

* UPPERCASE:
Indicates part of the command that must be entered exactly as shown. For example: `FOR BINARY WRITE`

* Braces { }
Indicates the information they enclose is optional. For example: `array[ {start} {,length} ]`

* Vertical bar |
Indicates a choice of two or more options, one of which MUST be used. For example: `OPEN file$ FOR BINARY|TEXT`

* Ellipses ...
Indicates that part of the command can be repeated as many times as required. For example: `DIM array[ n1 {,n2} ... ]`

**See also**
* [Command summary](#summary)
* [Keyword Reference](#keyword)

<!------------------------------------------------------------------------------->
# <a name="keyword"></a>Keyword Reference
This section contains an alphabetical listing of all of the basica keywords. Each entry goes into specific detail about each command, and is cross-referenced to other relevant commands.

The basica commands can either be functions, or statements, according to their syntactic class:

## Functions
Functions are keywords followed by parentheses '()' between which may be listed zero or more parameters.
These are predefined basica functions, as opposed to user-defined functions.
Function names ending with a dollar '$' return a string value, else they return a numeric value. These values can be used within a more complex expression.
Some functions require the program to pass one or more arguments to them, these arguments being numeric or string, or combinations thereof, depending on the function.
For example:
```vb
v$ = VERSION$()
t = COS(3.1)
sResult$ = STR$(t)
a$ = CHR$(123, 65, 66, 67)
```

## Statements
Statements are building blocks that make up programs.
They instruct basica to perform specific actions, such as opening a file, setting the date, sending data to an http server, etc.
Statements do not return a value, but often take one or more arguments.
Each statement must appear on a line by itself, or be separated from other program elements with a delimiting colon (:) character.
For example:
```vb
A = A + 10 : B$ = "basica"
OPEN "A Long Filename.txt" FOR BINARY READ AS fileNum
Count = 100
```

TODO: list all keywords alphabetically

**See also**
* [Command summary](#summary)
* [Format and typefaces](#format)

<!------------------------------------------------------------------------------->
# <a name="permission"></a>PERMISSION statement
**Purpose**
Give certain permissions to the program.

**Syntax**
> PERMISSION perm$

**Remarks**
*perm$* is a string describing the permission, as returned by the [PERMISSION$](#permission_) function.

Android apps need to request permissions to do sensitive operations, like send and receive SMS, make phone call, access GPS, etc.
In basica the user must request each permission his program needs to exercise.
This is done thanks to the `PERMISSION` command. You can use as many `PERMISSION` commands as needed. Usually they are placed at the top of your program.

**Examples**
```vb
' No permission at all needed:
FOR i=1 TO 10
  PRINT i
NEXT
```

```vb
' Write to SD permission needed:
PERMISSION "write external storage"
OPEN "readme.txt" FOR TEXT WRITE AS fileNum
WRITE fileNum, "Hello, world!"
CLOSE fileNum
```

**See also**
[PERMISSION$](#permission_)

<!------------------------------------------------------------------------------->
# <a name="permission_"></a>PERMISSION$ function
**Purpose**
Return a permission string as to be used with the [PERMISSION](#permission) statement.

**Syntax**
> perm$ = PERMISSION$(*n*)

**Remarks**
*n* starts at 1. If *n* is greater than the number of permissions basica has to offer, `PERMISSION$(n)` will return an empty string.

Here is the table of each permission and their meaning:

index | value | permission meaning
------|-------|-------------------
PERMISSION$(1) | "write external storage" | write to the Android device SD-Card

**See also**
[PERMISSION](#permission)

<!------------------------------------------------------------------------------->
# <a name="credits"></a>Credits
The author would like to thank Paul Laughton who created RFO BASIC! that paved the way to basica.
The author would also like to thank jecelyin who created the 920 Editor V2 used in basica.
Finally, thanks to jMarc and the many contributors at the RFO BASIC! forum.
