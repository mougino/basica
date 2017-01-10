<!------------------------------------------------------------------------------->
# basica
basica is an editor + GUI composer + interpreter + compiler of the Basic language for Android devices.
It is based on RFO BASIC! with many improvements.

**KeyWord Quick Finder:**
[&#9398;](#a) [&#9399;](#b) [&#9400;](#c) [&#9401;](#d) [&#9402;](#e) [&#9403;](#f) [&#9404;](#g) [&#9405;](#h) [&#9406;](#i) [&#9407;](#j) [&#9408;](#k) [&#9409;](#l) [&#9410;](#m) [&#9411;](#n) [&#9412;](#o) [&#9413;](#p) [&#9415;](#r) [&#9416;](#s) [&#9417;](#t) [&#9418;](#u) [&#9419;](#v) [&#9420;](#w) [&#9423;](#z)

## Dogmata

1. the syntax should be as close to other Basic dialects as possible
  * especially Visual Basic (VB6) PowerBasic and FreeBasic, that have a large coders base
  * e.g. usual comment character `'`, usual line continuation character `_`
  * e.g. usual binary operators `AND`, `OR`, `NOT`
  * e.g. usual typical commands like `OPEN file$ FOR Mode Access AS #fileNum`
2. the command names should indicate as much as possible the order of the parameters:
  * e.g. `GR.TEXT.DRAW grObjId, text$, drawX, drawY ' GR->grObjId ; TEXT->text$ ; DRAW->draw coordinates`
  * e.g. `FILE.SIZE file$, size` or `FILE.EXISTS file$, exists`
  * e.g. `ARRAY.LEN arr[], len` or `LIST.LEN listId, len`
  * e.g. `IS_IN(sub$, main$) ' "IS sub$ IN main$?"` ([IS_IN](#is-in) is a refactor of [INSTR](#instr), which also remains available)
3. indices and failure codes should always be consistent
 * i.e. indices always start at 1 (array dim, list id, obj id, etc.)
 * and failure code is always 0 (e.g. cannot open a file, load a resource, etc.)
4. the power (and the responsibility) of basica should be given to the user at all time (when pressing Run or Compile):
  * sensitive commands need a `PERMISSION` statement in order to work
  * resources must be placed in a specific folder, see [Working with resources](#working-with-resources)
  * resources must be called with their exact filename case ("myPic.JPG" <> "Mypic.jpg")
5. graphical components (GUI) should be easily accessible via a dedicated API:
 * basica natively supports the [GW library](http://mougino.free.fr/gw.html) (an enhanced version in material design)
 * the GUI composer allows to build application screens (aka GW pages) in a WYSIWYG manner
6. the editor should be as intuitive and powerful as a source code editor can be:
 * multi tab
 * syntax highlighting
 * built-in manual / keyword reference with quick access to contextual help
 * bottom panel for tips and Run/Compile log
7. basica should be *maintained*: there should be no more than 3 months between official releases

**See also:**
* [Differences with RFO BASIC!](#differences-with-rfo-basic)

<!------------------------------------------------------------------------------->
# Command summary
The following is a list of the commands built into basica and separated into 18 groups of related commands, which can assist with identifying the best command for the task at hand.  Some commands may appear in more than one group.

* [Array, List, Stack and Bundle](#array-list-stack-and-bundle)
* [Communication Control](#communication-control)
* [Compiler Operations](#compiler-operations)
* [Console Commands](#console-commands)
* [Debugging and Error Control](#debugging-and-error-control)
* [File Commands](#file-commands)
* [Flow Control](#flow-control)
* [Graphic Commands](#graphic-commands)
* [Html Commands](#html-commands)
* [Input Commands](#input-commands)
* [Memory Management](#memory-management)
* [Numeric Operations](#numeric-operations)
* [Operating System](#operating-system)
* [Sound Commands](#sound-commands)
* [SQL Commands](#sql-commands)
* [String Operations](#string-operations)
* [Time Commands](#time-commands)
* [Misc Operations](#misc-operations)

**See also:**
* [Format and typefaces](#format-and-typefaces)
* [Keyword Reference](#keyword-reference)

<!------------------------------------------------------------------------------->
# Format and typefaces
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

**See also:**
* [Command summary](#command-summary)
* [Keyword Reference](#keyword-reference)

<!------------------------------------------------------------------------------->
# Keyword Reference
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

## A
* [ABS](#abs)
* [ACOS](#acos)
* [AND](#and)
* [APP.BROADCAST](#app-broadcast)
* [APP.START](#app-start)
* [APPEND](#open-statement)
* [ARRAY.AVERAGE](#array-average)
* [ARRAY.COPY](#array-copy)
* [ARRAY.DELETE](#array-delete)
* [ARRAY.DIMS](#array-dims)
* [ARRAY.FILL](#array-fill)
* [ARRAY.LEN](#array-len)
* [ARRAY.LOAD](#array-load)
* [ARRAY.MAX](#array-max)
* [ARRAY.MIN](#array-min)
* [ARRAY.REVERSE](#array-reverse)
* [ARRAY.SEARCH](#array-search)
* [ARRAY.SHUFFLE](#array-shuffle)
* [ARRAY.SORT](#array-sort)
* [ARRAY.STD_DEV](#array-std-dev)
* [ARRAY.SUM](#array-sum)
* [ARRAY.VARIANCE](#array-variance)
* [ASCII](#ascii)
* [ASIN](#asin)
* [ATAN](#atan)
* [ATAN2](#atan2)
* [AUDIO.ISDONE](#audio-isdone)
* [AUDIO.LENGTH](#audio-length)
* [AUDIO.LOAD](#audio-load)
* [AUDIO.LOOP](#audio-loop)
* [AUDIO.PAUSE](#audio-pause)
* [AUDIO.PLAY](#audio-play)
* [AUDIO.POSITION.CURRENT](#audio-position-current)
* [AUDIO.POSITION.SEEK](#audio-position-seek)
* [AUDIO.RECORD.START](#audio-record-start)
* [AUDIO.RECORD.STOP](#audio-record-stop)
* [AUDIO.RELEASE](#audio-release)
* [AUDIO.STOP](#audio-stop)
* [AUDIO.VOLUME](#audio-volume)

## B
* [BACK.RESUME](#back-resume)
* [BACKGROUND](#background)
* [BACKGROUND.RESUME](#background-resume)
* [BAND](#band)
* [BIN](#bin-function)
* [BIN$](#bin-function-1)
* [BINARY](#open-statement)
* [BNOT](#bnot)
* [BOR](#bor)
* [BROWSE](#browse)
* [BT.CLOSE](#bt-close)
* [BT.CONNECT](#bt-connect)
* [BT.DEVICE.NAME](#bt-device-name)
* [BT.DISCONNECT](#bt-disconnect)
* [BT.ONREADREADY.RESUME](#bt-onreadready-resume)
* [BT.OPEN](#bt-open)
* [BT.READ.BYTES](#bt-read-bytes)
* [BT.READ.READY](#bt-read-ready)
* [BT.RECONNECT](#bt-reconnect)
* [BT.SET.UUID](#bt-set-uuid)
* [BT.STATUS](#bt-status)
* [BT.WRITE](#bt-write)
* [BUNDLE.CLEAR](#bundle-clear)
* [BUNDLE.CONTAIN](#bundle-contain)
* [BUNDLE.CREATE](#bundle-create)
* [BUNDLE.GET](#bundle-get)
* [BUNDLE.KEYS](#bundle-keys)
* [BUNDLE.PUT](#bundle-put)
* [BUNDLE.REMOVE](#bundle-remove)
* [BUNDLE.TYPE](#bundle-type)
* [BXOR](#bxor)

## C
* [CALL](#call)
* [CBRT](#cbrt)
* [CEIL](#ceil)
* [CHDIR](#chdir)
* [CHR$](#chr)
* [CLIPBOARD.GET](#clipboard-get)
* [CLIPBOARD.PUT](#clipboard-put)
* [CLOCK](#clock)
* [CLOSE](#close)
* [CLS](#cls)
* [CON.FRONT](#con-front)
* [CON.LINE.COUNT](#con-line-count)
* [CON.LINE.TEXT](#con-line-text)
* [CON.LINE.TOUCHED](#con-line-touched)
* [CON.SAVE](#con-save)
* [CON.SELECT](#con-select)
* [CON.TITLE](#con-title)
* [CONSOLETOUCH.RESUME](#consoletouch-resume)
* [COS](#cos)
* [COSH](#cosh)

## D
* [DEBUG.DUMP.ARRAY](#debug-dump-array)
* [DEBUG.DUMP.BUNDLE](#debug-dump-bundle)
* [DEBUG.DUMP.LIST](#debug-dump-list)
* [DEBUG.DUMP.SCALARS](#debug-dump-scalars)
* [DEBUG.DUMP.STACK](#debug-dump-stack)
* [DEBUG.ECHO.OFF](#debug-echo-off)
* [DEBUG.ECHO.ON](#debug-echo-on)
* [DEBUG.OFF](#debug-off)
* [DEBUG.ON](#debug-on)
* [DEBUG.PRINT](#debug-print)
* [DEBUG.SHOW](#debug-show)
* [DEBUG.SHOW.ARRAY](#debug-show-array)
* [DEBUG.SHOW.BUNDLE](#debug-show-bundle)
* [DEBUG.SHOW.LIST](#debug-show-list)
* [DEBUG.SHOW.PROGRAM](#debug-show-program)
* [DEBUG.SHOW.SCALARS](#debug-show-scalars)
* [DEBUG.SHOW.STACK](#debug-show-stack)
* [DEBUG.SHOW.WATCH](#debug-show-watch)
* [DEBUG.WATCH](#debug-watch)
* [DECODE$](#decode)
* [DECRYPT](#decrypt)
* [DEVICE](#device)
* [DEVICE.LANGUAGE](#device-language)
* [DEVICE.LOCALE](#device-locale)
* [DIALOG.MESSAGE](#dialog-message)
* [DIALOG.SELECT](#dialog-select)
* [DIM](#dim)
* [DO](#do)

## E
* [ELSE](#if)
* [EMAIL.SEND](#email-send)
* [ENCODE$](#encode)
* [ENCRYPT](#encrypt)
* [END](#end-disambiguation)
* [ENDS_WITH](#ends-with)
* [EOF](#eof)
* [EXIT](#exit-disambiguation)
* [EXP](#exp)

## F
* [FILE.COPY](#file-copy)
* [FILE.DELETE](#file-delete)
* [FILE.DIR](#file-dir)
* [FILE.EXISTS](#file-exists)
* [FILE.MKDIR](#file-mkdir)
* [FILE.RENAME](#file-rename)
* [FILE.ROOT](#file-root)
* [FILE.SIZE](#file-size)
* [FILE.TYPE](#file-type)
* [FLOOR](#floor)
* [FONT.CLEAR](#font-clear)
* [FONT.DELETE](#font-delete)
* [FONT.LOAD](#font-load)
* [FOR](#for)
* [FORMAT$](#format)
* [FORMAT_USING$](#format-using)
* [FRAC](#frac)
* [FTP.CD](#ftp-cd)
* [FTP.CLOSE](#ftp-close)
* [FTP.DELETE](#ftp-delete)
* [FTP.DIR](#ftp-dir)
* [FTP.GET](#ftp-get)
* [FTP.MKDIR](#ftp-mkdir)
* [FTP.OPEN](#ftp-open)
* [FTP.PUT](#ftp-put)
* [FTP.RENAME](#ftp-rename)
* [FTP.RMDIR](#ftp-rmdir)
* [FUNCTION](#function)

## G
* [GET](#get)
* [GET$](#get-1)
* [GETERROR$](#geterror)
* [GOSUB](#gosub)
* [GOTO](#goto)
* [GPS.ACCURACY](#gps-accuracy)
* [GPS.ALTITUDE](#gps-altitude)
* [GPS.BEARING](#gps-bearing)
* [GPS.CLOSE](#gps-close)
* [GPS.LATITUDE](#gps-latitude)
* [GPS.LOCATION](#gps-location)
* [GPS.LONGITUDE](#gps-longitude)
* [GPS.OPEN](#gps-open)
* [GPS.PROVIDER](#gps-provider)
* [GPS.SATELLITES](#gps-satellites)
* [GPS.SPEED](#gps-speed)
* [GPS.STATUS](#gps-status)
* [GPS.TIME](#gps-time)
* [GR.ARC](#gr-arc)
* [GR.BITMAP.CREATE](#gr-bitmap-create)
* [GR.BITMAP.CROP](#gr-bitmap-crop)
* [GR.BITMAP.DELETE](#gr-bitmap-delete)
* [GR.BITMAP.DRAW](#gr-bitmap-draw)
* [GR.BITMAP.DRAWINTO.END](#gr-bitmap-drawinto-end)
* [GR.BITMAP.DRAWINTO.START](#gr-bitmap-drawinto-start)
* [GR.BITMAP.FILL](#gr-bitmap-fill)
* [GR.BITMAP.LOAD](#gr-bitmap-load)
* [GR.BITMAP.SAVE](#gr-bitmap-save)
* [GR.BITMAP.SCALE](#gr-bitmap-scale)
* [GR.BITMAP.SIZE](#gr-bitmap-size)
* [GR.BOUNDED.TOUCH](#gr-bounded-touch)
* [GR.BOUNDED.TOUCH2](#gr-bounded-touch2)
* [GR.BRIGHTNESS](#gr-brightness)
* [GR.CAMERA.AUTOSHOOT](#gr-camera-autoshoot)
* [GR.CAMERA.MANUALSHOOT](#gr-camera-manualshoot)
* [GR.CAMERA.SELECT](#gr-camera-select)
* [GR.CAMERA.SHOOT](#gr-camera-shoot)
* [GR.CIRCLE](#gr-circle)
* [GR.CLIP](#gr-clip)
* [GR.CLOSE](#gr-close)
* [GR.CLS](#gr-cls)
* [GR.COLOR](#gr-color)
* [GR.FRONT](#gr-front)
* [GR.GET.BMPIXEL](#gr-get-bmpixel)
* [GR.GET.PARAMS](#gr-get-params)
* [GR.GET.PIXEL](#gr-get-pixel)
* [GR.GET.POSITION](#gr-get-position)
* [GR.GET.TEXTBOUNDS](#gr-get-textbounds)
* [GR.GET.TYPE](#gr-get-type)
* [GR.GET.VALUE](#gr-get-value)
* [GR.GETDL](#gr-getdl)
* [GR.GROUP](#gr-group)
* [GR.GROUP.GETDL](#gr-group-getdl)
* [GR.GROUP.LIST](#gr-group-list)
* [GR.GROUP.NEWDL](#gr-group-newdl)
* [GR.HIDE](#gr-hide)
* [GR.LINE](#gr-line)
* [GR.MODIFY](#gr-modify)
* [GR.MOVE](#gr-move)
* [GR.NEWDL](#gr-newdl)
* [GR.ONGRTOUCH.RESUME](#gr-ongrtouch-resume)
* [GR.OPEN](#gr-open)
* [GR.ORIENTATION](#gr-orientation)
* [GR.OVAL](#gr-oval)
* [GR.PAINT.COPY](#gr-paint-copy)
* [GR.PAINT.GET](#gr-paint-get)
* [GR.PAINT.RESET](#gr-paint-reset)
* [GR.POINT](#gr-point)
* [GR.POLY](#gr-poly)
* [GR.RECT](#gr-rect)
* [GR.RENDER](#gr-render)
* [GR.ROTATE.END](#gr-rotate-end)
* [GR.ROTATE.START](#gr-rotate-start)
* [GR.SAVE](#gr-save)
* [GR.SCALE](#gr-scale)
* [GR.SCREEN](#gr-screen)
* [GR.SCREEN.TO_BITMAP](#gr-screen-to-bitmap)
* [GR.SET.ANTIALIAS](#gr-set-antialias)
* [GR.SET.PIXELS](#gr-set-pixels)
* [GR.SET.STROKE](#gr-set-stroke)
* [GR.SHOW](#gr-show)
* [GR.SHOW.TOGGLE](#gr-show-toggle)
* [GR.STATUSBAR](#gr-statusbar)
* [GR.STATUSBAR.SHOW](#gr-statusbar-show)
* [GR.TEXT.ALIGN](#gr-text-align)
* [GR.TEXT.BOLD](#gr-text-bold)
* [GR.TEXT.DRAW](#gr-text-draw)
* [GR.TEXT.HEIGHT](#gr-text-height)
* [GR.TEXT.SETFONT](#gr-text-setfont)
* [GR.TEXT.SIZE](#gr-text-size)
* [GR.TEXT.SKEW](#gr-text-skew)
* [GR.TEXT.STRIKE](#gr-text-strike)
* [GR.TEXT.TYPEFACE](#gr-text-typeface)
* [GR.TEXT.UNDERLINE](#gr-text-underline)
* [GR.TEXT.WIDTH](#gr-text-width)
* [GR.TOUCH](#gr-touch)
* [GR.TOUCH2](#gr-touch2)
* [GR_COLLISION](#gr-collision)
* [GRABFILE](#grabfile)
* [GRABURL](#graburl)

## H
* [HEADSET](#headset)
* [HEX](#hex)
* [HEX$](#hex-1)
* [HOME](#home)
* [HTML.CLEAR.CACHE](#html-clear-cache)
* [HTML.CLEAR.HISTORY](#html-clear-history)
* [HTML.CLOSE](#html-close)
* [HTML.GET.DATALINK](#html-get-datalink)
* [HTML.GO.BACK](#html-go-back)
* [HTML.GO.FORWARD](#html-go-forward)
* [HTML.LOAD.STRING](#html-load-string)
* [HTML.LOAD.URL](#html-load-url)
* [HTML.OPEN](#html-open)
* [HTML.ORIENTATION](#html-orientation)
* [HTML.POST](#html-post)
* [HTTP.POST](#http-post)
* [HYPOT](#hypot)

## I
* [IF](#if)
* [INCLUDE](#include)
* [INKEY$](#inkey)
* [INPUT](#input)
* [INPUT.LINE](#input-line)
* [INPUT.TEXT](#input-text)
* [INSTR](#instr)
* [INT](#int)
* [INT$](#int-1)
* [IS_IN](#is-in)
* [IS_NUMBER](#is-number)

## J
* [JOIN](#join)
* [JOIN.ALL](#join-all)

## K
* [KB.HIDE](#kb-hide)
* [KB.RESUME](#kb-resume)
* [KB.SHOW](#kb-show)
* [KB.SHOWING](#kb-showing)
* [KB.TOGGLE](#kb-toggle)
* [KEY.RESUME](#key-resume)
* [KILL](#kill)

## L
* [LCASE$](#lcase)
* [LEFT$](#left)
* [LEN](#len)
* [LET](#let)
* [LINE INPUT](#line-input)
* [LIST.ADD](#list-add)
* [LIST.ADD.ARRAY](#list-add-array)
* [LIST.ADD.LIST](#list-add-list)
* [LIST.CLEAR](#list-clear)
* [LIST.CREATE](#list-create)
* [LIST.GET](#list-get)
* [LIST.INSERT](#list-insert)
* [LIST.REMOVE](#list-remove)
* [LIST.REPLACE](#list-replace)
* [LIST.SEARCH](#list-search)
* [LIST.LEN](#list-len)
* [LIST.TOARRAY](#list-toarray)
* [LIST.TYPE](#list-type)
* [LOG](#log)
* [LOG10](#log10)
* [LOWMEMORY.RESUME](#lowmemory-resume)
* [LTRIM$](#ltrim)

## M
* [MAX](#max)
* [MENUKEY.RESUME](#menukey-resume)
* [MID$](#mid)
* [MIN](#min)
* [MKDIR](#mkdir)
* [MOD](#mod)
* [MYPHONENUMBER](#myphonenumber)

## N
* [NEXT](#for)
* [NOT](#not)
* [NOTIFY](#notify)

## O
* [OCT](#oct)
* [OCT$](#oct-1)
* [ONBACKGROUND](#onbackground)
* [ONBACKKEY](#onbackkey)
* [ONBTREADREADY](#onbtreadready)
* [ONCONSOLETOUCH](#onconsoletouch)
* [ONERROR](#onerror)
* [ONGRTOUCH](#ongrtouch)
* [ONKBCHANGE](#onkbchange)
* [ONKEYPRESS](#onkeypress)
* [ONLOWMEMORY](#onlowmemory)
* [ONMENUKEY](#onmenukey)
* [ONTIMER](#ontimer)
* [OPEN](#open-statement)
* [OR](#or)

## P
* [PARSE$](#parse)
* [PARSECOUNT](#parsecount)
* [PERMISSION](#permission-statement)
* [PERMISSION$](#permission-function)
* [PHONE.CALL](#phone-call)
* [PHONE.DIAL](#phone-dial)
* [PHONE.INFO](#phone-info)
* [PHONE.RCV.INIT](#phone-rcv-init)
* [PHONE.RCV.NEXT](#phone-rcv-next)
* [PI](#pi)
* [POPUP](#popup)
* [POW](#pow)
* [PRINT](#print-disambiguation)
* [PROGRAM.INFO](#program-info)
* [PUT](#put)
* [PUT$](#put-1)

## R
* [RANDOMIZE](#randomize)
* [READ](#open-statement)
* [READ.DATA](#read-data)
* [READ.FROM](#read-from)
* [READ.NEXT](#read-next)
* [REDIM](#redim)
* [REM](#rem)
* [REPLACE$](#replace)
* [RETURN](#return)
* [RIGHT$](#right)
* [RINGER.GET.MODE](#ringer-get-mode)
* [RINGER.GET.VOLUME](#ringer-get-volume)
* [RINGER.SET.MODE](#ringer-set-mode)
* [RINGER.SET.VOLUME](#ringer-set-volume)
* [RND](#rnd)
* [ROUND](#round)
* [RTRIM$](#rtrim)
* [RUN](#run)

## S
* [SCREEN](#screen)
* [SCREEN.ROTATION](#screen-rotation)
* [SCREEN.SIZE](#screen-size)
* [SEEK](seek-disambiguation)
* [SELECT CASE](#select)
* [SENSORS.CLOSE](#sensors-close)
* [SENSORS.LIST](#sensors-list)
* [SENSORS.OPEN](#sensors-open)
* [SENSORS.READ](#sensors-read)
* [SETBOF](#setbof)
* [SETEOF](#seteof)
* [SETSOF](#setbof)
* [SGN](#sgn)
* [SHIFT](#shift)
* [SIN](#sin)
* [SINH](#sinh)
* [SLEEP](#sleep)
* [SMS.RCV.INIT](#sms-rcv-init)
* [SMS.RCV.NEXT](#sms-rcv-next)
* [SMS.SEND](#sms-send)
* [SOCKET.CLIENT.CLOSE](#socket-client-close)
* [SOCKET.CLIENT.CONNECT](#socket-client-connect)
* [SOCKET.CLIENT.READ.FILE](#socket-client-read-file)
* [SOCKET.CLIENT.READ.LINE](#socket-client-read-line)
* [SOCKET.CLIENT.READ.READY](#socket-client-read-ready)
* [SOCKET.CLIENT.SERVER.IP](#socket-client-server-ip)
* [SOCKET.CLIENT.STATUS](#socket-client-status)
* [SOCKET.CLIENT.WRITE.BYTES](#socket-client-write-bytes)
* [SOCKET.CLIENT.WRITE.FILE](#socket-client-write-file)
* [SOCKET.CLIENT.WRITE.LINE](#socket-client-write-line)
* [SOCKET.MYIP](#socket-myip)
* [SOCKET.SERVER.CLIENT.IP](#socket-server-client-ip)
* [SOCKET.SERVER.CLOSE](#socket-server-close)
* [SOCKET.SERVER.CONNECT](#socket-server-connect)
* [SOCKET.SERVER.CREATE](#socket-server-create)
* [SOCKET.SERVER.DISCONNECT](#socket-server-disconnect)
* [SOCKET.SERVER.READ.FILE](#socket-server-read-file)
* [SOCKET.SERVER.READ.LINE](#socket-server-read-line)
* [SOCKET.SERVER.READ.READY](#socket-server-read-ready)
* [SOCKET.SERVER.STATUS](#socket-server-status)
* [SOCKET.SERVER.WRITE.BYTES](#socket-server-write-bytes)
* [SOCKET.SERVER.WRITE.FILE](#socket-server-write-file)
* [SOCKET.SERVER.WRITE.LINE](#socket-server-write-line)
* [SOUNDPOOL.LOAD](#soundpool-load)
* [SOUNDPOOL.OPEN](#soundpool-open)
* [SOUNDPOOL.PAUSE](#soundpool-pause)
* [SOUNDPOOL.PLAY](#soundpool-play)
* [SOUNDPOOL.RELEASE](#soundpool-release)
* [SOUNDPOOL.RESUME](#soundpool-resume)
* [SOUNDPOOL.SETPRIORITY](#soundpool-setpriority)
* [SOUNDPOOL.SETRATE](#soundpool-setrate)
* [SOUNDPOOL.SETVOLUME](#soundpool-setvolume)
* [SOUNDPOOL.STOP](#soundpool-stop)
* [SOUNDPOOL.UNLOAD](#soundpool-unload)
* [SPLIT](#split)
* [SPLIT.ALL](#split-all)
* [SQL.CLOSE](#sql-close)
* [SQL.DELETE](#sql-delete)
* [SQL.DROP_TABLE](#sql-drop-table)
* [SQL.EXEC](#sql-exec)
* [SQL.INSERT](#sql-insert)
* [SQL.NEW_TABLE](#sql-new-table)
* [SQL.NEXT](#sql-next)
* [SQL.OPEN](#sql-open)
* [SQL.QUERY](#sql-query)
* [SQL.QUERY.LENGTH](#sql-query-length)
* [SQL.QUERY.POSITION](#sql-query-position)
* [SQL.RAW_QUERY](#sql-raw-query)
* [SQL.UPDATE](#sql-update)
* [SQR](#sqr)
* [STACK.CLEAR](#stack-clear)
* [STACK.CREATE](#stack-create)
* [STACK.ISEMPTY](#stack-isempty)
* [STACK.PEEK](#stack-peek)
* [STACK.POP](#stack-pop)
* [STACK.PUSH](#stack-push)
* [STACK.TYPE](#stack-type)
* [STARTS_WITH](#starts-with)
* [STR$](#str)
* [STT.LISTEN](#stt-listen)
* [STT.RESULTS](#stt-results)
* [SU.CLOSE](#su-close)
* [SU.OPEN](#su-open)
* [SU.READ.LINE](#su-read-line)
* [SU.READ.READY](#su-read-ready)
* [SU.WRITE](#su-write)
* [SUB](#sub)
* [SWAP](#swap)
* [SYSTEM.CLOSE](#system-close)
* [SYSTEM.OPEN](#system-open)
* [SYSTEM.READ.LINE](#system-read-line)
* [SYSTEM.READ.READY](#system-read-ready)
* [SYSTEM.WRITE](#system-write)

## T
* [TALLY](#tally)
* [TAN](#tan)
* [TEXT](#open-statement)
* [THEN](#if)
* [TIME](#time)
* [TIMER.CLEAR](#timer-clear)
* [TIMER.RESUME](#timer-resume)
* [TIMER.SET](#timer-set)
* [TIMEZONE.GET](#timezone-get)
* [TIMEZONE.LIST](#timezone-list)
* [TIMEZONE.SET](#timezone-set)
* [TODEGREES](#todegrees)
* [TONE](#tone)
* [TORADIANS](#toradians)
* [TRIM$](#trim)
* [TTS.INIT](#tts-init)
* [TTS.SPEAK](#tts-speak)
* [TTS.SPEAK.TOFILE](#tts-speak-tofile)
* [TTS.STOP](#tts-stop)

## U
* [UBOUND](#ubound)
* [UCASE$](#ucase)
* [UCODE](#ucode)
* [UNDIM](#undim)
* [UNTIL](#do)
* [USING$](#using)

## V
* [VAL](#val)
* [VERSION$](#version)
* [VIBRATE](#vibrate)
* [VOLKEYS.OFF](#volkeys-off)
* [VOLKEYS.ON](#volkeys-on)

## W
* [WAKELOCK](#wakelock)
* [WEND](#while)
* [WHILE](#while)
* [WIFI.INFO](#wifi-info)
* [WIFILOCK](#wifilock)
* [WORD$](#word)
* [WRITE](#open-statement)

## Z
* [ZCOUNT](#zcount)
* [ZDIR](#zdir)
* [ZIP](#open-statement)
* [ZREAD](#zread)
* [ZWRITE](#zwrite)

**See also:**
* [Command summary](#command-summary)
* [Format and typefaces](#format-and-typefaces)

<!------------------------------------------------------------------------------->
# Differences with RFO BASIC!
basica is based on the excellent RFO BASIC! for Android, with the goal to remove much of its inconsistencies, and also rename or refactor some commands to follow basica's [dogmata](#dogmata) (especially dogma 1 and dogma 2).

## Changes in flow control
RFO BASIC! | basica
-----------|-------
D_U.BREAK | EXIT DO
D_U.CONTINUE | ITERATE DO
F_N.BREAK | EXIT FOR
F_N.CONTINUE | ITERATE FOR
SW.BEGIN | SELECT CASE
SW.BREAK | **removed** not needed anymore: any `CASE` or `END SELECT` will do
SW.CASE | CASE {IS}
SW.DEFAULT | CASE ELSE
SW.END | END SELECT
W_R.BREAK | EXIT WHILE
W_R.CONTINUE | ITERATE WHILE
WHILE-REPEAT | WHILE-WEND

## Changes in BYTE.* commands
RFO BASIC! | basica
-----------|-------
BYTE.CLOSE *fileNum* | CLOSE {#}*fileNum*
BYTE.COPY *fileNum*, *targetFile$* | **removed**, use FILE.COPY *sourceFile$*, *targetFile$* instead
BYTE.EOF *fileNum*, *isEof* | isEof = EOF ( {#}*fileNum* )
BYTE.OPEN r&#124;w&#124;a, *fileNum*, *file$* | OPEN *file$* FOR BINARY READ&#124;WRITE&#124;APPEND AS {#}*fileNum*
BYTE.POSITION.GET *fileNum*, *position* | position = SEEK ( {#}*fileNum* )
BYTE.POSITION.MARK *fileNum*, *position* | SETBOF&#124;SETSOF {#}*fileNum*, *position*
BYTE.POSITION.SET *fileNum*, *position* | SEEK {#}*fileNum*, *position*
BYTE.READ.BUFFER *fileNum*, *count*, *buffer$* | GET$ {#}*fileNum*, *count*, *buffer$*
BYTE.READ.BYTE *fileNum*, *byte1* {,*byte2*} ... | **removed**, use GET$ {#}*fileNum*, *count*, *buffer$* and read each byte of *buffer$* instead
BYTE.READ.NUMBER *fileNum*, *num1* {,*num2*} ... | GET {#}*fileNum*, *num1* {,*num2*} ...
BYTE.TRUNCATE *fileNum*, *length* | See SETEOF {#}*fileNum* that truncates to the current file pointer
BYTE.WRITE.BUFFER *fileNum*, *buffer$* | PUT$ {#}*fileNum*, *buffer$*
BYTE.WRITE.BYTE *fileNum*, *byte1* {,*byte2*} ... | **removed**, use PUT$ {#}*fileNum*, CHR$(*byte1*) {+CHR$(*byte2*)} ... instead
BYTE.WRITE.NUMBER *fileNum*, *num1* {,*num2*} ... | PUT {#}*fileNum*, *num1* {,*num2*} ...

## Changes in TEXT.* commands
RFO BASIC! | basica
-----------|-------
TEXT.CLOSE *fileNum* | CLOSE {#}*fileNum*
TEXT.EOF *fileNum*, *isEof* | isEof = EOF ( {#}*fileNum* )
TEXT.OPEN r&#124;w&#124;a, *fileNum*, *file$* | OPEN *file$* FOR TEXT READ&#124;WRITE&#124;APPEND AS {#}*fileNum*
TEXT.POSITION.GET *fileNum*, *position* | position = SEEK ( {#}*fileNum* )
TEXT.POSITION.MARK *fileNum*, *position* | SETBOF &#124; SETSOF {#}*fileNum*, *position*
TEXT.POSITION.SET *fileNum*, *position* | SEEK {#}*fileNum*, *position*
TEXT.READLN *fileNum*, *line$* | LINE INPUT **#***fileNum*, *line$*
TEXT.WRITELN *fileNum*, *num1*&#124;*string1$* {*num2*&#124;*string2$*} ... | PRINT **#***fileNum*, *num1*&#124;*string1$* {*num2*&#124;*string2$*} ...

## Changes in ZIP.* commands
RFO BASIC! | basica
-----------|-------
ZIP.CLOSE *fileNum* | CLOSE {#}*fileNum*
ZIP.COUNT *zip$*, *n_entries* | ZCOUNT *zip$*, *n_entries*
ZIP.DIR *zip$*, *entries$[]* | ZDIR *zip$*, *entries$[]*
ZIP.OPEN r&#124;w, *fileNum*, *file$* | OPEN *file$* FOR ZIP READ&#124;WRITE AS {#}*fileNum*
ZIP.READ *fileNum*, *buffer$*, *entry$* | ZREAD {#}*fileNum*, *entry$* TO *buffer$*
ZIP.WRITE *fileNum*, *buffer$*, *entry$* | ZWRITE *buffer$* TO {#}*fileNum*, *entry$*

## Changes in order of parameters
RFO BASIC! | basica
-----------|-------
ARRAY.AVERAGE | ARRAY.AVERAGE *array[]*, *average*
ARRAY.LENGTH | ARRAY.LEN *array[]*, *length*
ARRAY.MAX | ARRAY.MAX *array[]*, *max*
ARRAY.MIN | ARRAY.MIN *array[]*, *min*
ARRAY.STD_DEV | ARRAY.STD_DEV *array[]*, *std_dev*
ARRAY.SUM | ARRAY.SUM *array[]*, *sum*
ARRAY.VARIANCE | ARRAY.MAX *array[]*, *variance*
LIST.SIZE | LIST.LEN *listId*, *length*
FILE.DELETE | FILE.DELETE *file$*, *delOK*
FILE.EXISTS | FILE.EXISTS *file$*, *exists*
FILE.SIZE | FILE.SIZE *file$*, *size*
FILE.TYPE | FILE.TYPE *file$*, *type*
GR.TEXT.DRAW | GR.TEXT.DRAW *grObjId*, *text$*, *drawX*, *drawY*

## Other changes
RFO BASIC! | basica
-----------|-------
&#126; (line continuation) | underscore &#95;
&#33; (comment) | single quote &#39;
&#37; (inline comment) | single quote &#39;
&#33;&#33; (block comment) | **removed**, use &#39; in front of each line instead
&#33; (operator) | NOT
&#38; | AND
&#124; | OR
CONSOLE.* commands | renamed as CON.* commands
SELECT | CON.SELECT
PAUSE | SLEEP
FN.DEF | SUB&#124;FUNCTION funcName{$} ( {param1{$}} {,param2{$}} ... )
FN.END | END SUB&#124;FUNCTION
FN.RTN value{$} | RETURN value{$}, EXIT SUB&#124;FUNCTION
GR_COLISION | GR.COLISION grObjId1, grObjId2, collision
LOWER$ | LCASE$
UPPER$ | UCASE$
TGET | INPUT prompt$, result{$}
INPUT | INPUT.LINE
TEXT.INPUT | INPUT.TEXT

# Additions
* [Arithmetic operator](#arithmetic-operators) `\` for integral division
* [INSTR](#instr)
* [CHDIR](#chdir)
* [FILE.COPY](#file-copy)
* [KILL](#kill)
* [LOF](#lof), [SETBOF](#setbof)/[SETSOF](#setbof) and [SETEOF](#seteof)
* [PERMISSION](#permission-statement) and [PERMISSION$](#permission-function)
* [PARSECOUNT](#parsecount), [PARSE$](#parse) and [TALLY](#tally)
* [REDIM](#redim) and [REDIM PRESERVE](#redim)
* [UBOUND](#ubound)

Back to [basica](#basica)

<!------------------------------------------------------------------------------->
# Array, List, Stack and Bundle
The following functions can be used to manipulate and manage arrays:
* [ARRAY.AVERAGE](#array-average)
* [ARRAY.COPY](#array-copy)
* [ARRAY.DELETE](#array-delete)
* [ARRAY.DIMS](#array-dims)
* [ARRAY.FILL](#array-fill)
* [ARRAY.LEN](#array-len)
* [ARRAY.LOAD](#array-load)
* [ARRAY.MAX](#array-max)
* [ARRAY.MIN](#array-min)
* [ARRAY.REVERSE](#array-reverse)
* [ARRAY.SEARCH](#array-search)
* [ARRAY.SHUFFLE](#array-shuffle)
* [ARRAY.SORT](#array-sort)
* [ARRAY.STD_DEV](#array-std-dev)
* [ARRAY.SUM](#array-sum)
* [ARRAY.VARIANCE](#array-variance)
* [DEBUG.DUMP.ARRAY](#debug-dump-array)
* [DEBUG.SHOW.ARRAY](#debug-show-array)
* [DIM](#dim)
* [JOIN](#join)
* [JOIN.ALL](#join-all)
* [LIST.ADD.ARRAY](#list-add-array)
* [LIST.TOARRAY](#list-toarray)
* [REDIM](#redim)
* [UNDIM](#undim)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Communication Control
The following functions can be used for external communications:
* [Bluetooth Commands](#bluetooth-commands)
* [EMAIL.SEND](#email-send)
* [FTP Commands](#ftp-commands)
* [GRABURL](#graburl)
* [HTTP.POST](#http-post)
* [PHONE.CALL](#phone-call)
* [PHONE.DIAL](#phone-dial)
* [PHONE.RCV.INIT](#phone-rcv-init)
* [PHONE.RCV.NEXT](#phone-rcv-next)
* [SMS.RCV.INIT](#sms-rcv-init)
* [SMS.RCV.NEXT](#sms-rcv-next)
* [SMS.SEND](#sms-send)
* [Socket (TCP/IP) Commands](#socket-tcp-ip-commands)
* [WIFI.INFO](#wifi-info)
* [WIFILOCK](#wifilock)

Back to [Command summary](#command-summary)

# Bluetooth Commands
The following commands can be used to communicate with a device by bluetooth:
* [BT.CLOSE](#bt-close)
* [BT.CONNECT](#bt-connect)
* [BT.DEVICE.NAME](#bt-device-name)
* [BT.DISCONNECT](#bt-disconnect)
* [BT.ONREADREADY.RESUME](#bt-onreadready-resume)
* [BT.OPEN](#bt-open)
* [BT.READ.BYTES](#bt-read-bytes)
* [BT.READ.READY](#bt-read-ready)
* [BT.RECONNECT](#bt-reconnect)
* [BT.SET.UUID](#bt-set-uuid)
* [BT.STATUS](#bt-status)
* [BT.WRITE](#bt-write)
* [ONBTREADREADY](#onbtreadready)

Back to [Communication Control](#communication-control)

# FTP Commands
The following commands can be used to operate the File Transfer Protocol (FTP):
* [FTP.CD](#ftp-cd)
* [FTP.CLOSE](#ftp-close)
* [FTP.DELETE](#ftp-delete)
* [FTP.DIR](#ftp-dir)
* [FTP.GET](#ftp-get)
* [FTP.MKDIR](#ftp-mkdir)
* [FTP.OPEN](#ftp-open)
* [FTP.PUT](#ftp-put)
* [FTP.RENAME](#ftp-rename)
* [FTP.RMDIR](#ftp-rmdir)

Back to [Communication Control](#communication-control)

# Socket (TCP/IP) Commands
The following commands can be used to handle TCP/IP sockets:
* [SOCKET.CLIENT.CLOSE](#socket-client-close)
* [SOCKET.CLIENT.CONNECT](#socket-client-connect)
* [SOCKET.CLIENT.READ.FILE](#socket-client-read-file)
* [SOCKET.CLIENT.READ.LINE](#socket-client-read-line)
* [SOCKET.CLIENT.READ.READY](#socket-client-read-ready)
* [SOCKET.CLIENT.SERVER.IP](#socket-client-server-ip)
* [SOCKET.CLIENT.STATUS](#socket-client-status)
* [SOCKET.CLIENT.WRITE.BYTES](#socket-client-write-bytes)
* [SOCKET.CLIENT.WRITE.FILE](#socket-client-write-file)
* [SOCKET.CLIENT.WRITE.LINE](#socket-client-write-line)
* [SOCKET.MYIP](#socket-myip)
* [SOCKET.SERVER.CLIENT.IP](#socket-server-client-ip)
* [SOCKET.SERVER.CLOSE](#socket-server-close)
* [SOCKET.SERVER.CONNECT](#socket-server-connect)
* [SOCKET.SERVER.CREATE](#socket-server-create)
* [SOCKET.SERVER.DISCONNECT](#socket-server-disconnect)
* [SOCKET.SERVER.READ.FILE](#socket-server-read-file)
* [SOCKET.SERVER.READ.LINE](#socket-server-read-line)
* [SOCKET.SERVER.READ.READY](#socket-server-read-ready)
* [SOCKET.SERVER.STATUS](#socket-server-status)
* [SOCKET.SERVER.WRITE.BYTES](#socket-server-write-bytes)
* [SOCKET.SERVER.WRITE.FILE](#socket-server-write-file)
* [SOCKET.SERVER.WRITE.LINE](#socket-server-write-line)

Back to [Communication Control](#communication-control)

<!------------------------------------------------------------------------------->
# Compiler Operations
The following functions manipulate the compiler's operation:

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Console Commands

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Debugging and Error Control

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# File Commands
The following functions can be used to manipulate files:
* [BROWSE](#browse)
* [CHDIR](#chdir)
* [CLOSE](#close)
* [EOF](#eof)
* [FILE.COPY](#file-copy)
* [FILE.DELETE](#file-delete)
* [FILE.DIR](#file-dir)
* [FILE.EXISTS](#file-exists)
* [FILE.MKDIR](#file-mkdir)
* [FILE.RENAME](#file-rename)
* [FILE.ROOT](#file-root)
* [FILE.SIZE](#file-size)
* [FILE.TYPE](#file-type)
* [GET](#get)
* [GET$](#get-1)
* [GRABFILE](#grabfile)
* [KILL](#kill)
* [LINE INPUT](#line-input)
* [MKDIR](#mkdir)
* [OPEN](#open-statement)
* [PRINT#](print-1)
* [PUT](#put)
* [PUT$](#put-1)
* [SEEK](seek-disambiguation)
* [SETBOF](#setbof)
* [SETEOF](#seteof)
* [SETSOF](#setbof)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Flow Control

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Graphic Commands

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Html Commands

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Input Commands

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Memory Management
* [AUDIO.LOAD](#audio-load)
* [AUDIO.RELEASE](#audio-release)
* [BUNDLE.CLEAR](#bundle-clear)
* [BUNDLE.CREATE](#bundle-create)
* [DIM](#dim)
* [FONT.CLEAR](#font-clear)
* [FONT.DELETE](#font-delete)
* [FONT.LOAD](#font-load)
* [GR.BITMAP.CREATE](#gr-bitmap-create)
* [GR.BITMAP.CROP](#gr-bitmap-crop)
* [GR.BITMAP.DELETE](#gr-bitmap-delete)
* [GR.BITMAP.LOAD](#gr-bitmap-load)
* [GR.BITMAP.SCALE](#gr-bitmap-scale)
* [LIST.CLEAR](#list-clear)
* [LIST.CREATE](#list-create)
* [LOWMEMORY.RESUME](#lowmemory-resume)
* [ONLOWMEMORY](#onlowmemory)
* [REDIM](#redim)
* [SOUNDPOOL.LOAD](#soundpool-load)
* [SOUNDPOOL.RELEASE](#soundpool-release)
* [SOUNDPOOL.UNLOAD](#soundpool-unload)
* [STACK.CLEAR](#stack-clear)
* [STACK.CREATE](#stack-create)
* [UNDIM](#undim)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Numeric Operations

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Operating System

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Sound Commands

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# SQL Commands

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# String Operations

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Time Commands

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Misc Operations

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# BIN function
**Purpose:**
Convert a binary string to a numeric value.

**Syntax:**
> number = BIN(*base2$*)

**Remarks:**
The characters of *base2$* can be only binary digits (0 or 1), with an optional leading sign ("+" or "-"), or the function generates a runtime error.

**See also:**
* [BIN$](#bin-function-1)
* [HEX](#hex) and [HEX$](#hex-1)
* [OCT](#oct) and [OCT$](#oct-1)

**Examples:**
```vb
PRINT "Value of binary string '10101010':"
PRINT BIN("10101010") ' will print 170.0
```

<!------------------------------------------------------------------------------->
# BIN$ function
**Purpose:**
Convert a numeric value to a binary string.

**Syntax:**
> s$ = BIN$(*number*)

**Remarks:**
*number* is a numeric expression in the range of a 64-bit integer (-9223372036854775808 to +9223372036854775807). Any fractional part of the value is rounded. The result string is always formatted as an integral number using all the significant digits in *number*. It is never expressed in scientific notation.

**See also:**
* [BIN](#bin-function)
* [HEX](#hex) and [HEX$](#hex-1)
* [OCT](#oct) and [OCT$](#oct-1)

**Examples:**
```vb
PRINT "Binary string for number 170:"
PRINT BIN$(170) ' will print "10101010"
```

<!------------------------------------------------------------------------------->
# Files
basica offers three distinct ways to store and retrieve information from the file system: BINARY, TEXT, and ZIP file read and write. Each has its advantages and disadvantages; the one that works best for you will depend on your application.

**See:**
* [Text Files](#text-files)
* [Binary Files](#binary-files)
* [Zip Files](#zip-files)

<!------------------------------------------------------------------------------->
# Variables
A basica variable is a container for some number or string value. The value of a variable can change during program execution.

## Variable Names
Like a label or a user-defined `SUB` or `FUNCTION`, a variable name must start with the characters "a" through "z". The remaining characters may also include the digits "0" through "9" and the special characters "#", "@", and "_". A variable name may be as long as needed.

There is no case in basica variable names: the variable "gLoP" is the same as the variable "glop" to basica.

## Variable Types
basica has only two types of variables: variables that hold numbers and variables that hold strings. Variables that hold strings end with the character "$". Variables that hold numbers do not end in "$".

*Age*, *amount* and *HEIGHT* are all numeric variable names.

*First_Name$*, *Street$* and *A$* are all string variable names.

basica variables do not need to be declared (except if you want them [GLOBAL](#global)). This is a big difference with Visual Basic, PowerBasic and FreeBasic: in basica, any new variable name is considered a valid variable.
If you use a numeric variable without assigning it a value, it has the value 0.0. If you use a string variable without assigning it a value, its value is the empty string "".

In detail, basica numbers are double-precision 64-bit IEEE 754 floating point numbers. Their range of values is 4.94065645841246544e-324d to 1.79769313486231570e+308d (positive or negative). basica strings are a series of 0 or more bytes (ASCII value 0-255) and can be encoded with different charsets, for different uses. By default basica strings can either be UTF-16 `TEXT` strings or ISO-8859-1 byte buffers.

<!------------------------------------------------------------------------------->
# Text Files
Text [files](#files) provide a straightforward way to read and write human readable data. basica's text file commands manipulate strings of characters that are separated by carriage-return and/or line-feed, used to separate records.

Quite possibly, the best reason for using text files is their degree of portability to other programs, programming languages, and OSes. Because of this, you can often look at text files as the common denominator of data processing, since they can be read by word-processing programs and editors (such as basica's), absorbed by other applications (such as database managers), and sent over the Internet to other computers.

The idea behind text files is simplicity itself: write to them as though they were the screen and read from them as though they were the keyboard.

Create a text file using the following steps:

1. Create the file in `TEXT` mode. To create a file in basica, you must use the [OPEN](#open-statement) statement.
`TEXT` mode has two access options to prepare a file for output:
  * `TEXT WRITE`: If a file does not exist, a new file is created. If a file already exists, its contents are erased, and the file is then treated as a new file.
  * `TEXT APPEND`: If a file does not exist, a new file is created. If a file already exists, basica appends (adds) data at the end of that file.
2. Output data to the file. Use [PRINT#](#print-1) to write data to a text file.
3. Close the file. The [CLOSE](#close) statement closes a file after the program has completed all I/O operations.

To read a text file:

1. First, [OPEN](#open-statement) the file in `TEXT READ` mode/access. This prepares the file for reading.
2. Read data in from the file. Use basica's [LINE INPUT](#line-input) statement.
3. Close the file. The [CLOSE](#close) statement closes a file after the program has completed all I/O operations.

The drawback to text files is that you only have sequential access to your data. You access one line at a time, starting with the first line. This means if you want to get to the last line in a text file of 23,000 lines, you will have to read the preceding 22,999 lines.

Text files, therefore, are best suited to applications that perform sequential processing (for example, counting words, checking spelling, printing mailing labels in file order) or in which all the data can be held in memory simultaneously. This allows you to read the entire file in one fell swoop at the start of a program and to write it all back at the end. In between, the information can be stored in an array or a list (in memory) which can be accessed randomly.

The [SEEK](#seek) statement can be used to change the position of the next line to be read. A position value of 1 will read the first line in the text file. You can use this trick to read an entire file, then use SEEK to reposition the file pointer to the start of the file, in order to process the data a second time. This is certainly quicker than closing and re-opening the file.

Reading or writing very large text files can cause Out of Memory errors. The reason is that basica allocates a buffer the size of the whole file to `OPEN` by default. If you want to operate on very large files you need to use the option `LEN = bufferSize` of the [OPEN](#open-statement) statement. To navigate in the file, you will then move the **BOF** (or **SOF**, they are synonymous: one meaning **B**eginning **O**f **F**ile the other **S**tart **O**f **F**ile) carret thanks to [SETBOF](#setbof)/[SETSOF](#setbof).

Text files lend themselves to database situations in which the length of individual records is variable. For example, suppose an alumni list had a comments field. Some people may have 100 bytes or more of comments. Others, perhaps most, will have none. Text files handle this problem without wasting disk space.

The `OPEN` statement also provides an optional charset parameter `CHR = charSet$`. This specifies the encoding charset for this file: "UTF-8", "UTF-16" (basica's default), "UTF-16BE", "UTF-16LE", "US-ASCII" or "ISO-8859-1". Since text files consist of text alone, the selected charset is enforced by basica. All data read or written to the file is automatically forced to the selected charset, regardless of the type of variables or expressions used. With binary or random files, this specification has no effect.

**See also:**
* [OPEN](#open-statement)
* [Binary Files](#binary-files)
* [Zip Files](#zip-files)

Back to [Files](#files)

<!------------------------------------------------------------------------------->
# Binary Files
Binary [files](#files) allow you to treat any file as a numbered sequence of bytes without regard to anything, including the following: charset encoding (ASCII, Unicode), number versus string considerations, record length, carriage returns. With the binary approach to a file problem, you read and write a file by specifying exactly which bytes to read or write.

Flexibility always comes at a price. Binary files require that you do all the work to decide what goes where. Binary may be the best option when dealing with alien files that aren't in [Text](#text-files) format; for example, a file created by a spreadsheet or database product. Of course, you will have to know the precise structure of the file before you can even attempt to break it down into numbers and strings agreeable to basica.

Every file opened in binary mode has an associated position indicator that points to the place in the file that will be read or written to next. Use the [SEEK](#seek) statement to set the position indicator, and the [SEEK](#seek-1) function to read it.

Data read from or written to binary files can either be [numerals](#variables) (a 64-bit number) or [strings](#variables) which are a collection of 0 or more bytes (a byte has an ASCII value of 0 to 255).

Binary files can be created in the following way:

1. Create the file in `BINARY` mode. To create a file in basica, you must use the [OPEN](#open-statement) statement.
`BINARY` mode has two access options to prepare a file for output:
  * `BINARY WRITE`: If a file does not exist, a new file is created. If a file already exists, its contents are erased, and the file is then treated as a new file.
  * `BINARY APPEND`: If a file does not exist, a new file is created. If a file already exists, basica appends (adds) data at the end of that file.
2. Output data to the file. Use [PUT](#put) to write a numeric or [PUT$](#put-1) to write a string (series of bytes) to a binary file. See [Variables](#variables) for details on numeric Vs string.
3. Close the file. The [CLOSE](#close) statement closes a file after the program has completed all I/O operations.

To read a binary file:

1. First, [OPEN](#open-statement) the file in `BINARY READ` mode/access. This prepares the file for reading.
2. Read data in from the file. Use basica's [GET](#get) or [GET$](#get-1) statements to respectively read a number or a string.
3. Close the file. The [CLOSE](#close) statement closes a file after the program has completed all I/O operations.

**See also:**
* [OPEN](#open-statement)
* [Text Files](#text-files)
* [Zip Files](#zip-files)

Back to [Files](#files)

<!------------------------------------------------------------------------------->
# Zip Files
Zip is an archive [file](#files) format that supports lossless data compression. A zip file may contain one or more files or directories, called "entries", that may have been compressed. Zip files usually have the extension .zip, .gzip, .zip64 (pkware zip), .jar or .apk (Android PacKage, the official format for Android apps). The zip format has been completely standardized, and is used by many programs on many different OSes.

Unlike [text files](#text-files) and [binary files](#binary-files), you can only read or write entries (or "files") to a zip file. Also, a zip file does not support the `APPEND` access method on Android (this is an OS limitation), you can only use `READ` or `WRITE`.

basica has two groups of commands to manipulate zip files:

## zip entries access commands

Zip files are created in the following way:

1. Create the file in `ZIP WRITE` mode thanks to the [OPEN](#open-statement) statement.
2. Output entries to the zip file. Use [ZWRITE](#zwrite) to store a [string](#variables) buffer to an entry.
3. Close the file. The [CLOSE](#close) statement closes a file after the program has completed all I/O operations.

To read a zip file:

1. First, [OPEN](#open-statement) the file in `ZIP READ` mode/access. This prepares the file for reading.
2. Read entries in from the file. Use basica's [ZREAD](#zread) to read an entry into a [string](#variables) buffer.
3. Close the file with [CLOSE](#close).

## zip file descriptor commands

These commands are useful if you want to access a zip file that you did not create (thus its content is unknown to you).

* You can count the number of entries in a zip file with the [ZCOUNT](#zcount) statement.
* And/or you can list the entries inside a zip file with the [ZDIR](#zdir) statement.

With the result of these commands, you can then open the zip file for `ZIP READ` and get each entry's content as desired.

**See also:**
* [OPEN](#open-statement)
* [Text Files](#text-files)
* [Binary Files](#binary-files)

Back to [Files](#files)

<!------------------------------------------------------------------------------->
# OPEN statement
**Purpose:**
Prepare a [file](#files) for reading or writing.

**Syntax:**
> OPEN *file$* FOR **Mode** **Access** AS {#}*fileNum* {LEN = *bufferSize*} {CHR = *charSet$*}

**Remarks:**
The main function of `OPEN` is to associate a file number (*fileNum*) with a file and to prepare that file for reading or writing. This file number is then used, rather than its name, in every statement that refers to the file.

Unlike VB PowerBasic and FreeBasic, there is no `FREEFILE` function to use before calling `OPEN`. In basica, the `OPEN` statement determines alone if the operation failed -in this case *fileNum* will contain `0`- or if it succeeded -in this case *fileNum* will contain the next unused file number. You cannot pick a file number yourself in basica.

An `OPEN` statement is usually balanced by a matching [CLOSE](#close) statement.

The `OPEN` statement comprises the following elements:
* *file$* is a [string expression](#variables) specifying the name of the file to be opened, and may optionally include a path specification. *file$* must respect the exact case of the path + filename. E.g. trying to open "/sdcard/MyFile.PNG" with `OPEN "/SdCard/myfile.png" ...` will **NOT** work. If *file$* is a URL starting with "http://" then an Internet file is opened, else a local file is opened. If no path is specified, the default path ("/sdcard") is used (see [Paths explained](#paths-explained)).

* **Mode** specifies the file organization and style of access (text, binary, or zip) for reading, writing, or appending. **Mode** needs to be specified as one of the following:

Mode | File type | Action
-----|-----------|-------
BINARY | Binary | can be used to read and write any type of file (.txt, .jpg, .pdf, .mp3, etc.). Each command reads or writes one byte or a sequence of bytes as binary data.
TEXT | Text | exclusively used for text (.txt) files. Text files are made up of lines of characters that end in "\r" (`CHR$(13)` = Carriage Return) and/or "\n" (`CHR$(10)` = New Line). Each command reads or writes entire lines.
ZIP | Archive | used to read and write archives: .zip, .gzip, .zip64 (pkware zip), .jar and .apk. Each command counts/lists/reads or writes entire files (known as "entries") in the archive.

* **Access** specifies the type of access this process will have to the file, among the following:

Access | Description | Modes concerned
-------|-------------|----------------
READ | Open the file for read operations only | BINARY, TEXT, ZIP
WRITE | Erase the content of the file (file is 0 byte) and opens it for write operations | BINARY, TEXT, ZIP
APPEND | Add data in write mode to an existing file | BINARY, TEXT
** Note that APPEND access is not supported in ZIP mode. This is an Android OS limitation. **

* *fileNum* is a numeric variable destined to store the unique integer value identifying the file.

* *bufferSize* (optional) specifies the size of the buffer to be used by basica. The default buffer size, if not specified, is the whole size of the file to `OPEN`. Changing *bufferSize* is an advanced technique that you will rarely need to use. You should only do it when the file is very large, to avoid Out Of Memory errors. In this case you should use a smaller buffer size (minimum size available is 8096 bytes) and move the **BOF**/**SOF** carret (**B**eginning/**S**tart **O**f **F**ile) accordingly. See [SETBOF](#setbof) or [SETSOF](#setbof) statements.

* *charSet$* (optional) is a string specifying the charset encoding to be used in TEXT mode only. Default is "UTF-16". You can choose among: "UTF-8", "UTF-16", "UTF-16BE", "UTF-16LE", "US-ASCII" and "ISO-8859-1".

**Restrictions:**
Attempting to OPEN a file for READ that does not exist returns a *fileNum* of `0`. It is always a good idea to test that *fileNum* is true (not zero) before proceeding to do read or write operations.

If you try to OPEN a nonexistent file for WRITE or APPEND, a new file is automatically created. For this reason, Internet files may only be opened in READ mode.

**See also:**
* [File Commands](#file-commands)
* [Files](#files)

**Examples:**
This program is divided into five procedures. The difference between each procedure is the mode in which the file is opened, and the way the data in the file is manipulated:
```vb
SUB TextWrite()
  ' The file is opened for text write, and some data is
  ' written to it.  If the file exists, it is over-written.
  OPEN "basica.data" FOR TEXT WRITE AS #fileNum
  IF NOT fileNum THEN END "Error opening file for text write"
  IntegerVar = 12345
  TempStr$ = "History is made at night."
  PRINT #fileNum, TempStr$, IntegerVar * 2, TempStr$, IntegerVar \ 2
  CLOSE #fileNum
  PRINT "Text write ok"
END SUB  ' end procedure Text Write

SUB TextAppend()
  ' The file is opened for text append, and data in this case is
  ' added to the end of file. If the file does not exist, it is created.
  OPEN "basica.data" FOR TEXT APPEND AS #fileNum
  IF NOT fileNum THEN END "Error opening file for text append"
  IntegerVar = 32123
  TempStr$ = "I am not a number!"
  PRINT #fileNum, TempStr$, IntegerVar * 0.2
  CLOSE #fileNum
  PRINT "Text append ok"
END SUB  ' end procedure Text Append

SUB TextRead()
  ' The file is opened for text read, and data is read from the file.
  OPEN "basica.data" FOR TEXT READ AS #fileNum
  IF NOT fileNum THEN END "Error opening file for text read"
  LINE INPUT #fileNum, TempStr$
  TempStr$ = ""
  WHILE NOT EOF(#fileNum)  ' check if at end of file
    LINE INPUT #fileNum, a$
    TempStr$ = TempStr$ + a$
  WEND
  PRINT TempStr$
  CLOSE #fileNum
  PRINT "Text read ok"
END SUB  ' end procedure Text Read

SUB BinaryIO()
  ' The file is opened for binary read. SEEK explicitly moves the file pointer
  ' to the end of file to get the last 3 bytes using GET$.
  OPEN "basica.data" FOR BINARY READ AS #fileNum
  IF NOT fileNum THEN END "Error opening file for binary read"
  SEEK #fileNum, LOF(#fileNum) - 2  ' To get bytes 'LOF-2', 'LOF-1' and 'LOF' (3 bytes)
  GET$ #fileNum, 3, ThreeLastChars$
  CLOSE #fileNum
  ' The file is then opened for binary append and the same data is written back
  ' at the end of the file.
  OPEN "basica.data" FOR BINARY APPEND AS #fileNum
  IF NOT fileNum THEN END "Error opening file for binary append"
  FOR i = 1 TO LEN(ThreeLastChars$)
    PUT$ #fileNum, MID$(ThreeLastChars$, i, 1)
  NEXT i
  CLOSE #fileNum
  PRINT "Binary I/O ok"
END SUB  ' end procedure Binary IO

SUB ZipIO()
  ' We open a new archive file for zip write and we put "basica.data" in it.
  GRABFILE "basica.data" TO basicaData$
  OPEN "basica.zip" FOR ZIP WRITE AS #fileNum
  IF NOT fileNum THEN END "Error opening file for zip write"
  ZWRITE basicaData$ TO #fileNum, "basica.data"
  CLOSE #fileNum
  ' Then we count the entries in the archive, and we list them.
  ZCOUNT "basica.zip", n_entries : PRINT n_entries ; " entries in basica.zip"
  ZDIR "basica.zip", entries$[]
  FOR i=1 TO UBOUND(entries$[])
    PRINT entries$[i]
  NEXT
  ' Finally we open the archive for zip read and we extract the content of "basica.data"
  OPEN "basica.zip" FOR ZIP READ AS #fileNum
  IF NOT fileNum THEN END "Error opening file for zip read"
  ZREAD #fileNum, "basica.data" TO basicaData$
  PRINT basicaData$
  CLOSE #fileNum
  PRINT "Binary I/O ok"
END SUB  ' end procedure Zip IO

CALL TextWrite()
CALL TextAppend()
CALL TextRead()
CALL BinaryIO()
CALL ZipIO()
```

<!------------------------------------------------------------------------------->
# END (disambiguation)
See:
* [END](#end) to end the current program and display the console
* [END FUNCTION](#function) to end a FUNCTION declaration
* [END IF](#if) to end an IF block
* [END SELECT](#select-case) to end a SELECT CASE block
* [END SUB](#sub) to end a SUB declaration

<!------------------------------------------------------------------------------->
# EXIT (disambiguation)
See:
* [EXIT](#exit) to exit the program and go back to the Home screen
* [EXIT DO](#do) to exit a DO-UNTIL loop
* [EXIT FOR](#for) to exit a FOR-NEXT loop
* [EXIT FUNCTION](#function) to exit a FUNCTION
* [EXIT SUB](#sub) to exit a SUB
* [EXIT WHILE](#while) to exit a WHILE-WEND loop

<!------------------------------------------------------------------------------->
# PRINT (disambiguation)
See:
* [PRINT](#print) to print a number or string to console
* [PRINT#](#print-1) to write in a TEXT file

<!------------------------------------------------------------------------------->
# PERMISSION statement
**Purpose:**
Give a certain permission to the program.

**Syntax:**
> PERMISSION *perm$*

**Remarks:**
*perm$* is a string describing the permission, as returned by the [PERMISSION$](#permission-function) function.

Android apps need to request permissions to do sensitive operations, like send and receive SMS, make phone call, access GPS, etc.
In basica the user must request each permission his program needs to exercise.
This is done thanks to the `PERMISSION` command. You can use as many `PERMISSION` commands as needed. Usually they are placed at the top of your program. See the list of permissions in the [PERMISSION$](#permission-function) function.

**See also:**
* [PERMISSION$](#permission-function)

**Examples:**
```vb
' No permission at all needed:
FOR i=1 TO 10
  PRINT i
NEXT
```

```vb
' Write to SD permission needed:
PERMISSION "write external storage"
OPEN "readme.txt" FOR TEXT WRITE AS #fileNum
PUT$ #fileNum, "Hello, world!"
CLOSE #fileNum
```

<!------------------------------------------------------------------------------->
# PERMISSION$ function
**Purpose:**
Return a permission string as to be used with the [PERMISSION](#permission-statement) statement.

**Syntax:**
> perm$ = PERMISSION$(*n*)

**Remarks:**
*n* starts at 1. If *n* is greater than the number of permissions basica has to offer, `PERMISSION$(n)` will return an empty string.

Here is the table of each permission and their meaning:

index | value | permission meaning
------|-------|-------------------
PERMISSION$(1) | "write external storage" | write to the Android device SD-Card

**See also:**
* [PERMISSION](#permission-statement)

<!------------------------------------------------------------------------------->
# Credits
The author would like to thank Paul Laughton who created RFO BASIC! that paved the way to basica.
The author would also like to thank jecelyin who created the 920 Editor V2 used in basica.
Finally, thanks to jMarc and the many contributors at the RFO BASIC! forum.
