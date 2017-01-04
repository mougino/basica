<!------------------------------------------------------------------------------->
# <a name="basica"></a>basica
basica is an editor + GUI composer + interpreter + compiler of the Basic language for Android devices.
It is based on RFO BASIC! with many improvements.

**KeyWord Quick Finder:**
[&#9398;](#a) [&#9399;](#b) [&#9400;](#c) [&#9401;](#d) [&#9402;](#e) [&#9403;](#f) [&#9404;](#g) [&#9405;](#h) [&#9406;](#i) [&#9407;](#j) [&#9408;](#k) [&#9409;](#l) [&#9410;](#m)
[&#9411;](#n) [&#9412;](#o) [&#9413;](#p) [&#9414;](#q) [&#9415;](#r) [&#9416;](#s) [&#9417;](#t) [&#9418;](#u) [&#9419;](#v) [&#9420;](#w) [&#9421;](#x) [&#9422;](#y) [&#9423;](#z)

**Dogmata:**

1. the syntax should be as close to other Basic dialects as possible
  * especially Visual Basic (VB6) and PowerBasic that both have a large coders base
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
* [Differences with RFO BASIC!](#differences)

<!------------------------------------------------------------------------------->
# <a name="summary"></a>Command summary
The following is a list of the commands built into basica and separated into 18 groups of related commands, which can assist with identifying the best command for the task at hand.  Some commands may appear in more than one group.

* [Array, List, Stack and Bundle](#array)
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
* [Sound Commands](#sound)
* [SQL Commands](#sql)
* [String Operations](#string)
* [Time Commands](#time)
* [Misc Operations](#misc)

**See also:**
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

**See also:**
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

## A
* [ABS](#abs)
* [ACOS](#acos)
* [AND](#and)
* [APP.BROADCAST](#appbroadcast)
* [APP.START](#appstart)
* [APPEND](#append)
* [ARRAY.AVERAGE](#arrayaverage)
* [ARRAY.COPY](#arraycopy)
* [ARRAY.DELETE](#arraydelete)
* [ARRAY.DIMS](#arraydims)
* [ARRAY.FILL](#arrayfill)
* [ARRAY.LEN](#arraylen)
* [ARRAY.LOAD](#arrayload)
* [ARRAY.MAX](#arraymax)
* [ARRAY.MIN](#arraymin)
* [ARRAY.REVERSE](#arrayreverse)
* [ARRAY.SEARCH](#arraysearch)
* [ARRAY.SHUFFLE](#arrayshuffle)
* [ARRAY.SORT](#arraysort)
* [ARRAY.STD_DEV](#arraystd_dev)
* [ARRAY.SUM](#arraysum)
* [ARRAY.VARIANCE](#arrayvariance)
* [ASCII](#ascii)
* [ASIN](#asin)
* [ATAN](#atan)
* [ATAN2](#atan2)
* [AUDIO.ISDONE](#audioisdone)
* [AUDIO.LENGTH](#audiolength)
* [AUDIO.LOAD](#audioload)
* [AUDIO.LOOP](#audioloop)
* [AUDIO.PAUSE](#audiopause)
* [AUDIO.PLAY](#audioplay)
* [AUDIO.POSITION.CURRENT](#audiopositioncurrent)
* [AUDIO.POSITION.SEEK](#audiopositionseek)
* [AUDIO.RECORD.START](#audiorecordstart)
* [AUDIO.RECORD.STOP](#audiorecordstop)
* [AUDIO.RELEASE](#audiorelease)
* [AUDIO.STOP](#audiostop)
* [AUDIO.VOLUME](#audiovolume)

## B
* [BACK.RESUME](#backresume)
* [BACKGROUND](#background)
* [BACKGROUND.RESUME](#backgroundresume)
* [BAND](#band)
* [BIN](#bin)
* [BIN$](#bin_)
* [BINARY](#binary)
* [BNOT](#bnot)
* [BOR](#bor)
* [BROWSE](#browse)
* [BT.CLOSE](#btclose)
* [BT.CONNECT](#btconnect)
* [BT.DEVICE.NAME](#btdevicename)
* [BT.DISCONNECT](#btdisconnect)
* [BT.ONREADREADY.RESUME](#btonreadreadyresume)
* [BT.OPEN](#btopen)
* [BT.READ.BYTES](#btreadbytes)
* [BT.READ.READY](#btreadready)
* [BT.RECONNECT](#btreconnect)
* [BT.SET.UUID](#btsetuuid)
* [BT.STATUS](#btstatus)
* [BT.WRITE](#btwrite)
* [BUNDLE.CLEAR](#bundleclear)
* [BUNDLE.CONTAIN](#bundlecontain)
* [BUNDLE.CREATE](#bundlecreate)
* [BUNDLE.GET](#bundleget)
* [BUNDLE.KEYS](#bundlekeys)
* [BUNDLE.PUT](#bundleput)
* [BUNDLE.REMOVE](#bundleremove)
* [BUNDLE.TYPE](#bundletype)
* [BXOR](#bxor)

## C
* [CALL](#call)
* [CBRT](#cbrt)
* [CEIL](#ceil)
* [CHR$](#chr_)
* [CLIPBOARD.GET](#clipboardget)
* [CLIPBOARD.PUT](#clipboardput)
* [CLOCK](#clock)
* [CLOSE](#close)
* [CLS](#cls)
* [CONSOLE.FRONT](#consolefront)
* [CONSOLE.LINE.COUNT](#consolelinecount)
* [CONSOLE.LINE.TEXT](#consolelinetext)
* [CONSOLE.LINE.TOUCHED](#consolelinetouched)
* [CONSOLE.SAVE](#consolesave)
* [CONSOLE.TITLE](#consoletitle)
* [CONSOLETOUCH.RESUME](#consoletouchresume)
* [COS](#cos)
* [COSH](#cosh)

## D
* [D_U.BREAK](#d_ubreak)
* [D_U.CONTINUE](#d_ucontinue)
* [DEBUG.DUMP.ARRAY](#debugdumparray)
* [DEBUG.DUMP.BUNDLE](#debugdumpbundle)
* [DEBUG.DUMP.LIST](#debugdumplist)
* [DEBUG.DUMP.SCALARS](#debugdumpscalars)
* [DEBUG.DUMP.STACK](#debugdumpstack)
* [DEBUG.ECHO.OFF](#debugechooff)
* [DEBUG.ECHO.ON](#debugechoon)
* [DEBUG.OFF](#debugoff)
* [DEBUG.ON](#debugon)
* [DEBUG.PRINT](#debugprint)
* [DEBUG.SHOW](#debugshow)
* [DEBUG.SHOW.ARRAY](#debugshowarray)
* [DEBUG.SHOW.BUNDLE](#debugshowbundle)
* [DEBUG.SHOW.LIST](#debugshowlist)
* [DEBUG.SHOW.PROGRAM](#debugshowprogram)
* [DEBUG.SHOW.SCALARS](#debugshowscalars)
* [DEBUG.SHOW.STACK](#debugshowstack)
* [DEBUG.SHOW.WATCH](#debugshowwatch)
* [DEBUG.WATCH](#debugwatch)
* [DECODE$](#decode_)
* [DECRYPT](#decrypt)
* [DEVICE](#device)
* [DEVICE.LANGUAGE](#devicelanguage)
* [DEVICE.LOCALE](#devicelocale)
* [DIALOG.MESSAGE](#dialogmessage)
* [DIALOG.SELECT](#dialogselect)
* [DIM](#dim)
* [DO](#do)

## E
* [ECHO.OFF](#echooff)
* [ECHO.ON](#echoon)
* [ELSE](#else)
* [EMAIL.SEND](#emailsend)
* [ENCODE$](#encode_)
* [ENCRYPT](#encrypt)
* [END](#end)
* [ENDS_WITH](#ends_with)
* [EOF](#eof)
* [EXIT](#exit)
* [EXP](#exp)

## F
* [F_N.BREAK](#f_nbreak)
* [F_N.CONTINUE](#f_ncontinue)
* [FILE.COPY](#filecopy)
* [FILE.DELETE](#filedelete)
* [FILE.DIR](#filedir)
* [FILE.EXISTS](#fileexists)
* [FILE.MKDIR](#filemkdir)
* [FILE.RENAME](#filerename)
* [FILE.ROOT](#fileroot)
* [FILE.SIZE](#filesize)
* [FILE.TYPE](#filetype)
* [FLOOR](#floor)
* [FONT.CLEAR](#fontclear)
* [FONT.DELETE](#fontdelete)
* [FONT.LOAD](#fontload)
* [FOR](#for)
* [FORMAT$](#format_)
* [FORMAT_USING$](#format_using_)
* [FRAC](#frac)
* [FTP.CD](#ftpcd)
* [FTP.CLOSE](#ftpclose)
* [FTP.DELETE](#ftpdelete)
* [FTP.DIR](#ftpdir)
* [FTP.GET](#ftpget)
* [FTP.MKDIR](#ftpmkdir)
* [FTP.OPEN](#ftpopen)
* [FTP.PUT](#ftpput)
* [FTP.RENAME](#ftprename)
* [FTP.RMDIR](#ftprmdir)
* [FUNCTION](#function)

## G
* [GETERROR$](#geterror_)
* [GOSUB](#gosub)
* [GOTO](#goto)
* [GPS.ACCURACY](#gpsaccuracy)
* [GPS.ALTITUDE](#gpsaltitude)
* [GPS.BEARING](#gpsbearing)
* [GPS.CLOSE](#gpsclose)
* [GPS.LATITUDE](#gpslatitude)
* [GPS.LOCATION](#gpslocation)
* [GPS.LONGITUDE](#gpslongitude)
* [GPS.OPEN](#gpsopen)
* [GPS.PROVIDER](#gpsprovider)
* [GPS.SATELLITES](#gpssatellites)
* [GPS.SPEED](#gpsspeed)
* [GPS.STATUS](#gpsstatus)
* [GPS.TIME](#gpstime)
* [GR.ARC](#grarc)
* [GR.BITMAP.CREATE](#grbitmapcreate)
* [GR.BITMAP.CROP](#grbitmapcrop)
* [GR.BITMAP.DELETE](#grbitmapdelete)
* [GR.BITMAP.DRAW](#grbitmapdraw)
* [GR.BITMAP.DRAWINTO.END](#grbitmapdrawintoend)
* [GR.BITMAP.DRAWINTO.START](#grbitmapdrawintostart)
* [GR.BITMAP.FILL](#grbitmapfill)
* [GR.BITMAP.LOAD](#grbitmapload)
* [GR.BITMAP.SAVE](#grbitmapsave)
* [GR.BITMAP.SCALE](#grbitmapscale)
* [GR.BITMAP.SIZE](#grbitmapsize)
* [GR.BOUNDED.TOUCH](#grboundedtouch)
* [GR.BOUNDED.TOUCH2](#grboundedtouch2)
* [GR.BRIGHTNESS](#grbrightness)
* [GR.CAMERA.AUTOSHOOT](#grcameraautoshoot)
* [GR.CAMERA.MANUALSHOOT](#grcameramanualshoot)
* [GR.CAMERA.SELECT](#grcameraselect)
* [GR.CAMERA.SHOOT](#grcamerashoot)
* [GR.CIRCLE](#grcircle)
* [GR.CLIP](#grclip)
* [GR.CLOSE](#grclose)
* [GR.CLS](#grcls)
* [GR.COLOR](#grcolor)
* [GR.FRONT](#grfront)
* [GR.GET.BMPIXEL](#grgetbmpixel)
* [GR.GET.PARAMS](#grgetparams)
* [GR.GET.PIXEL](#grgetpixel)
* [GR.GET.POSITION](#grgetposition)
* [GR.GET.TEXTBOUNDS](#grgettextbounds)
* [GR.GET.TYPE](#grgettype)
* [GR.GET.VALUE](#grgetvalue)
* [GR.GETDL](#grgetdl)
* [GR.GROUP](#grgroup)
* [GR.GROUP.GETDL](#grgroupgetdl)
* [GR.GROUP.LIST](#grgrouplist)
* [GR.GROUP.NEWDL](#grgroupnewdl)
* [GR.HIDE](#grhide)
* [GR.LINE](#grline)
* [GR.MODIFY](#grmodify)
* [GR.MOVE](#grmove)
* [GR.NEWDL](#grnewdl)
* [GR.ONGRTOUCH.RESUME](#grongrtouchresume)
* [GR.OPEN](#gropen)
* [GR.ORIENTATION](#grorientation)
* [GR.OVAL](#groval)
* [GR.PAINT.COPY](#grpaintcopy)
* [GR.PAINT.GET](#grpaintget)
* [GR.PAINT.RESET](#grpaintreset)
* [GR.POINT](#grpoint)
* [GR.POLY](#grpoly)
* [GR.RECT](#grrect)
* [GR.RENDER](#grrender)
* [GR.ROTATE.END](#grrotateend)
* [GR.ROTATE.START](#grrotatestart)
* [GR.SAVE](#grsave)
* [GR.SCALE](#grscale)
* [GR.SCREEN](#grscreen)
* [GR.SCREEN.TO_BITMAP](#grscreento_bitmap)
* [GR.SET.ANTIALIAS](#grsetantialias)
* [GR.SET.PIXELS](#grsetpixels)
* [GR.SET.STROKE](#grsetstroke)
* [GR.SHOW](#grshow)
* [GR.SHOW.TOGGLE](#grshowtoggle)
* [GR.STATUSBAR](#grstatusbar)
* [GR.STATUSBAR.SHOW](#grstatusbarshow)
* [GR.TEXT.ALIGN](#grtextalign)
* [GR.TEXT.BOLD](#grtextbold)
* [GR.TEXT.DRAW](#grtextdraw)
* [GR.TEXT.HEIGHT](#grtextheight)
* [GR.TEXT.SETFONT](#grtextsetfont)
* [GR.TEXT.SIZE](#grtextsize)
* [GR.TEXT.SKEW](#grtextskew)
* [GR.TEXT.STRIKE](#grtextstrike)
* [GR.TEXT.TYPEFACE](#grtexttypeface)
* [GR.TEXT.UNDERLINE](#grtextunderline)
* [GR.TEXT.WIDTH](#grtextwidth)
* [GR.TOUCH](#grtouch)
* [GR.TOUCH2](#grtouch2)
* [GR_COLLISION](#gr_collision)
* [GRABFILE](#grabfile)
* [GRABURL](#graburl)

## H
* [HEADSET](#headset)
* [HEX](#hex)
* [HEX$](#hex_)
* [HOME](#home)
* [HTML.CLEAR.CACHE](#htmlclearcache)
* [HTML.CLEAR.HISTORY](#htmlclearhistory)
* [HTML.CLOSE](#htmlclose)
* [HTML.GET.DATALINK](#htmlgetdatalink)
* [HTML.GO.BACK](#htmlgoback)
* [HTML.GO.FORWARD](#htmlgoforward)
* [HTML.LOAD.STRING](#htmlloadstring)
* [HTML.LOAD.URL](#htmlloadurl)
* [HTML.OPEN](#htmlopen)
* [HTML.ORIENTATION](#htmlorientation)
* [HTML.POST](#htmlpost)
* [HTTP.POST](#httppost)
* [HYPOT](#hypot)

## I
* [IF](#if)
* [INCLUDE](#include)
* [INKEY$](#inkey_)
* [INPUT](#input)
* [INPUT.LINE](#inputline)
* [INPUT.TEXT](#inputtext)
* [INSTR](#instr)
* [INT](#int)
* [INT$](#int_)
* [IS_IN](#is_in)
* [IS_NUMBER](#is_number)

## J
* [JOIN](#join)
* [JOIN.ALL](#joinall)

## K
* [KB.HIDE](#kbhide)
* [KB.RESUME](#kbresume)
* [KB.SHOW](#kbshow)
* [KB.SHOWING](#kbshowing)
* [KB.TOGGLE](#kbtoggle)
* [KEY.RESUME](#keyresume)

## L
* [LCASE$](#lcase_)
* [LEFT$](#left_)
* [LEN](#len)
* [LET](#let)
* [LINE INPUT](#lineinput)
* [LIST.ADD](#listadd)
* [LIST.ADD.ARRAY](#listaddarray)
* [LIST.ADD.LIST](#listaddlist)
* [LIST.CLEAR](#listclear)
* [LIST.CREATE](#listcreate)
* [LIST.GET](#listget)
* [LIST.INSERT](#listinsert)
* [LIST.REMOVE](#listremove)
* [LIST.REPLACE](#listreplace)
* [LIST.SEARCH](#listsearch)
* [LIST.LEN](#listlen)
* [LIST.TOARRAY](#listtoarray)
* [LIST.TYPE](#listtype)
* [LOG](#log)
* [LOG10](#log10)
* [LOWMEMORY.RESUME](#lowmemoryresume)
* [LTRIM$](#ltrim_)

## M
* [MAX](#max)
* [MENUKEY.RESUME](#menukeyresume)
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
* [PHONE.CALL](#phonecall)
* [PHONE.DIAL](#phonedial)
* [PHONE.INFO](#phoneinfo)
* [PHONE.RCV.INIT](#phonercvinit)
* [PHONE.RCV.NEXT](#phonercvnext)
* [PI](#pi)
* [POPUP](#popup)
* [POW](#pow)
* [PRINT](#print)
* [PROGRAM.INFO](#programinfo)

## R
* [RANDOMIZE](#randomize)
* [READ](#read)
* [READ$](#read_)
* [READ.DATA](#readdata)
* [READ.FROM](#readfrom)
* [READ.NEXT](#readnext)
* [REM](#rem)
* [REPEAT$](#repeat_)
* [REPLACE$](#replace_)
* [RETURN](#return)
* [RIGHT$](#right_)
* [RINGER.GET.MODE](#ringergetmode)
* [RINGER.GET.VOLUME](#ringergetvolume)
* [RINGER.SET.MODE](#ringersetmode)
* [RINGER.SET.VOLUME](#ringersetvolume)
* [RND](#rnd)
* [ROUND](#round)
* [RTRIM$](#rtrim_)
* [RUN](#run)

## S
* [SCREEN](#screen)
* [SCREEN.ROTATION](#screenrotation)
* [SCREEN.SIZE](#screensize)
* [SELECT](#select)
* [SENSORS.CLOSE](#sensorsclose)
* [SENSORS.LIST](#sensorslist)
* [SENSORS.OPEN](#sensorsopen)
* [SENSORS.READ](#sensorsread)
* [SETBOF](#setbof)
* [SETEOF](#seteof)
* [SETSOF](#setsof)
* [SGN](#sgn)
* [SHIFT](#shift)
* [SIN](#sin)
* [SINH](#sinh)
* [SLEEP](#sleep)
* [SMS.RCV.INIT](#smsrcvinit)
* [SMS.RCV.NEXT](#smsrcvnext)
* [SMS.SEND](#smssend)
* [SOCKET.CLIENT.CLOSE](#socketclientclose)
* [SOCKET.CLIENT.CONNECT](#socketclientconnect)
* [SOCKET.CLIENT.READ.FILE](#socketclientreadfile)
* [SOCKET.CLIENT.READ.LINE](#socketclientreadline)
* [SOCKET.CLIENT.READ.READY](#socketclientreadready)
* [SOCKET.CLIENT.SERVER.IP](#socketclientserverip)
* [SOCKET.CLIENT.STATUS](#socketclientstatus)
* [SOCKET.CLIENT.WRITE.BYTES](#socketclientwritebytes)
* [SOCKET.CLIENT.WRITE.FILE](#socketclientwritefile)
* [SOCKET.CLIENT.WRITE.LINE](#socketclientwriteline)
* [SOCKET.MYIP](#socketmyip)
* [SOCKET.SERVER.CLIENT.IP](#socketserverclientip)
* [SOCKET.SERVER.CLOSE](#socketserverclose)
* [SOCKET.SERVER.CONNECT](#socketserverconnect)
* [SOCKET.SERVER.CREATE](#socketservercreate)
* [SOCKET.SERVER.DISCONNECT](#socketserverdisconnect)
* [SOCKET.SERVER.READ.FILE](#socketserverreadfile)
* [SOCKET.SERVER.READ.LINE](#socketserverreadline)
* [SOCKET.SERVER.READ.READY](#socketserverreadready)
* [SOCKET.SERVER.STATUS](#socketserverstatus)
* [SOCKET.SERVER.WRITE.BYTES](#socketserverwritebytes)
* [SOCKET.SERVER.WRITE.FILE](#socketserverwritefile)
* [SOCKET.SERVER.WRITE.LINE](#socketserverwriteline)
* [SOUNDPOOL.LOAD](#soundpoolload)
* [SOUNDPOOL.OPEN](#soundpoolopen)
* [SOUNDPOOL.PAUSE](#soundpoolpause)
* [SOUNDPOOL.PLAY](#soundpoolplay)
* [SOUNDPOOL.RELEASE](#soundpoolrelease)
* [SOUNDPOOL.RESUME](#soundpoolresume)
* [SOUNDPOOL.SETPRIORITY](#soundpoolsetpriority)
* [SOUNDPOOL.SETRATE](#soundpoolsetrate)
* [SOUNDPOOL.SETVOLUME](#soundpoolsetvolume)
* [SOUNDPOOL.STOP](#soundpoolstop)
* [SOUNDPOOL.UNLOAD](#soundpoolunload)
* [SPLIT](#split)
* [SPLIT.ALL](#splitall)
* [SQL.CLOSE](#sqlclose)
* [SQL.DELETE](#sqldelete)
* [SQL.DROP_TABLE](#sqldrop_table)
* [SQL.EXEC](#sqlexec)
* [SQL.INSERT](#sqlinsert)
* [SQL.NEW_TABLE](#sqlnew_table)
* [SQL.NEXT](#sqlnext)
* [SQL.OPEN](#sqlopen)
* [SQL.QUERY](#sqlquery)
* [SQL.QUERY.LENGTH](#sqlquerylength)
* [SQL.QUERY.POSITION](#sqlqueryposition)
* [SQL.RAW_QUERY](#sqlraw_query)
* [SQL.UPDATE](#sqlupdate)
* [SQR](#sqr)
* [STACK.CLEAR](#stackclear)
* [STACK.CREATE](#stackcreate)
* [STACK.ISEMPTY](#stackisempty)
* [STACK.PEEK](#stackpeek)
* [STACK.POP](#stackpop)
* [STACK.PUSH](#stackpush)
* [STACK.TYPE](#stacktype)
* [STARTS_WITH](#starts_with)
* [STR$](#str_)
* [STT.LISTEN](#sttlisten)
* [STT.RESULTS](#sttresults)
* [SU.CLOSE](#suclose)
* [SU.OPEN](#suopen)
* [SU.READ.LINE](#sureadline)
* [SU.READ.READY](#sureadready)
* [SU.WRITE](#suwrite)
* [SUB](#sub)
* [SW.BEGIN](#swbegin)
* [SW.BREAK](#swbreak)
* [SW.CASE](#swcase)
* [SW.DEFAULT](#swdefault)
* [SW.END](#swend)
* [SWAP](#swap)
* [SYSTEM.CLOSE](#systemclose)
* [SYSTEM.OPEN](#systemopen)
* [SYSTEM.READ.LINE](#systemreadline)
* [SYSTEM.READ.READY](#systemreadready)
* [SYSTEM.WRITE](#systemwrite)

## T
* [TALLY](#tally)
* [TAN](#tan)
* [TEXT](#text)
* [THEN](#then)
* [TIME](#time)
* [TIMER.CLEAR](#timerclear)
* [TIMER.RESUME](#timerresume)
* [TIMER.SET](#timerset)
* [TIMEZONE.GET](#timezoneget)
* [TIMEZONE.LIST](#timezonelist)
* [TIMEZONE.SET](#timezoneset)
* [TODEGREES](#todegrees)
* [TONE](#tone)
* [TORADIANS](#toradians)
* [TRIM$](#trim_)
* [TTS.INIT](#ttsinit)
* [TTS.SPEAK](#ttsspeak)
* [TTS.SPEAK.TOFILE](#ttsspeaktofile)
* [TTS.STOP](#ttsstop)

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
* [VOLKEYS.OFF](#volkeysoff)
* [VOLKEYS.ON](#volkeyson)

## W
* [W_R.BREAK](#w_rbreak)
* [W_R.CONTINUE](#w_rcontinue)
* [WAKELOCK](#wakelock)
* [WHILE](#while)
* [WIFI.INFO](#wifiinfo)
* [WIFILOCK](#wifilock)
* [WORD$](#word_)
* [WRITE](#write)
* [WRITE$](#write_)

## Z
* [ZCOUNT](#zcount)
* [ZDIR](#dir)
* [ZREAD](#zread)
* [ZWRITE](#zwrite)

**See also:**
* [Command summary](#summary)
* [Format and typefaces](#format)

<!------------------------------------------------------------------------------->
# <a name="differences"></a>Differences with RFO BASIC!
basica is based on the excellent RFO BASIC! for Android, with the goal to remove much of its inconsistencies, and also rename or refactor some commands to follow basica's [dogmata](#basica) (especially dogma 1 and dogma 2).

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
FN.DEF | FUNCTION funcName{$} ( {param1{$}} {,param2{$}} ... ) or SUB subName ( {param1{$}} {,param2{$}} ... )
FN.END | END FUNCTION or END SUB
FN.RTN num&#124;string$ | RETURN {num&#124;string$}
GR_COLISION | GR.COLISION grObjId1, grObjId2, collision
LOWER$ | LCASE$
UPPER$ | UCASE$
TGET | INPUT
INPUT | INPUT.LINE
INPUT.TEXT | INPUT.TEXT

# Additions
* INSTR
* FILE.COPY
* LOF, SETBOF/SETSOF and SETEOF
* PERMISSION and PERMISSION$
* PARSECOUNT, PARSE$ and TALLY
* REDIM and REDIM PRESERVE

Back to [basica](#basica)

<!------------------------------------------------------------------------------->
# <a name="array"></a>Array, List, Stack and Bundle
The following functions can be used to manipulate and manage arrays:
* [ARRAY.AVERAGE](#arrayaverage)
* [ARRAY.COPY](#arraycopy)
* [ARRAY.DELETE](#arraydelete)
* [ARRAY.DIMS](#arraydims)
* [ARRAY.FILL](#arrayfill)
* [ARRAY.LEN](#arraylen)
* [ARRAY.LOAD](#arrayload)
* [ARRAY.MAX](#arraymax)
* [ARRAY.MIN](#arraymin)
* [ARRAY.REVERSE](#arrayreverse)
* [ARRAY.SEARCH](#arraysearch)
* [ARRAY.SHUFFLE](#arrayshuffle)
* [ARRAY.SORT](#arraysort)
* [ARRAY.STD_DEV](#arraystd_dev)
* [ARRAY.SUM](#arraysum)
* [ARRAY.VARIANCE](#arrayvariance)
* [DEBUG.DUMP.ARRAY](#debugdumparray)
* [DEBUG.SHOW.ARRAY](#debugshowarray)
* [DIM](#dim)
* [JOIN](#join)
* [JOIN.ALL](#joinall)
* [LIST.ADD.ARRAY](#listaddarray)
* [LIST.TOARRAY](#listtoarray)
* [REDIM](#redim)
* [UNDIM](#undim)

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="communication"></a>Communication Control
The following functions can be used for external communications:
* [Bluetooth Commands](#bluetooth)
* [EMAIL.SEND](#emailsend)
* [FTP Commands](#ftp)
* [GRABURL](#graburl)
* [HTTP.POST](#httppost)
* [PHONE.CALL](#phonecall)
* [PHONE.DIAL](#phonedial)
* [PHONE.RCV.INIT](#phonercvinit)
* [PHONE.RCV.NEXT](#phonercvnext)
* [SMS.RCV.INIT](#smsrcvinit)
* [SMS.RCV.NEXT](#smsrcvnext)
* [SMS.SEND](#smssend)
* [Socket (TCP/IP) Commands](#socket)
* [WIFI.INFO](#wifiinfo)
* [WIFILOCK](#wifilock)

Back to [Command summary](#command)

# <a name="bluetooth"></a>Bluetooth Commands
The following commands can be used to communicate with a device by bluetooth:
* [BT.CLOSE](#btclose)
* [BT.CONNECT](#btconnect)
* [BT.DEVICE.NAME](#btdevicename)
* [BT.DISCONNECT](#btdisconnect)
* [BT.ONREADREADY.RESUME](#btonreadreadyresume)
* [BT.OPEN](#btopen)
* [BT.READ.BYTES](#btreadbytes)
* [BT.READ.READY](#btreadready)
* [BT.RECONNECT](#btreconnect)
* [BT.SET.UUID](#btsetuuid)
* [BT.STATUS](#btstatus)
* [BT.WRITE](#btwrite)
* [ONBTREADREADY](#onbtreadready)

Back to [Communication Control](#communication)

# <a name="ftp"></a>FTP Commands
The following commands can be used to operate the File Transfer Protocol (FTP):
* [FTP.CD](#ftpcd)
* [FTP.CLOSE](#ftpclose)
* [FTP.DELETE](#ftpdelete)
* [FTP.DIR](#ftpdir)
* [FTP.GET](#ftpget)
* [FTP.MKDIR](#ftpmkdir)
* [FTP.OPEN](#ftpopen)
* [FTP.PUT](#ftpput)
* [FTP.RENAME](#ftprename)
* [FTP.RMDIR](#ftprmdir)

Back to [Communication Control](#communication)

# <a name="socket"></a>Socket (TCP/IP) Commands
The following commands can be used to handle TCP/IP sockets:
* [SOCKET.CLIENT.CLOSE](#socketclientclose)
* [SOCKET.CLIENT.CONNECT](#socketclientconnect)
* [SOCKET.CLIENT.READ.FILE](#socketclientreadfile)
* [SOCKET.CLIENT.READ.LINE](#socketclientreadline)
* [SOCKET.CLIENT.READ.READY](#socketclientreadready)
* [SOCKET.CLIENT.SERVER.IP](#socketclientserverip)
* [SOCKET.CLIENT.STATUS](#socketclientstatus)
* [SOCKET.CLIENT.WRITE.BYTES](#socketclientwritebytes)
* [SOCKET.CLIENT.WRITE.FILE](#socketclientwritefile)
* [SOCKET.CLIENT.WRITE.LINE](#socketclientwriteline)
* [SOCKET.MYIP](#socketmyip)
* [SOCKET.SERVER.CLIENT.IP](#socketserverclientip)
* [SOCKET.SERVER.CLOSE](#socketserverclose)
* [SOCKET.SERVER.CONNECT](#socketserverconnect)
* [SOCKET.SERVER.CREATE](#socketservercreate)
* [SOCKET.SERVER.DISCONNECT](#socketserverdisconnect)
* [SOCKET.SERVER.READ.FILE](#socketserverreadfile)
* [SOCKET.SERVER.READ.LINE](#socketserverreadline)
* [SOCKET.SERVER.READ.READY](#socketserverreadready)
* [SOCKET.SERVER.STATUS](#socketserverstatus)
* [SOCKET.SERVER.WRITE.BYTES](#socketserverwritebytes)
* [SOCKET.SERVER.WRITE.FILE](#socketserverwritefile)
* [SOCKET.SERVER.WRITE.LINE](#socketserverwriteline)

Back to [Communication Control](#communication)

<!------------------------------------------------------------------------------->
# <a name="compiler"></a>Compiler Operations
The following functions manipulate the compiler's operation:

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="console"></a>Console Commands

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="debugging"></a>Debugging and Error Control

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="file"></a>File Commands

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="flow"></a>Flow Control

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="graphic"></a>Graphic Commands

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="html"></a>Html Commands

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="input"></a>Input Commands

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="memory"></a>Memory Management
* [AUDIO.LOAD](#audioload)
* [AUDIO.RELEASE](#audiorelease)
* [BUNDLE.CLEAR](#bundleclear)
* [BUNDLE.CREATE](#bundlecreate)
* [DIM](#dim)
* [FONT.CLEAR](#fontclear)
* [FONT.DELETE](#fontdelete)
* [FONT.LOAD](#fontload)
* [GR.BITMAP.CREATE](#grbitmapcreate)
* [GR.BITMAP.CROP](#grbitmapcrop)
* [GR.BITMAP.DELETE](#grbitmapdelete)
* [GR.BITMAP.LOAD](#grbitmapload)
* [GR.BITMAP.SCALE](#grbitmapscale)
* [LIST.CLEAR](#listclear)
* [LIST.CREATE](#listcreate)
* [LOWMEMORY.RESUME](#lowmemoryresume)
* [ONLOWMEMORY](#onlowmemory)
* [REDIM](#redim)
* [SOUNDPOOL.LOAD](#soundpoolload)
* [SOUNDPOOL.RELEASE](#soundpoolrelease)
* [SOUNDPOOL.UNLOAD](#soundpoolunload)
* [STACK.CLEAR](#stackclear)
* [STACK.CREATE](#stackcreate)
* [UNDIM](#undim)

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="numeric"></a>Numeric Operations

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="operating"></a>Operating System

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="sound"></a>Sound Commands

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="sql"></a>SQL Commands

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="string"></a>String Operations

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="time"></a>Time Commands

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="misc"></a>Misc Operations

Back to [Command summary](#command)

<!------------------------------------------------------------------------------->
# <a name="permission"></a>PERMISSION statement
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
OPEN "readme.txt" FOR TEXT WRITE AS fileNum
WRITE fileNum, "Hello, world!"
CLOSE fileNum
```

**See also:**
* [PERMISSION$](#permission_)

<!------------------------------------------------------------------------------->
# <a name="permission_"></a>PERMISSION$ function
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
# <a name="credits"></a>Credits
The author would like to thank Paul Laughton who created RFO BASIC! that paved the way to basica.
The author would also like to thank jecelyin who created the 920 Editor V2 used in basica.
Finally, thanks to jMarc and the many contributors at the RFO BASIC! forum.
