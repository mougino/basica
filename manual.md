<!------------------------------------------------------------------------------->
# basica
basica is an editor + GUI composer + interpreter + compiler of the Basic language for Android devices.
It is based on RFO BASIC! with many improvements.

**KeyWord Quick Finder:**
[&#9398;](#a) [&#9399;](#b) [&#9400;](#c) [&#9401;](#d) [&#9402;](#e) [&#9403;](#f) [&#9404;](#g) [&#9405;](#h) [&#9406;](#i) [&#9407;](#j) [&#9408;](#k) [&#9409;](#l) [&#9410;](#m)
[&#9411;](#n) [&#9412;](#o) [&#9413;](#p) [&#9414;](#q) [&#9415;](#r) [&#9416;](#s) [&#9417;](#t) [&#9418;](#u) [&#9419;](#v) [&#9420;](#w) [&#9421;](#x) [&#9422;](#y) [&#9423;](#z)

## Dogmata

1. the syntax should be as close to other Basic dialects as possible
  * especially Visual Basic (VB6) PowerBasic and FreeBasic, that have a large coders base
2. the command names should indicate as much as possible the order of the parameters:
  * e.g. `GR.TEXT.DRAW grObjId, text$, drawX, drawY ' GR->grObjId ; TEXT->text$ ; DRAW->draw coordinates`
  * e.g. `FILE.SIZE file$, size` or `FILE.EXISTS file$, exists`
  * e.g. `ARRAY.LEN arr[], len` or `LIST.LEN listId, len`
  * e.g. `IS_IN(sub$, main$) ' "IS sub$ IN main$?"` (IS_IN is a refactor of INSTR, which also remains available)
3. indices and failure codes should always be consistent
 * i.e. indices always start at 1 (array dim, lists, etc.)
 * and failure code is always 0 (e.g. cannot open a file, load a resource, etc.)
4. the power (and the responsibility) of basica should be given to the user at all time (when pressing Run or Compile):
  * sensitive commands need a `PERMISSION` statement in order to work
  * resources must be called with their exact filename case ("myPic.JPG" <> "Mypic.jpg")
5. the editor should be as intuitive and powerful as a source code editor can be:
 * multi tab
 * syntax highlighting
 * built-in manual / keyword reference with quick access to contextual help
 * bottom panel for tips and Run/Compile log
6. basica should be *maintained*: there should be no more than 3 months between official releases

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
* [APPEND](#append)
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
* [BIN](#bin)
* [BIN$](#bin_)
* [BINARY](#binary)
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
* [CHR$](#chr_)
* [CLIPBOARD.GET](#clipboard-get)
* [CLIPBOARD.PUT](#clipboard-put)
* [CLOCK](#clock)
* [CLOSE](#close)
* [CLS](#cls)
* [CONSOLE.FRONT](#console-front)
* [CONSOLE.LINE.COUNT](#console-line-count)
* [CONSOLE.LINE.TEXT](#console-line-text)
* [CONSOLE.LINE.TOUCHED](#console-line-touched)
* [CONSOLE.SAVE](#console-save)
* [CONSOLE.TITLE](#console-title)
* [CONSOLETOUCH.RESUME](#consoletouch-resume)
* [COS](#cos)
* [COSH](#cosh)

## D
* [D_U.BREAK](#d-u-break)
* [D_U.CONTINUE](#d-u-continue)
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
* [DECODE$](#decode_)
* [DECRYPT](#decrypt)
* [DEVICE](#device)
* [DEVICE.LANGUAGE](#device-language)
* [DEVICE.LOCALE](#device-locale)
* [DIALOG.MESSAGE](#dialog-message)
* [DIALOG.SELECT](#dialog-select)
* [DIM](#dim)
* [DO](#do)

## E
* [ECHO.OFF](#echo-off)
* [ECHO.ON](#echo-on)
* [ELSE](#else)
* [EMAIL.SEND](#email-send)
* [ENCODE$](#encode_)
* [ENCRYPT](#encrypt)
* [END](#end)
* [ENDS_WITH](#ends-with)
* [EOF](#eof)
* [EXIT](#exit)
* [EXP](#exp)

## F
* [F_N.BREAK](#f-n-break)
* [F_N.CONTINUE](#f-n-continue)
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
* [FORMAT$](#format_)
* [FORMAT_USING$](#format-using_)
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
* [GETERROR$](#geterror_)
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
* [HEX$](#hex_)
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
* [INKEY$](#inkey_)
* [INPUT](#input)
* [INPUT.LINE](#input-line)
* [INPUT.TEXT](#input-text)
* [INSTR](#instr)
* [INT](#int)
* [INT$](#int_)
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

## L
* [LCASE$](#lcase_)
* [LEFT$](#left_)
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
* [LTRIM$](#ltrim_)

## M
* [MAX](#max)
* [MENUKEY.RESUME](#menukey-resume)
* [MID$](#mid_)
* [MIN](#min)
* [MKDIR](#mkdir)
* [MOD](#mod)
* [MYPHONENUMBER](#myphonenumber)

## N
* [NEXT](#next)
* [NOT](#not)
* [NOTIFY](#notify)

## O
* [OCT](#oct)
* [OCT$](#oct_)
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
* [OPEN](#open)
* [OR](#or)

## P
* [PARSE$](#parse_)
* [PARSECOUNT](#parsecount)
* [PERMISSION](#permission)
* [PERMISSION$](#permission_)
* [PHONE.CALL](#phone-call)
* [PHONE.DIAL](#phone-dial)
* [PHONE.INFO](#phone-info)
* [PHONE.RCV.INIT](#phone-rcv-init)
* [PHONE.RCV.NEXT](#phone-rcv-next)
* [PI](#pi)
* [POPUP](#popup)
* [POW](#pow)
* [PRINT](#print)
* [PROGRAM.INFO](#program-info)

## R
* [RANDOMIZE](#randomize)
* [READ](#read)
* [READ$](#read_)
* [READ.DATA](#read-data)
* [READ.FROM](#read-from)
* [READ.NEXT](#read-next)
* [REM](#rem)
* [REPEAT$](#repeat_)
* [REPLACE$](#replace_)
* [RETURN](#return)
* [RIGHT$](#right_)
* [RINGER.GET.MODE](#ringer-get-mode)
* [RINGER.GET.VOLUME](#ringer-get-volume)
* [RINGER.SET.MODE](#ringer-set-mode)
* [RINGER.SET.VOLUME](#ringer-set-volume)
* [RND](#rnd)
* [ROUND](#round)
* [RTRIM$](#rtrim_)
* [RUN](#run)

## S
* [SCREEN](#screen)
* [SCREEN.ROTATION](#screen-rotation)
* [SCREEN.SIZE](#screen-size)
* [SELECT](#select)
* [SENSORS.CLOSE](#sensors-close)
* [SENSORS.LIST](#sensors-list)
* [SENSORS.OPEN](#sensors-open)
* [SENSORS.READ](#sensors-read)
* [SETBOF](#setbof)
* [SETEOF](#seteof)
* [SETSOF](#setsof)
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
* [STR$](#str_)
* [STT.LISTEN](#stt-listen)
* [STT.RESULTS](#stt-results)
* [SU.CLOSE](#su-close)
* [SU.OPEN](#su-open)
* [SU.READ.LINE](#su-read-line)
* [SU.READ.READY](#su-read-ready)
* [SU.WRITE](#su-write)
* [SUB](#sub)
* [SW.BEGIN](#sw-begin)
* [SW.BREAK](#sw-break)
* [SW.CASE](#sw-case)
* [SW.DEFAULT](#sw-default)
* [SW.END](#sw-end)
* [SWAP](#swap)
* [SYSTEM.CLOSE](#system-close)
* [SYSTEM.OPEN](#system-open)
* [SYSTEM.READ.LINE](#system-read-line)
* [SYSTEM.READ.READY](#system-read-ready)
* [SYSTEM.WRITE](#system-write)

## T
* [TALLY](#tally)
* [TAN](#tan)
* [TEXT](#text)
* [THEN](#then)
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
* [TRIM$](#trim_)
* [TTS.INIT](#tts-init)
* [TTS.SPEAK](#tts-speak)
* [TTS.SPEAK.TOFILE](#tts-speak-tofile)
* [TTS.STOP](#tts-stop)

## U
* [UCASE$](#ucase_)
* [UCODE](#ucode)
* [UNDIM](#undim)
* [UNTIL](#until)
* [USING$](#using_)

## V
* [VAL](#val)
* [VERSION$](#version_)
* [VIBRATE](#vibrate)
* [VOLKEYS.OFF](#volkeys-off)
* [VOLKEYS.ON](#volkeys-on)

## W
* [W_R.BREAK](#w-r-break)
* [W_R.CONTINUE](#w-r-continue)
* [WAKELOCK](#wakelock)
* [WHILE](#while)
* [WIFI.INFO](#wifi-info)
* [WIFILOCK](#wifilock)
* [WORD$](#word_)
* [WRITE](#write)
* [WRITE$](#write_)

## Z
* [ZCOUNT](#zcount)
* [ZDIR](#zdir)
* [ZREAD](#zread)
* [ZWRITE](#zwrite)

**See also:**
* [Command summary](#command-summary)
* [Format and typefaces](#format-and-typefaces)

<!------------------------------------------------------------------------------->
# Differences with RFO BASIC!
basica is based on the excellent RFO BASIC! for Android, with the goal to remove much of its inconsistencies, and also rename or refactor some commands to follow basica's [dogmata](#dogmata) (especially dogma 1 and dogma 2).

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
ZIP.DIR *zip$*, *entries[]* | ZDIR *zip$*, *entries[]*
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
PAUSE | SLEEP
FN.DEF | SUB&#124;FUNCTION funcName{$} ( {param1{$}} {,param2{$}} ... )
FN.END | END SUB&#124;FUNCTION
FN.RTN num&#124;string$ | RETURN {num&#124;string$}
GR_COLISION | GR.COLISION grObjId1, grObjId2, collision
LOWER$ | LCASE$
UPPER$ | UCASE$
TGET | INPUT
INPUT | INPUT.LINE
TEXT.INPUT | INPUT.TEXT

# Additions
* INSTR
* FILE.COPY
* LOF, SETBOF/SETSOF and SETEOF
* PERMISSION and PERMISSION$
* PARSECOUNT, PARSE$ and TALLY
* REDIM and REDIM PRESERVE

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
# BIN

<!------------------------------------------------------------------------------->
# BIN$

<!------------------------------------------------------------------------------->
# PERMISSION statement
**Purpose:**
Give a certain permission to the program.

**Syntax:**
> PERMISSION *perm$*

**Remarks:**
*perm$* is a string describing the permission, as returned by the [PERMISSION$](#permission_) function.

Android apps need to request permissions to do sensitive operations, like send and receive SMS, make phone call, access GPS, etc.
In basica the user must request each permission his program needs to exercise.
This is done thanks to the `PERMISSION` command. You can use as many `PERMISSION` commands as needed. Usually they are placed at the top of your program. See the list of permissions in the [PERMISSION$](#permission_) function.

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

**See also:**
* [PERMISSION$](#permission_)

<!------------------------------------------------------------------------------->
# PERMISSION$ function
**Purpose:**
Return a permission string as to be used with the [PERMISSION](#permission) statement.

**Syntax:**
> perm$ = PERMISSION$(*n*)

**Remarks:**
*n* starts at 1. If *n* is greater than the number of permissions basica has to offer, `PERMISSION$(n)` will return an empty string.

Here is the table of each permission and their meaning:

index | value | permission meaning
------|-------|-------------------
PERMISSION$(1) | "write external storage" | write to the Android device SD-Card

**See also:**
* [PERMISSION](#permission)

<!------------------------------------------------------------------------------->
# Credits
The author would like to thank Paul Laughton who created RFO BASIC! that paved the way to basica.
The author would also like to thank jecelyin who created the 920 Editor V2 used in basica.
Finally, thanks to jMarc and the many contributors at the RFO BASIC! forum.

