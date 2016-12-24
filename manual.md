# Command summary
The following is a list of the commands built into basica and separated into 17 groups of related commands, which can assist with identifying the best command for the task at hand.  Some commands may appear in more than one group.

* [Array Operations](#permission)
* [Collection Objects]()
* [Communication Control]()
* [Compiler Operations]()
* [Debugging and Error Control]()
* [File Commands]()
* [Flow Control]()
* [Graphic Commands]()
* [Input Commands]()
* [Memory Management]()
* [Metastatements]()
* [Numeric Operations]()
* [Operating System]()
* [Printing Commands]()
* [String Operations]()
* [Thread Control]()
* [Time Commands]()
* [Misc Operations]()

# <a name="permission"></a>Permission
Syntax:
```vb
perm$ = PERMISSION$(n) ' n starting at 1
PERMISSION perm$
```
Android apps need to request permissions to do sensitive operations, like send and receive SMS, make phone call, access GPS, etc.
In basica the user must request each permission his program needs to exercise.
This is done thanks to the `PERMISSION` command. You can use as many `PERMISSION` commands as needed. Usually they are placed at the top of your program.

Here is a table of each permission and their meaning:

index | value | permission meaning
------|-------|-------------------
PERMISSION$(1) | "write external storage" | write to the phone/tablet SD-Card

Here are a few examples:
```vb
' No permission at all needed:
FOR i=1 TO 10
  PRINT i
NEXT
```

```vb
' Write to SD permission needed:
TEXT.OPEN w, fid, "readme.txt"
TEXT.WRITELN fid, "Hello, world!"
TEXT.CLOSE fid
```

# <a name="credits"></a>Credits
The author would like to thank Paul Laughton who created RFO BASIC! on which basica was based on.
The author would like to thank jecelyin who created the 920 Editor V2 used in basica.
Finally, thanks to jMarc and the many contributors at the RFO BASIC! forum.
