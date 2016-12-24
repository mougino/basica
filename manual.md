<!------------------------------------------------------------------------------->
# <a name="basica"></a>basica
basica is an editor + interpreter + compiler of the Basic language for Android devices.

**Dogmata**
* the syntax should be as close as Visual Basic commands as possible
* the command name gives as much as possible the order of the parameters
  * e.g. `IS_IN(sub, main) ' is read "IS sub IN main ?" ' nota: IS_IN is a refactor of INSTR, also available for retro-compatibility`
  * e.g. `GR.TEXT.DRAW grObjId, text$, drawX, drawY ' GR->grObjId ; TEXT->text$ ; DRAW->draw coordinates`
* the power (and the responsibility) is given to the user
  * permissions, resources (filename case), everything needs to be declared and respected, both when pressing Run or Compile
* free and open source (GPL V3)

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
* [Keyword Reference](#keyword)
* [Format and typefaces](#format)

<!------------------------------------------------------------------------------->
# <a name="keyword"></a>Keyword Reference

<!------------------------------------------------------------------------------->
# <a name="format"></a>Format and typefaces



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
OPEN "readme.txt" FOR TEXT WRITE AS fid
WRITE fid, "Hello, world!"
CLOSE fid
```

**See also**
[PERMISSION$](#permission_)

<!------------------------------------------------------------------------------->
# <a name="permission_"></a>PERMISSION$ function
**Purpose**
Return a permission string as to be used with the [PERMISSION](#permission) statement.

**Syntax**
> perm$ = PERMISSION$(n)

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
