<!------------------------------------------------------------------------------->
# basica
basica is an editor + GUI composer + interpreter + compiler of the Basic language for Android devices.
It is based on RFO BASIC! with many improvements.

**KeyWord Quick Finder:**
[&#9398;](#a) [&#9399;](#b) [&#9400;](#c) [&#9401;](#d) [&#9402;](#e) [&#9403;](#f) [&#9404;](#g) [&#9405;](#h) [&#9406;](#i) [&#9407;](#j) [&#9408;](#k) [&#9409;](#l) [&#9410;](#m) [&#9411;](#n) [&#9412;](#o) [&#9413;](#p) [&#9415;](#r) [&#9416;](#s) [&#9417;](#t) [&#9418;](#u) [&#9419;](#v) [&#9420;](#w) [&#9423;](#z)

## Dogmata

1. the syntax should be as close to other BASIC dialects as possible
  * especially Visual Basic (VB6) PowerBasic and FreeBasic, which have a large coders base
  * e.g. usual comment character `'`, usual line continuation character `_`
  * e.g. usual binary operators `AND`, `OR`, `NOT`
  * e.g. usual typical commands like `OPEN file$ FOR Mode Access AS #fileNum`
2. the command names should always indicate the order of the parameters
  * e.g. `GR.TEXT.DRAW grObjId, text$, drawX, drawY ' GR->grObjId ; TEXT->text$ ; DRAW->draw coordinates`
  * e.g. `FILE.SIZE file$, size` or `FILE.EXISTS file$, exists`
  * e.g. `ARRAY.LEN arr[], len` or `LIST.LEN listId, len`
  * e.g. `IS_IN(sub$, main$) ' "IS sub$ IN main$ ?"` ([IS_IN](#is_in-function) is a refactor of [INSTR](#instr-function), which also remains available)
3. all interrupt labels and their corresponding resume commands should be consistant
 * e.g. `ON.BACKKEY`/`BACKKEY.RESUME`, `ON.BTREADREADY`/`BTREADREADY.RESUME`
 * e.g. `ON.GRTOUCH`/`GRTOUCH.RESUME`, `ON.KEYPRESS`/`KEYPRESS.RESUME`
4. indices and failure codes should always be consistent
 * i.e. indices always start at 1 (array dim, list id, obj id, etc.)
 * and failure code is always 0 (e.g. cannot open a file, load a resource, etc.)
5. the power (and the responsibility) of basica should be given to the user at all time (when pressing Run or Compile):
  * sensitive commands need a `PERMISSION` statement in order to work
  * resources must be placed in a specific folder, see [Working with resources](#working-with-resources)
  * resources must be called with their exact filename case ("myPic.JPG" <> "Mypic.jpg") <!-- http://stackoverflow.com/a/5407535 -->
6. graphical components (GUI) should be easily accessible via a dedicated API:
 * basica should natively support the [GW&trade; library](http://mougino.free.fr/gw.html) (an enhanced version)
 * the GUI composer should allow to build application screens in a WYSIWYG manner
 * all basica GUI components (dialogs, controls) should respect material design
7. basica APKs (compiled by users) should be as self-contained as possible
 * i.e. basica APKs should not make a mess by creating a lot of "sdcard/myAPKs/..." folders
 * i.e. HTML and SQL resources should be transparently accessed (R/W) without the need to be on SD

**See also:**
* [Differences with RFO BASIC!](#differences-with-rfo-basic)
* [Differences with VB6, PB, FB](#differences-with-vb6-pb-fb)
* [Credits](#credits)

<!------------------------------------------------------------------------------->
# Credits
The author would like to thank Paul Laughton who created RFO BASIC! that paved the way to basica.
The author would also like to thank jecelyin who created the 920 Editor V2 used in basica.
Finally, thanks to jMarc and the many contributors at the RFO BASIC! forum.

<!------------------------------------------------------------------------------->
# Command summary
The following is a list of the commands built into basica and separated into 18 groups of related commands, which can assist with identifying the best command for the task at hand.  Some commands may appear in more than one group.

* [Array, List, Stack and Bundle](#array-list-stack-and-bundle)
* [Communication Control](#communication-control)
* [Console Commands](#console-commands)
* [Debugging and Error Control](#debugging-and-error-control)
* [File Commands](#file-commands)
* [Flow Control](#flow-control)
* [Graphic Commands](#graphic-commands)
* [GW&trade; (GUI) Commands](#gw-gui-commands)
* [HTML Commands](#html-commands)
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
# Operating System
The following functions manipulate specific Android OS features (sensors, vibrate, notification etc.):
* [APP.BROADCAST](#app-broadcast)
* [APP.START](#app-start)
* [BACKGROUND](#background)
* [BACKGROUND.RESUME](#background-resume)
* [BROWSE](#browse)
* [CLIPBOARD.GET](#clipboard-get)
* [CLIPBOARD.PUT](#clipboard-put)
* [DEVICE](#device)
* [DEVICE.LANGUAGE](#device-language)
* [DEVICE.LOCALE](#device-locale)
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
* [HEADSET](#headset)
* [HOME](#home)
* [KB.HIDE](#kb-hide)
* [KB.SHOW](#kb-show)
* [KB.SHOWING](#kb-showing)
* [KB.TOGGLE](#kb-toggle)
* [KBTOGGLE.RESUME](#kbtoggle-resume)
* [MYPHONENUMBER](#myphonenumber)
* [NOTIFY](#notify)
* [ON.BACKGROUND](#on-background)
* [ON.KBTOGGLE](#on-kbtoggle)
* [PERMISSION](#permission-statement)
* [PERMISSION$](#permission-function)
* [PHONE.CALL](#phone-call)
* [PHONE.DIAL](#phone-dial)
* [PHONE.INFO](#phone-info)
* [PHONE.RCV.INIT](#phone-rcv-init)
* [PHONE.RCV.NEXT](#phone-rcv-next)
* [POPUP](#popup)
* [PROGRAM.INFO](#program-info)
* [RINGER.GET.MODE](#ringer-get-mode)
* [RINGER.GET.VOLUME](#ringer-get-volume)
* [RINGER.SET.MODE](#ringer-set-mode)
* [RINGER.SET.VOLUME](#ringer-set-volume)
* [SCREEN.INFO](#screen-info)
* [SCREEN.ROTATION](#screen-rotation)
* [SCREEN.SIZE](#screen-size)
* [SENSORS.CLOSE](#sensors-close)
* [SENSORS.LIST](#sensors-list)
* [SENSORS.OPEN](#sensors-open)
* [SENSORS.READ](#sensors-read)
* [SMS.RCV.INIT](#sms-rcv-init)
* [SMS.RCV.NEXT](#sms-rcv-next)
* [SMS.SEND](#sms-send)
* [STT.LISTEN](#stt-listen)
* [STT.RESULTS](#stt-results)
* [SU.CLOSE](#su-close)
* [SU.OPEN](#su-open)
* [SU.READ.LINE](#su-read-line)
* [SU.READ.READY](#su-read-ready)
* [SU.WRITE](#su-write)
* [SYSTEM.CLOSE](#system-close)
* [SYSTEM.OPEN](#system-open)
* [SYSTEM.READ.LINE](#system-read-line)
* [SYSTEM.READ.READY](#system-read-ready)
* [SYSTEM.WRITE](#system-write)
* [TTS.INIT](#tts-init)
* [TTS.SPEAK](#tts-speak)
* [TTS.SPEAK.TOFILE](#tts-speak-tofile)
* [TTS.STOP](#tts-stop)
* [VIBRATE](#vibrate)
* [VOLKEYS.OFF](#volkeys-off)
* [VOLKEYS.ON](#volkeys-on)
* [WAKELOCK](#wakelock)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Numeric Operations
The following functions manipulate and manage [numeric](#variable-types) data:
* [ABS](#abs)
* [ACOS](#acos)
* [AND](#and)
* [ARRAY.AVERAGE](#array-average)
* [ARRAY.MAX](#array-max)
* [ARRAY.MIN](#array-min)
* [ARRAY.STDDEV](#array-stddev)
* [ARRAY.SUM](#array-sum)
* [ARRAY.VARIANCE](#array-variance)
* [ASIN](#asin)
* [ATAN](#atan)
* [ATAN2](#atan2)
* [BAND](#band)
* [BIN](#bin-function)
* [BIN$](#bin-function-1)
* [BNOT](#bnot)
* [BOR](#bor)
* [BXOR](#bxor)
* [CBRT](#cbrt)
* [CEIL](#ceil)
* [COS](#cos)
* [COSH](#cosh)
* [EXP](#exp)
* [FLOOR](#floor)
* [FRAC](#frac)
* [HEX](#hex)
* [HEX$](#hex-1)
* [HYPOT](#hypot)
* [INT](#int)
* [INT$](#int-1)
* [LOG](#log)
* [LOG10](#log10)
* [MAX](#max)
* [MIN](#min)
* [MOD](#mod)
* [NOT](#not)
* [OCT](#oct)
* [OCT$](#oct-1)
* [OR](#or)
* [PI](#pi)
* [POW](#pow)
* [RND](#rnd)
* [ROUND](#round)
* [SGN](#sgn)
* [SHIFT](#shift)
* [SIN](#sin)
* [SINH](#sinh)
* [SQR](#sqr)
* [TAN](#tan)
* [TODEGREES](#todegrees)
* [TORADIANS](#toradians)
* [VAL](#val)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Input Commands
The following functions can be used to gather input data:
* [COMMAND$](#command)
* [DIALOG.MESSAGE](#dialog-message)
* [DIALOG.SELECT](#dialog-select)
* [GR.BOUNDED.TOUCH](#gr-bounded-touch)
* [GR.BOUNDED.TOUCH2](#gr-bounded-touch2)
* [GR.TOUCH](#gr-touch)
* [GR.TOUCH2](#gr-touch2)
* [GW.ACTION$](#gw-action)
* [GW.ADD.DIALOG.INPUT](#gw-add-dialog-input)
* [GW.ADD.INPUTBOX](#gw-add-inputbox)
* [GW.ADD.INPUTCOLOR](#gw-add-inputcolor)
* [GW.ADD.INPUTDATETIME](#gw-add-inputdatetime)
* [GW.ADD.INPUTDATE](#gw-add-inputdate)
* [GW.ADD.INPUTEMAIL](#gw-add-inputemail)
* [GW.ADD.INPUTLINE](#gw-add-inputline)
* [GW.ADD.INPUTLIST](#gw-add-inputlist)
* [GW.ADD.INPUTMONTH](#gw-add-inputmonth)
* [GW.ADD.INPUTNUMBER](#gw-add-inputnumber)
* [GW.ADD.INPUTPASSWORD](#gw-add-inputpassword)
* [GW.ADD.INPUTTEL](#gw-add-inputtel)
* [GW.ADD.INPUTTIME](#gw-add-inputtime)
* [GW.ADD.INPUTURL](#gw-add-inputurl)
* [GW.ADD.INPUTWEEK](#gw-add-inputweek)
* [GW.ADD.LISTENER](#gw-add-listener)
* [GW.WAIT.ACTION$](#gw-wait-action)
* [HTML.GET.DATALINK](#html-get-datalink)
* [INKEY$](#inkey)
* [INPUT](#input)
* [INPUT.BOX](#input-box)
* [INPUT.LINE](#input-line)
* [ON.BACKKEY](#on-backkey) and [BACKKEY.RESUME](#backkey-resume)
* [ON.CONTOUCH](#on-contouch) and [CONTOUCH.RESUME](#contouch-resume)
* [ON.GRTOUCH](#on-grtouch) and [GRTOUCH.RESUME](#grtouch-resume)
* [ON.KBTOGGLE](#on-kbtoggle) and [KBTOGGLE.RESUME](#kbtoggle-resume)
* [ON.KEYPRESS](#on-keypress) and [KEYPRESS.RESUME](#keypress-resume)
* [ON.MENUKEY](#on-menukey) and [MENUKEY.RESUME](#menukey-resume)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# HTML Commands
The HTML mode is one of basica's four display modes, along with the [console](#console-commands), [graphic](#graphic-commands) and [GW&trade; (GUI)](#gw-gui-commands) modes.

basica's HTML mode provides an Android Webview as a canvas, allowing you to render HTML/JavaScript code and interact with it.

The following functions can be used to access the HTML interface:
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

**See also:**
* [Console Commands](#console-commands)
* [Graphic Commands](#graphic-commands)
* [HTML Commands](#html-commands)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# GW (GUI) Library
Welcome to basica's powerful and improved **GW&trade; lib**. The GW&trade; library allows a basica programmer to easily create a Graphical User Interface (GUI) for an Android app using simple BASIC statements. With GW&trade;, there's no need to stress over learning how to effectively use GUI design software that contains icons you don't understand and also hundreds of cryptic "property" (XML) settings. With GW&trade;, your basica application can create user interface dialogs "on the fly".

This chapter describes basica's GW&trade; library and how to easily create full-featured Graphical User Interfaces in your code.

* [Load the lib](#load-the-lib)
* [Specify Page settings before creation](#specify-page-settings-before-creation)
* [Create a new Page](#create-a-new-page)
* [Transform the Page](#transform-the-page)
* [Prepare Controls Layout](#prepare-controls-layout)
* [Pre-Customize Controls](#pre-customize-controls)
* [Add Standard Controls](#add-standard-controls)
* [Add User Input Controls](#add-user-input-controls)
* [Add Bars](#add-bars)
* [Add a Panel](#add-a-panel)
* [Add a Spinner](#add-a-spinner)
* [Add Dialogs](#add-dialogs)
* [Custom Controls, Listeners](#custom-controls-listeners)
* [Render and Update the Page](#render-and-update-the-page)
* [Manage User Interaction](#manage-user-interaction)
* [Special Functions](#special-functions)

**See also:**
* [GW&trade; (GUI) Commands](#gw-gui-commands)
* [Console Commands](#console-commands)
* [Graphic Commands](#graphic-commands)
* [HTML Commands](#html-commands)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# GW (GUI) Commands
The [GW&trade; mode](#gw-gui-library) is one of basica's four display modes, along with the [console](#console-commands), [graphic](#graphic-commands) and [HTML](#html-commands) modes. GW&trade; focuses on Graphical User Interface (GUI) creation, to provide the typical "Look and Feel" of Android apps.

The following functions can be used to create [GW](#gw-gui-library) application interfaces:
* [GW.ACTION$](#gw-action)
* [GW.ADD.AUDIO](#gw-add-audio)
* [GW.ADD.BAR.LBUTTON$](#gw-add-bar-lbutton)
* [GW.ADD.BAR.LMENU$](#gw-add-bar-lmenu)
* [GW.ADD.BAR.RBUTTON$](#gw-add-bar-rbutton)
* [GW.ADD.BAR.RMENU$](#gw-add-bar-rmenu)
* [GW.ADD.BAR.TITLE$](#gw-add-bar-title)
* [GW.ADD.BUTTON](#gw-add-button)
* [GW.ADD.CHECKBOX](#gw-add-checkbox)
* [GW.ADD.COLORPICKER](#gw-add-colorpicker)
* [GW.ADD.DIALOG.CHECKBOX](#gw-add-dialog-checkbox)
* [GW.ADD.DIALOG.INPUT](#gw-add-dialog-input)
* [GW.ADD.DIALOG.MESSAGE](#gw-add-dialog-message)
* [GW.ADD.FLIPSWITCH](#gw-add-flipswitch)
* [GW.ADD.FONT$](#gw-add-font)
* [GW.ADD.FOOTBAR](#gw-add-footbar)
* [GW.ADD.GALLERY](#gw-add-gallery)
* [GW.ADD.ICON](#gw-add-icon)
* [GW.ADD.IMAGE](#gw-add-image)
* [GW.ADD.INPUTBOX](#gw-add-inputbox)
* [GW.ADD.INPUTCOLOR](#gw-add-inputcolor)
* [GW.ADD.INPUTDATETIME](#gw-add-inputdatetime)
* [GW.ADD.INPUTDATE](#gw-add-inputdate)
* [GW.ADD.INPUTEMAIL](#gw-add-inputemail)
* [GW.ADD.INPUTLINE](#gw-add-inputline)
* [GW.ADD.INPUTLIST](#gw-add-inputlist)
* [GW.ADD.INPUTMONTH](#gw-add-inputmonth)
* [GW.ADD.INPUTNUMBER](#gw-add-inputnumber)
* [GW.ADD.INPUTPASSWORD](#gw-add-inputpassword)
* [GW.ADD.INPUTTEL](#gw-add-inputtel)
* [GW.ADD.INPUTTIME](#gw-add-inputtime)
* [GW.ADD.INPUTURL](#gw-add-inputurl)
* [GW.ADD.INPUTWEEK](#gw-add-inputweek)
* [GW.ADD.LINK](#gw-add-link)
* [GW.ADD.LISTENER](#gw-add-listener)
* [GW.ADD.LISTVIEW](#gw-add-listview)
* [GW.ADD.LOADING.IMG](#gw-add-loading-img)
* [GW.ADD.LOCK.PATTERN](#gw-add-lock-pattern)
* [GW.ADD.PANEL](#gw-add-panel)
* [GW.ADD.PROGRESSBAR](#gw-add-progressbar)
* [GW.ADD.RADIO](#gw-add-radio)
* [GW.ADD.SELECTBOX](#gw-add-selectbox)
* [GW.ADD.SLIDER](#gw-add-slider)
* [GW.ADD.SPINNER](#gw-add-spinner)
* [GW.ADD.SUBMIT](#gw-add-submit)
* [GW.ADD.TABLE](#gw-add-table)
* [GW.ADD.TEXTBOX](#gw-add-textbox)
* [GW.ADD.TEXT](#gw-add-text)
* [GW.ADD.TITLEBAR](#gw-add-titlebar)
* [GW.ADD.TITLE](#gw-add-title)
* [GW.ADD.VIDEO](#gw-add-video)
* [GW.ALLOW.SELECT](#gw-allow-select)
* [GW.AMODIFY)](#gw-amodify)
* [GW.AMODIFY](#gw-amodify)
* [GW.CENTER.PAGE.VER](#gw-center-page-ver)
* [GW.CHECKBOX.CHECKED](#gw-checkbox-checked)
* [GW.CLEAR.LOCK.PATTERN](#gw-clear-lock-pattern)
* [GW.CLOSE.COLLAPSIBLE](#gw-close-collapsible)
* [GW.CLOSE.DIALOG](#gw-close-dialog)
* [GW.CLOSE.GALLERY](#gw-close-gallery)
* [GW.CLOSE.GROUP](#gw-close-group)
* [GW.CLOSE.INPUTLIST](#gw-close-inputlist)
* [GW.CLOSE.PAGE](#gw-close-page)
* [GW.CLOSE.PANEL](#gw-close-panel)
* [GW.CODE.HIGHLIGHT$](#gw-code-highlight)
* [GW.CUSTO.DLGBTN](#gw-custo-dlgbtn)
* [GW.DEFAULT.TRANSITIONS](#gw-default-transitions)
* [GW.DISABLE](#gw-disable)
* [GW.DOWNLOAD.THEME](#gw-download-theme)
* [GW.DUMP.TO.FILE](#gw-dump-to-file)
* [GW.DUMP](#gw-dump)
* [GW.ENABLE](#gw-enable)
* [GW.FLIPSWITCH.CHANGED](#gw-flipswitch-changed)
* [GW.FOCUS](#gw-focus)
* [GW.GALLERY.IS.OPEN](#gw-gallery-is-open)
* [GW.GET.IMAGE.DIM$](#gw-get-image-dim)
* [GW.GET.VALUE$](#gw-get-value)
* [GW.GET.VALUE](#gw-get-value)
* [GW.HIDE.SPINNER](#gw-hide-spinner)
* [GW.HIDE](#gw-hide)
* [GW.ICON$](#gw-icon)
* [GW.ID$](#gw-id)
* [GW.ID](#gw-id)
* [GW.INJECT.HTML](#gw-inject-html)
* [GW.LAST.ID](#gw-last-id)
* [GW.LINK$](#gw-link)
* [GW.LOAD.THEME](#gw-load-theme)
* [GW.MODIFY)](#gw-modify)
* [GW.MODIFY](#gw-modify)
* [GW.NEW.CLASS](#gw-new-class)
* [GW.NEW.PAGE](#gw-new-page)
* [GW.NEW.CUSTO](#gw-new-custo)
* [GW.OPEN](#gw-open)
* [GW.OPEN.COLLAPSIBLE](#gw-open-collapsible)
* [GW.OPEN.GROUP](#gw-open-group)
* [GW.PICK.FILE$](#gw-pick-file)
* [GW.PICK.FOLDER$](#gw-pick-folder)
* [GW.PREVENT.SELECT](#gw-prevent-select)
* [GW.QUICK.CUSTO](#gw-quick-custo)
* [GW.RADIO.SELECTED](#gw-radio-selected)
* [GW.RENDER](#gw-render)
* [GW.RESET.CUSTO](#gw-reset-custo)
* [GW.SET.PROGRESSBAR](#gw-set-progressbar)
* [GW.SET.TRANSITION](#gw-set-transition)
* [GW.SHELF.CLOSE](#gw-shelf-close)
* [GW.SHELF.NEWCELL](#gw-shelf-newcell)
* [GW.SHELF.NEWROW](#gw-shelf-newrow)
* [GW.SHELF.OPEN](#gw-shelf-open)
* [GW.SHOW.DIALOG$](#gw-show-dialog)
* [GW.SHOW.DIALOG](#gw-show-dialog)
* [GW.SHOW.PANEL$](#gw-show-panel)
* [GW.SHOW.PANEL](#gw-show-panel)
* [GW.SHOW.SPINNER](#gw-show-spinner)
* [GW.SHOW.WRONG.PATTERN](#gw-show-wrong-pattern)
* [GW.SHOW](#gw-show)
* [GW.START.CENTER](#gw-start-center)
* [GW.STOP.CENTER](#gw-stop-center)
* [GW.THEME$](#gw-theme)
* [GW.THEME.EXISTS](#gw-theme-exists)
* [GW.UNLOAD.THEME](#gw-unload-theme)
* [GW.USE.FONT](#gw-use-font)
* [GW.USE.CUSTO](#gw-use-custo)
* [GW.WAIT.ACTION$](#gw-wait-action)
* [GW.ZOOM.INPUT](#gw-zoom-input)

**See also:**
* [GW&trade; (GUI) Library](#gw-gui-library)
* [Console Commands](#console-commands)
* [Graphic Commands](#graphic-commands)
* [HTML Commands](#html-commands)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Bitmaps
In Android OS, and in basica [graphic mode](#graphic-commands), an image is called a "**bitmap**", although any kind of picture can be loaded as a "bitmap" (not only .bmp files). For example: .jpg, .png (with transparency), .gif, etc. can be loaded as a bitmap (note that animated gifs are not supported, only the first frame will be loaded).

Some bitmaps are said **immutable** (a simpler word is "read-only"). This is typically the case when you load a bitmap from a file with the [GR.BITMAP.LOAD](#gr-bitmap-load) command: the pointer points to an immutable bitmap, i.e. you cannot draw on the resulting bitmap.

On the other hand, basica allows you to create blank "bitmaps" (via [GR.BITMAP.CREATE](#gr-bitmap-create)) to be used as a **canvas** and draw into them (via [GR.BITMAP.DRAWINTO.START](#gr-bitmap-drawinto-start) / [GR.BITMAP.DRAWINTO.END](#gr-bitmap-drawinto-end)). Drawing objects into a canvas bitmap is very fast, especially if you draw a big number of objects. This technique can be used if you want to achieve performance, but note that the objects drawn in the canvas bitmap will become immutable themselves, as they will become part of the bitmap - you won't be able to change their individual properties with [GR.MODIFY](#gr-modify) anymore.

Let's take an example:
```vb
GR.OPEN ' open graphic mode
GR.SCREEN w, h ' get screen width and height

PRINT "Drawing 200 colored rectangles directly on screen"
t = TIMER()
FOR i=1 TO 200
  GR.COLOR 255, 256*RND(), 256*RND(), 256*RND() ' alpha=255 (opaque); random RGB
  GR.RECT objId, w*RND(), h*RND(), w*RND(), h*RND() ' draw rectangle at random coordinates on screen
  GR.RENDER ' render graphic screen to show new rectangle
NEXT
t = (TIMER() - t) / 1000 ' TIMER() is in milliseconds -> round it to seconds
PRINT "Done in " + INT$(t) + " seconds"

GR.CLS ' clear graphic screen
PRINT "Drawing 200 colored rectangles in a canvas bitmap the size of the screen"
GR.BITMAP.CREATE bmpPtr, w, h ' create canvas bitmap
GR.BITMAP.DRAW objId, bmpPtr, 0, 0 ' put it on the screen
GR.BITMAP.DRAWINTO.START bmpPtr ' start drawing in it
t = TIMER()
FOR i=1 TO 200
  GR.COLOR 255, 256*RND(), 256*RND(), 256*RND() ' exact same code as above
  GR.RECT objId, w*RND(), h*RND(), w*RND(), h*RND()
  GR.RENDER
NEXT
t = (TIMER() - t) / 1000
GR.BITMAP.DRAWINTO.END
PRINT "Done in " + INT$(t) + " seconds"
```

Typical result on the above snippet are 22 seconds to draw 200 colored rectangles directly on screen, and only half (11 seconds) if they are drawn in a canvas bitmap, itself drawn on the screen. The more objects you draw, the bigger difference there will be in the results, since each new object on screen slows down the rendering ; while with the [GR.BITMAP.DRAWINTO](#gr-bitmap-drawinto-start) technique there is only one bitmap object on the screen at all time.

If you want to alter (draw on) an image loaded from disk, you need to first load it as a bitmap (immutable), create a canvas bitmap of the same size, draw your first bitmap into it (you can then recycle the first bitmap to free memory), and continue to draw into your canvas bitmap.

The following snippet illustrates this case:

```vb
GR.OPEN ' open graphic mode
myPic$ = "image.png" ' replace with path to an image present on your device
GR.BITMAP.LOAD immutablePtr, myPic$
IF NOT immutablePtr THEN END "Error loading " + myPic$
GR.BITMAP.SIZE immutablePtr, w, h ' get myPic$ dimensions (WxH pixels)
GR.BITMAP.CREATE canvasPtr, w, h ' create a canvas bitmap of the same size
GR.BITMAP.DRAWINTO.START canvasPtr
GR.BITMAP.DRAW objId, immutablePtr, 0, 0 ' draw myPic$ in this canvas
GR.BITMAP.DELETE immutablePtr ' now that we used myPic$ we can recycle it
GR.WIDTH 5 ' set line width to 5 pixels
GR.LINE objId, 0, 0, w, h ' this command and the next one draw a black "X" on top of myPic$
GR.LINE objId, 0, h, w, 0
GR.BITMAP.DRAWINTO.END
GR.BITMAP.DRAW objId, canvasPtr, 0, 0 ' draw the canvas bitmap on screen
GR.RENDER ' render!
DO : SLEEP 1 : UNTIL 0 ' pause until Back key is hit
```

Bitmaps take a lot of internal memory. Loading several bitmaps is usually a bottleneck when developping small games. You need to be very careful to load only the bitmaps needed on screen at a given time, and recycle them as soon as you are done with them, via [GR.BITMAP.DELETE](#gr-bitmap-delete).

The following commands also create internal bitmaps, and should be carefully monitored for the same memory concerns: [GR.BITMAP.CREATE](#gr-bitmap-create) of course, but also [GR.BITMAP.CROP](#gr-bitmap-crop) and [GR.BITMAP.SCALE](#gr-bitmap-scale).

**See also:**
* [Graphic Commands](#graphic-commands)

<!------------------------------------------------------------------------------->
# Graphic Commands
The graphic (GR) mode is one of basica's four display modes, along with the [console](#console-commands), [GW&trade; (GUI)](#gw-gui-commands) and [HTML](#html-commands) modes.

basica's graphic mode is similar to a black board. You can draw anything on it: text, images (aka "[bitmaps](#bitmaps)"), and forms (circles, rectangles etc.)
This mode allows you to detect finger-touch on the screen (up to 2 fingers), making it the prefered mode for creating small Android games. The graphic mode also allows you to operate the device camera.

The following functions can be used to operate the graphic mode:
* [FONT.CLEAR](#font-clear)
* [FONT.DELETE](#font-delete)
* [FONT.LOAD](#font-load)
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
* [GR.COLLISION](#gr-collision)
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
* [GR.SCREEN.TOBITMAP](#gr-screen-tobitmap)
* [GR.SET.ANTIALIAS](#gr-set-antialias)
* [GR.SET.PIXELS](#gr-set-pixels)
* [GR.SHOW](#gr-show)
* [GR.SHOW.TOGGLE](#gr-show-toggle)
* [GR.STATUSBAR](#gr-statusbar)
* [GR.STATUSBAR.SHOW](#gr-statusbar-show)
* [GR.TEXT.ALIGN](#gr-text-align)
* [GR.TEXT.BOLD](#gr-text-bold)
* [GR.TEXT.DRAW](#gr-text-draw)
* [GR.TEXT.HEIGHT](#gr-text-height)
* [GR.TEXT.ITALIC](#gr-text-italic)
* [GR.TEXT.SETFONT](#gr-text-setfont)
* [GR.TEXT.SIZE](#gr-text-size)
* [GR.TEXT.STRIKE](#gr-text-strike)
* [GR.TEXT.TYPEFACE](#gr-text-typeface)
* [GR.TEXT.UNDERLINE](#gr-text-underline)
* [GR.TEXT.WIDTH](#gr-text-width)
* [GR.TOUCH](#gr-touch)
* [GR.TOUCH2](#gr-touch2)
* [GR.WIDTH](#gr-width)
* [GRTOUCH.RESUME](#grtouch-resume)
* [ON.GRTOUCH](#on-grtouch)

**See also:**
* [Console Commands](#console-commands)
* [GW&trade; (GUI) Commands](#gw-gui-commands)
* [HTML Commands](#html-commands)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Console Commands
The console is the simplest display mode among the four modes offered in basica (the three others being [graphic](#graphic-commands), [GW&trade; (GUI)](#gw-gui-commands) and [HTML](#html-commands)).

Like Linux or Windows consoles, basica's console allows to print and input simple text.
basica's console is also highly customizable: font, size, colors, lines, orientation...

The following functions can be used to operate on the console:
* [CLS](#cls)
* [CON.COLORS](#con-colors)
* [CON.FONT.SIZE](#con-font-size)
* [CON.FONT.TYPE](#con-font-type)
* [CON.FRONT](#con-front)
* [CON.LINE.COUNT](#con-line-count)
* [CON.LINE.TEXT](#con-line-text)
* [CON.LINE.TOUCHED](#con-line-touched)
* [CON.ORIENTATION](#con-orientation)
* [CON.SAVE](#con-save)
* [CON.SELECT](#con-select)
* [CON.SHOW.EMPTY](#con-show-empty)
* [CON.SHOW.LINES](#con-show-lines)
* [CON.TITLE](#con-title)
* [CONTOUCH.RESUME](#contouch-resume)
* [INPUT](#input)
* [ON.CONTOUCH](#on-contouch)
* [PRINT](#print)

**See also:**
* [Graphic Commands](#graphic-commands)
* [GW&trade; (GUI) Commands](#gw-gui-commands)
* [HTML Commands](#html-commands)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Flow Control
The following functions can be used to manage program execution/flow:
* [CALL](#call)
* [DO/{LOOP} UNTIL](#do)
* [END](#end-disambiguation)
* [EXIT](#exit-disambiguation)
* [FOR/NEXT](#for)
* [FUNCTION/END FUNCTION](#function)
* [GOSUB](#gosub)
* [GOTO](#goto)
* [IF](#if)
* [IF/END IF](#if-end-if-block)
* [INCLUDE](#include)
* [ITERATE](#iterate-disambiguation)
* [ON.BACKGROUND](#on-background) and [BACKGROUND.RESUME](#background-resume)
* [ON.BACKKEY](#on-backkey) and [BACKKEY.RESUME](#backkey-resume)
* [ON.BTREADREADY](#on-btreadready) and [BTREADREADY.RESUME](#btreadready-resume)
* [ON.CONTOUCH](#on-contouch) and [CONTOUCH.RESUME](#contouch-resume)
* [ON.ERROR](#on-error)
* [ON.GRTOUCH](#on-grtouch) and [GRTOUCH.RESUME](#grtouch-resume)
* [ON.KBTOGGLE](#on-kbtoggle) and [KBTOGGLE.RESUME](#kbtoggle-resume)
* [ON.KEYPRESS](#on-keypress) and [KEYPRESS.RESUME](#keypress-resume)
* [ON.LOWMEMORY](#on-lowmemory) and [LOWMEMORY.RESUME](#lowmemory-resume)
* [ON.MENUKEY](#on-menukey) and [MENUKEY.RESUME](#menukey-resume)
* [ON.TIMER](#on-timer) and [TIMER.RESUME](#timer-resume)
* [PROGRAM.INFO](#program-info)
* [RETURN](#gosub)
* [RUN](#run)
* [SELECT CASE](#select-case)
* [SLEEP](#sleep)
* [SUB/END SUB](#sub)
* [WHILE/WEND](#while)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Debugging and Error Control
The following functions can be used to trap and manage error conditions:
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
* [ERROR$](#error)
* [ON.ERROR](#on-error)
* [ON.LOWMEMORY](#on-lowmemory)

Back to [Command summary](#command-summary)

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
* [ARRAY.STDDEV](#array-stddev)
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
* [BACKKEY.RESUME](#backkey-resume)
* [BACKGROUND](#background)
* [BACKGROUND.RESUME](#background-resume)
* [BAND](#band)
* [BEEP](#beep)
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
* [BTREADREADY.RESUME](#btreadready-resume)
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
* [CLOSE](#close)
* [CLS](#cls)
* [COMMAND$](#command)
* [CON.COLORS](#con-colors)
* [CON.FONT.SIZE](#con-font-size)
* [CON.FONT.TYPE](#con-font-type)
* [CON.FRONT](#con-front)
* [CON.LINE.COUNT](#con-line-count)
* [CON.LINE.TEXT](#con-line-text)
* [CON.LINE.TOUCHED](#con-line-touched)
* [CON.ORIENTATION](#con-orientation)
* [CON.SAVE](#con-save)
* [CON.SELECT](#con-select)
* [CON.SHOW.EMPTY](#con-show-empty)
* [CON.SHOW.LINES](#con-show-lines)
* [CON.TITLE](#con-title)
* [CONTOUCH.RESUME](#contouch-resume)
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
* [ERROR$](#error)
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
* [GLOBAL](#global)
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
* [GR.COLLISION](#gr-collision)
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
* [GR.SCREEN.TOBITMAP](#gr-screen-tobitmap)
* [GR.SET.ANTIALIAS](#gr-set-antialias)
* [GR.SET.PIXELS](#gr-set-pixels)
* [GR.SHOW](#gr-show)
* [GR.SHOW.TOGGLE](#gr-show-toggle)
* [GR.STATUSBAR](#gr-statusbar)
* [GR.STATUSBAR.SHOW](#gr-statusbar-show)
* [GR.TEXT.ALIGN](#gr-text-align)
* [GR.TEXT.BOLD](#gr-text-bold)
* [GR.TEXT.DRAW](#gr-text-draw)
* [GR.TEXT.HEIGHT](#gr-text-height)
* [GR.TEXT.ITALIC](#gr-text-italic)
* [GR.TEXT.SETFONT](#gr-text-setfont)
* [GR.TEXT.SIZE](#gr-text-size)
* [GR.TEXT.STRIKE](#gr-text-strike)
* [GR.TEXT.TYPEFACE](#gr-text-typeface)
* [GR.TEXT.UNDERLINE](#gr-text-underline)
* [GR.TEXT.WIDTH](#gr-text-width)
* [GR.TOUCH](#gr-touch)
* [GR.TOUCH2](#gr-touch2)
* [GR.WIDTH](#gr-width)
* [GRTOUCH.RESUME](#grtouch-resume)
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
* [INPUT](#input-disambiguation)
* [INPUT.BOX](#input-box)
* [INPUT.LINE](#input-line)
* [INSTR](#instr-function)
* [INT](#int)
* [INT$](#int-1)
* [IS_IN](#is_in-function)
* [IS_NUMBER](#is-number)
* [ITERATE](#iterate-disambiguation)

## J
* [JOIN](#join)
* [JOIN.ALL](#join-all)

## K
* [KB.HIDE](#kb-hide)
* [KB.SHOW](#kb-show)
* [KB.SHOWING](#kb-showing)
* [KB.TOGGLE](#kb-toggle)
* [KBTOGGLE.RESUME](#kbtoggle-resume)
* [KEYPRESS.RESUME](#keypress-resume)
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
* [ON.BACKGROUND](#on-background)
* [ON.BACKKEY](#on-backkey)
* [ON.BTREADREADY](#on-btreadready)
* [ON.CONTOUCH](#on-contouch)
* [ON.ERROR](#on-error)
* [ON.GRTOUCH](#on-grtouch)
* [ON.KBTOGGLE](#on-kbtoggle)
* [ON.KEYPRESS](#on-keypress)
* [ON.LOWMEMORY](#on-lowmemory)
* [ON.MENUKEY](#on-menukey)
* [ON.TIMER](#on-timer)
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
* [REMOVE$](#remove)
* [REPLACE$](#replace)
* [RETURN](#return-disambiguation)
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
* [SCREEN.INFO](#screen-info)
* [SCREEN.ROTATION](#screen-rotation)
* [SCREEN.SIZE](#screen-size)
* [SEEK](seek-disambiguation)
* [SELECT CASE](#select-case)
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
* [SPACE$](#space)
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
* [TIMER](#timer)
* [TIMER.CLEAR](#timer-clear)
* [TIMER.RESUME](#timer-resume)
* [TIMER.SET](#timer-set)
* [TIMEZONE.GET](#timezone-get)
* [TIMEZONE.LIST](#timezone-list)
* [TIMEZONE.SET](#timezone-set)
* [TODEGREES](#todegrees)
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
* [VERSION](#version)
* [VERSION$](#version-1)
* [VIBRATE](#vibrate)
* [VOLKEYS.OFF](#volkeys-off)
* [VOLKEYS.ON](#volkeys-on)

## W
* [WAKELOCK](#wakelock)
* [WEND](#while)
* [WHILE](#while)
* [WIFI.INFO](#wifi-info)
* [WIFI.LOCK](#wifi-lock)
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

## Changes in interrupts
RFO BASIC! | basica
-----------|-------
ONBACKGROUND/BACKGROUND.RESUME | ON.BACKGROUND/BACKGROUND.RESUME <!--OK-->
ONBACKKEY/BACK.RESUME | ON.BACKKEY/BACKKEY.RESUME <!--OK-->
ONBTREADREADY/BT.ONREADREADY.RESUME | ON.BTREADREADY/BTREADREADY.RESUME <!--OK-->
ONCONSOLETOUCH/CONSOLETOUCH.RESUME | ON.CONTOUCH/CONTOUCH.RESUME <!--OK-->
ONERROR | ON.ERROR <!--OK-->
ONGRTOUCH/GR.ONGRTOUCH.RESUME | ON.GRTOUCH/GRTOUCH.RESUME <!--OK-->
ONKBCHANGE/KB.RESUME | ON.KBTOGGLE/KBTOGGLE.RESUME <!--OK-->
ONKEYPRESS/KEY.RESUME | ON.KEYPRESS/KEYPRESS.RESUME <!--OK-->
ONLOWMEMORY/LOWMEMORY.RESUME | ON.LOWMEMORY/LOWMEMORY.RESUME <!--OK-->
ONMENUKEY/MENUKEY.RESUME | ON.MENUKEY/MENUKEY.RESUME <!--OK-->
ONTIMER/TIMER.RESUME | ON.TIMER/TIMER.RESUME <!--OK-->

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
WHILE/REPEAT | WHILE/WEND <!--OK-->

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
Non existent | ZIP *folder$* TO *zipFile$*
Non existent | UNZIP *zipFile$* TO *folder$*

## Changes in order of parameters
RFO BASIC! | basica
-----------|-------
ARRAY.AVERAGE | ARRAY.AVERAGE *array[]*, *average* <!--OK-->
ARRAY.LENGTH | ARRAY.LEN *array[]*, *length* <!--OK-->
ARRAY.MAX | ARRAY.MAX *array[]*, *max* <!--OK-->
ARRAY.MIN | ARRAY.MIN *array[]*, *min* <!--OK-->
ARRAY.STD_DEV | ARRAY.STDDEV *array[]*, *standardDeviation* <!--OK-->
ARRAY.SUM | ARRAY.SUM *array[]*, *sum* <!--OK-->
ARRAY.VARIANCE | ARRAY.VARIANCE *array[]*, *variance* <!--OK-->
LIST.SIZE | LIST.LEN *listId*, *length* <!--OK-->
FILE.DELETE | FILE.DELETE *file$*, *delOK* <!--OK-->
FILE.EXISTS | FILE.EXISTS *file$*, *exists* <!--OK-->
FILE.SIZE | FILE.SIZE *file$*, *size* <!--OK-->
FILE.TYPE | FILE.TYPE *file$*, *type* <!--OK-->
GR.TEXT.DRAW | GR.TEXT.DRAW *grObjId*, *text$*, *drawX*, *drawY*

## Other changes
RFO BASIC! | basica
-----------|-------
&#126; (line continuation) | underscore &#95; <!--OK-->
&#33; (comment) | single quote &#39; <!--OK-->
&#37; (inline comment) | single quote &#39; <!--OK-->
&#33;&#33; (block comment) | **removed**, use &#39; in front of each line instead <!--OK-->
&#33; (operator) | NOT
&#38; | AND
&#124; | OR
CONSOLE.* commands | renamed as CON.* commands <!--OK-->
SELECT | CON.SELECT
PAUSE | SLEEP <!--OK-->
CLOCK | TIMER <!--OK-->
FN.DEF | SUB&#124;FUNCTION funcName{$} ( {param1{$}} {,param2{$}} ... )
FN.END | END SUB&#124;FUNCTION
FN.RTN result{$} | RETURN result{$}, EXIT SUB&#124;FUNCTION
GETERROR$ | ERROR$ <!--OK-->
GR_COLLISION | GR.COLLISION grObjId1, grObjId2, collision
GR.SET.STROKE | GR.WIDTH <!--OK-->
GR.TEXT.SKEW | GR.TEXT.ITALIC <!--OK-->
LOWER$ | LCASE$ <!--OK-->
UPPER$ | UCASE$ <!--OK-->
TONE | BEEP <!--OK-->
TGET | INPUT prompt$, result{$}
INPUT | INPUT.LINE
SCREEN | SCREEN.INFO <!--OK-->
TEXT.INPUT | INPUT.BOX
WIFILOCK | WIFI.LOCK <!--OK-->

# Additions
* [Arithmetic operator](#arithmetic-operators) `\` for integral division
* [CHDIR](#chdir), [FILE.COPY](#file-copy), [KILL](#kill)
* Support of wildcards (`*`, `?`) in [FILE.*](#file-commands) commands <!-- http://stackoverflow.com/a/805504 -->
* [CON.COLORS](#con-colors), [CON.FONT.SIZE](#con-font-size), [CON.FONT.TYPE](#con-font-type), [CON.ORIENTATION](#con-orientation), [CON.SHOW.EMPTY](#con-show-empty), [CON.SHOW.LINES](#con-show-lines)
* [GLOBAL](#global)
* [INSTR](#instr-function)
* [LOF](#lof), [SETBOF](#setbof)/[SETSOF](#setbof) and [SETEOF](#seteof)
* [PARSECOUNT](#parsecount), [PARSE$](#parse) and [TALLY](#tally)
* [PERMISSION](#permission-statement) and [PERMISSION$](#permission-function)
* [REDIM](#redim) and [REDIM PRESERVE](#redim)
* [REMOVE$](#remove)
* [SPACE$](#space)
* [UBOUND](#ubound)

**See also:**
* [Differences with VB6, PB, FB](#differences-with-vb6-pb-fb)

Back to [basica](#basica)

<!------------------------------------------------------------------------------->
# Differences with VB6, PB, FB
Herebelow you will find an equivalence-table for programmers who are fluent in Visual Basic 6 and/or PowerBasic and/or FreeBasic in order to find the matching function(s) in basica:

VB6, PB, FB | basica
------------|-------
#DEBUG | See [DEBUG.*](#debug-on) commands
#INCLUDE | See [INCLUDE](#include)
ARRAY ASSIGN | See [ARRAY.LOAD](#array-load)
ARRAY SCAN | See [ARRAY.SEARCH](#array-search)
DATA | See [READ.DATA](#read-data)
DIR$ | See [FILE.DIR](#file-dir)
ERASE | See [UNDIM](#undim) or [ARRAY.DELETE](#array-delete)
EXE.* | See [PROGRAM.INFO](#program-info)
FILEATTR | See [FILE.TYPE](#file-type)
FILECOPY | See [FILE.COPY](#file-copy)
FONT NEW | See [FONT.LOAD](#font-load)
FREEFILE | **Removed**, see [OPEN](#open-statement)
GRAPHIC * | See [GR.*](#gr-open) commands
IIF and IIF$ | **Not available**, you can write your own [user functions](#function)
INPUTBOX$ | See [INPUT.BOX](#input-box) or [INPUT.LINE](#input-line)
INSTR | See [IS_IN](#is_in-function)
ISFALSE | See [NOT](#not) e.g. `IF NOT cond`, triggered if `cond` is zero
ISTRUE | **No need**, in basica `IF cond` is evaluated TRUE if `cond` is not zero
LBOUND | **Removed**, in basica all arrays have a lower bound of `1`
LOCAL | **No need**, all variables not [GLOBAL](#global) are local by default
MID$ statement e.g. `MID$(s$,5,2) = "ab"` | **Not available**, see the [MID$](#mid) example
MKDIR | See [FILE.MKDIR](#file-mkdir)
a MOD b | MOD(a, b)
MSGBOX | See [POPUP](#popup) or [DIALOG.MESSAGE](#dialog-message)
NAME | See [FILE.RENAME](#file-rename)
ON n GOSUB and ON n GOTO | See [GOSUB n, ..](#gosub) and [GOTO n, ..](#goto)
ON ERROR | See [ON.ERROR](#on-error)
READ$ | See [READ.FROM](#read-from) and [READ.NEXT](#read-next)
REPLACE a$ WITH b$ IN main$ | `main$ = REPLACE$(main$, a$, b$)`
RESUME | See [Interrupts](#changes-in-interrupts)
RMDIR | See [FILE.DELETE](#file-delete)
SHELL | See [SYSTEM.*](#system-open) or [SU.*](#su-open) commands
STATIC | **Not available**, if you need a STATIC make it [GLOBAL](#global)
TCP * | See [SOCKET.*](#socket-tcp-ip-commands) commands
THREAD | **Not available**
TRACE, TRON, TROFF ... | See [DEBUG.*](#debugging-and-error-control) commands

**See also:**
* [Differences with RFO BASIC!](#differences-with-rfo-basic)

Back to [basica](#basica)

<!------------------------------------------------------------------------------->
# Array, List, Stack and Bundle
It is often useful to treat a set of [variables](#variables) as a group. This lets you perform repetitive operations more easily. basica offers four types of structure to manage sets of variables: Array, List, Stack and Bundle.

See:
* [Array structure](#array-structure) (definition) and [Array operations](#array-operations)
* [List structure](#list-structure) (definition) and [List operations](#list-operations)
* [Stack structure](#stack-structure) (definition) and [Stack operations](#stack-operations)
* [Bundle structure](#bundle-structure) (definition) and [Bundle operations](#bundle-operations)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Bundle Structure
A Bundle is a group of values collected together into a single object. A bundle object may contain any number of [string](#variable-types) and [numeric](#variable-types) values. There is no fixed limit on the size or number of bundles. You are limited only by the memory of your device.

The values are set and accessed by **keys**. A key is a string that identifies the value. For example, a bundle might contain a person’s first name and last name. The keys for accessing those name strings could be `"first_name"` and `"last_name"`. An age numeric value could also be placed in the bundle using an `"age"` key (see the example below).

A new, empty bundle is created by using the [BUNDLE.CREATE](#bundle-create) command. The command returns a [pointer](#pointers) to the empty bundle. Because the bundle is represented by a pointer, bundles can be placed in [lists](#list-structure) and [arrays](#array-structure). Bundles can also be contained in other bundles. This means that the combination of lists and bundles can be used to create arbitrarily complex data structures.

After a bundle is created, keys and values can be added to the bundle using the [BUNDLE.PUT](#bundle-put) command. Those values can be retrieved using the keys in the [BUNDLE.GET](#bundle-get) command. There are other bundle commands to facilitate the use of bundles.

**Examples:**
```vb
BUNDLE.CREATE bundleId
BUNDLE.PUT bundleId, "first_name", "Nicolas" ' key$="first_name" ; value$="Nicolas"
BUNDLE.PUT bundleId, "last_name", "Mougin"   ' key$="last_name" ; value$="Mougin"
BUNDLE.PUT bundleId, "age", 36               ' key$="age" ; value=36.0
```

## Bundle Auto-Create

Every bundle command has a parameter, *bundleId*, which is a [pointer](#pointers) to a bundle. If *bundleId* points to an actual bundle, this existing bundle is used. If it does not, then a new, empty bundle is created, and its pointer is stored in the [numeric variable](#variables) *bundleId*.

**Examples:** (see below for explanations)
```vb
BUNDLE.PUT b, "key1", 1.2     ' try to put a value in the bundle pointed to by b
BUNDLE.PUT 10, key2$, value2  ' try to put a value in the 10th bundle created
BUNDLE.REMOVE c+d, key$[3]    ' try to remove a key/value pair from a bundle pointed to by c+d
```

In the first example, if the value of `b` points to an existing bundle, the [BUNDLE.PUT](#bundle-put) command puts `"key1"` and the value `1.2` into that bundle. If there is no bundle pointer of the value of `b`, `BUNDLE.PUT` creates a new bundle, puts `"key1"` and the value `1.2` into the new bundle, and stores the bundle pointer inside the variable `b`.

In the second example, if there are at least ten bundles, then the `BUNDLE.PUT` command tries to put the key of the value of `key2$` with the value of `value2` into bundle #10. If there is no bundle #10, then the command does nothing. It cannot create a new variable because you did not provide a variable to store the bundle pointer.

In the third example, the bundle pointer is the value of the expression `c+d`. If there is no such bundle, the command does nothing. To create a new bundle, the bundle pointer expression must be a single [numeric variable](#variables).

**See also:**
* [Bundle Operations](#bundle-operations)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# Bundle Operations
The following functions can be used to manipulate and manage bundles:
* [BUNDLE.CLEAR](#bundle-clear)
* [BUNDLE.CONTAIN](#bundle-contain)
* [BUNDLE.CREATE](#bundle-create)
* [BUNDLE.GET](#bundle-get)
* [BUNDLE.KEYS](#bundle-keys)
* [BUNDLE.PUT](#bundle-put)
* [BUNDLE.REMOVE](#bundle-remove)
* [BUNDLE.TYPE](#bundle-type)

**See also:**
* [Bundle Structure](#bundle-structure)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# Queue structure
"Queues" are like the line that forms at your bank. When you arrive, you get in the back of the line or queue. When a teller becomes available the person at the head of the line or queue is removed from the queue to be serviced by the teller. The whole line moves forward by one person. Eventually, you get to the head of the line and will be serviced by the next available teller.

A queue is something like a [stack](#stack-structure) except the processing order is First In First Out (FIFO) rather than LIFO.

Using our customer order processing analogy, you could create a queue of order [bundles](#bundle-structure) for the order processing department. New order bundles would be placed at the end of the queue. The top-of-the-queue bundle would be removed by the order processing department when it was ready to service a new order.

There are no special commands in basica for queue operations. If you want to make a queue, create a [list](#list-structure).

Use [LIST.ADD](#list-add) to add new elements to the end of the queue.

Use [LIST.GET](#list-get) to get the element at the top of the queue and use [LIST.REMOVE](#list-remove) to remove that top of queue element. You should, of course, use [LIST.LEN](#list-len) before using [LIST.GET](#list-get) to ensure that there is a queued element remaining.

See:
* [List structure](#list-structure)
* [Stack structure](#stack-structure)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# Stack Structure
A stack is a collection of [string](#variable-types) or [numeric](#variable-types) values stacked on top of each other, which makes it easy to take an item off the top of the stack, while getting to an item deeper in the stack may require taking off multiple other items first.

The order in which elements come off a stack gives rise to its alternative name, LIFO (for last in, first out).
[Queues](#queue-structure) are something like a stack except the processing order is First In First Out (FIFO) rather than LIFO.

An example of the use of a stack is basica's [GOSUB](#gosub) command. When a `GOSUB` command is executed the line number to return to is "pushed" on the top of a stack. When a `RETURN` command is executed the return line number is "popped" off of the stack. This methodology allows `GOSUB` to be nested to any level. Any `RETURN` statement will always return to the line after the last `GOSUB` executed.

There is no fixed limit on the size or number of stacks. You are limited only by the memory of your device.

There are two types of stacks like there are two types of lists or arrays: [string](#variable-types) stacks and [numeric](#variable-types) stacks.

**See also:**
* [Stack Operations](#stack-operations)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# Stack Operations
The following functions can be used to manipulate and manage stacks:
* [STACK.CLEAR](#stack-clear)
* [STACK.CREATE](#stack-create)
* [STACK.ISEMPTY](#stack-isempty)
* [STACK.PEEK](#stack-peek)
* [STACK.POP](#stack-pop)
* [STACK.PUSH](#stack-push)
* [STACK.TYPE](#stack-type)

**See also:**
* [Stack Structure](#stack-structure)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# List Structure
A list is similar to a single-dimension [array](#array-structure). The difference is in the way a list is built and used. An array must be [dimensioned](#array-dimensions) before being used. The number of elements to be placed in the array must be predetermined. You can redimension an array but not easily remove one of its elements, or insert an element somewhere. Lists are much more flexible: a list starts out empty and grows as needed. Elements can be removed, replaced and inserted anywhere within the list.

There is no fixed limit on the size or number of lists. You are limited only by the memory of your device.

Another important difference is that a list is not a [variable type](#variable-types). A numeric [pointer](#pointers) is returned when a list is created. All further access to the list is by means of that numeric pointer. One implication of this is that it is easy to make a list of lists. A list of lists is nothing more than a [numeric](#variable-types) list containing numeric pointers to other lists.

Lists may be copied into new arrays. Arrays may be added to lists.

There are two types of lists like there are two types of arrays: [string](#variable-types) lists and [numeric](#variable-types) lists.

[Queues](#queue-structure), which are a special kind of structure, can be treated by the mean of lists.

**See also:**
* [List Operations](#list-operations)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# List Operations
The following functions can be used to manipulate and manage lists:
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

**See also:**
* [List Structure](#list-structure)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# Array Structure
An array is a group of [string](#variable-types) or [numeric](#variable-types) data sharing the same variable name. In basica, array variable names always finish with brackets, e.g. `item[]` or `string$[]`. The individual values that make up an array are called elements. An element of an array can be used in a statement or expression wherever you would use a regular string or numeric variable. In other words, each element of an array is itself a [variable](#variables).

You can think of an array as a row of boxes, numbered from one to a predetermined number (set with the [DIM](#dim) or [REDIM](#redim) statements). Each box holds a distinct value, which may or may not differ from the values in the other boxes. If you wanted to keep a list of ten animals, you could use a [string array](#string-arrays) called `Animals$[]`. The boxes and their numbers are represented by brackets surrounding a number; for example, `Animals$[5]` represents box number five of the array `Animals$[]`. Thus, if the value held within box number 5 is `"Cat"`, the statement `pet$=Animals$[5]` would place the value `"Cat"` into the variable `pet$`.

Dimensioning a dynamic array with [DIM](#dim) or [REDIM](#redim) also clears each element, unless the [PRESERVE](#redim) option is present. Each element of each numeric array is set to zero; [string arrays](#string-arrays) are set to the null string ("", length zero). Declaring the name and type of an array, as well as the number of its elements, is performed by the DIM statement. For example:

```vb
DIM Animals$[10]
Animals$[5] = "Cat"
```

...creates an array variable `Animals$[]`, consisting of 10 string elements, numbered 1 through 10, and fills its fifth element with the value "Cat". Array `Animals$[]` and a string variable also named `Animals$` are of course separate variables, that is why array variables are always written with their ending brackets `[]` in basica.

**See also:**
* [Array dimensions](#array-dimensions)
* [Subscripts and Segments](#subscripts-and-segments)
* [String arrays](#string-arrays)
* [Internal representation of arrays](#internal-representation-of-arrays)
* [Array operations](#array-operations)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# Array Dimensions
[Arrays](#array-structure) can have more than one index or dimension. An array with two dimensions can be thought of as an array of array. Let’s assume that we wanted to assign a list of three traits to every animal in the list of animals. Such a list for a "Cat" might be "Purrs", "Has four legs" and "Has Tail". We could set up the `Traits$[]` [string array](#string-arrays) to have two dimensions like so:

```vb
DIM Traits$[10, 3]
```

Then we could fill this two-dimension array as such:

```vb
Traits$[5, 1] = "Purrs" ' first index 5 corresponds to "Cat"
Traits$[5, 2] = "Has four legs"
Traits$[5, 3] = "Has Tail"
```

If someone asked what are the traits of cat, we could search `Animals$[index]` until `"Cat"` is found at `index=5`. `index=5` can then be used to access `Traits$[index, 1|2|3]`.
This full working example illustrates what we have been talking so far:

```vb
DIM Animals$[10]
Animals$[5] = "Cat"

DIM Traits$[10, 3] ' 10 animals, 3 traits for each
Traits$[5, 1] = "Purrs"
Traits$[5, 2] = "Has four legs"
Traits$[5, 3] = "Has Tail"

searched$ = "Cat"
FOR index=1 TO 10 ' search all Animals$[]
  IF Animals$[index] = searched$ THEN ' we found "Cat"
    PRINT "Cat found at index "; INT$(index); " of Animals$[]"
    PRINT "These are the three traits of a cat:"
    FOR trait=1 TO 3 ' print all 3 traits for the cat
      PRINT "Traits$["; INT$(index); ", "; INT$(trait); "] = "; Traits$[index, trait]
    NEXT trait
    EXIT FOR ' no need to search for "Cat" anymore -> exit the search loop
  END IF
NEXT index
```

basica arrays can have any number of dimensions of any size: `DIM ComplexArray[10, 20, 5, 3, 9]` is supported (although we really do not recommend using such a complex array).

**See also:**
* [Array structure](#array-structure)
* [Subscripts and Segments](#subscripts-and-segments)
* [String arrays](#string-arrays)
* [Internal representation of arrays](#internal-representation-of-arrays)
* [Array operations](#array-operations)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# Subscripts and Segments
Individual [array](#array-structure) elements are selected with subscripts or index numbers, which are [numeric expressions](#numeric-expressions) within brackets to the right of an array variable's name. For example, `Animals$[3]` and `Animals$[7]` are two of `Animals$[]` 10 elements. The first element of an array always has a subscript value of one, this cannot be changed and it is a fundamental difference with Visual Basic, PowerBasic and FreeBasic. Some examples follow:

```vb
' This DIM statement declares a 10-element array
' with subscript bounds of 1 TO 10.
' You can know the upper bound of the array by
' calling the UBOUND() function.
DIM Animals$[10]
PRINT UBOUND(Animals$[]) ' will print 10.0
```

```vb
' This DIM statement redimensions the array to contain
' 30 elements with subscript bounds of 1 TO 30.
' Another way to know the upper bound of the array is
' to use the ARRAY.LEN statement.
REDIM Animals$[30]
ARRAY.LEN Animals$[], upper
PRINT upper ' will print 30.0
```

You must [DIM](#dim) all arrays before you can use them. This is the same behaviour as other BASIC dialects such as Visual Basic, PowerBasic or FreeBasic. But unlike these dialects, basica only allow you to set the upper limit ([UBOUND](#ubound)) of an array rather than define a range of subscript values.

Some basica commands take an array as an input parameter. If the array is specified with nothing in the brackets (for example `Animals$[]`), then the command reads the entire array.

Most of these commands allow you to limit their operation to a segment of the array by using the notation `Array[start, length]`, where both `start` and `length` are [numeric expressions](#numeric-expressions).

For example, you can write `Animals$[2,3]`. Usually that means "the animal at row 2 and column 3 of a two-dimensional array called Animals$[]". When used to specify an array segment, it has a different meaning: "read only the segment of the Animals$[] array that starts at index 2 and includes 3 elements". Notice that this notation applies only to one-dimensional arrays. See [Internal representation of arrays](#internal-representation-of-arrays) to know why.

Both of the expressions in the `[start, length]` pair are optional. If the `start` value is omitted: `Animals$[,3]` the default starting index is `1`. If the `length` value is omitted: `Animals$[2,]` the default is the whole length of the array (or "upper bound"). If both are omitted: `Animals$[,]` (although this is not recommended for clarity) the default is to use the entire array.

**See also:**
* [Array structure](#array-structure)
* [Array dimensions](#array-dimensions)
* [String arrays](#string-arrays)
* [Internal representation of arrays](#internal-representation-of-arrays)
* [Array operations](#array-operations)

**Examples:**
```vb
DIM Numbers[10]
FOR i=1 TO 10
  Numbers[i] = i
NEXT

ARRAY.AVERAGE Numbers[], avg
PRINT avg ' will display 5.5 (1+2+..+9+10)/10

ARRAY.AVERAGE Numbers[5,3], avg ' restrict to Numbers[5]..Numbers[7] (3 elements)
PRINT avg ' will display 6.0 (5+6+7)/3

ARRAY.FILL Numbers[2,5], 9 ' fill Numbers[2]..Numbers[6] (5 elements) with the value 9.0
ARRAY.AVERAGE Numbers[2,5], avg
PRINT avg ' will display 9.0
```

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# String arrays
The elements of [string](#variable-types) arrays hold strings instead of [numbers](#variable-types). Each string can be a different length. For example `DIM words$[50]` creates a sequence of 50 independent string variables:

```vb
DIM words$[50]
words$[1] = "Daniel likes cats."      ' 18-character string
words$[2] = ""                        ' a null string
words$[3] = "Nicki is a sweet child." ' 23-character string
' assign more array values here
words$[50] = SPACE$(200)              ' 200-character string
```

**See also:**
* [Array structure](#array-structure)
* [Array dimensions](#array-dimensions)
* [Subscripts and Segments](#subscripts-and-segments)
* [Internal representation of arrays](#internal-representation-of-arrays)
* [Array operations](#array-operations)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# Internal representation of arrays
basica stores arrays in row-major order: `A[1,1]` is first (lowest) in memory, then `A[1,2]`, then `A[1,3]`, and so on through all the columns of the array.  After the columns are taken care of, the next row is stored.
Another way to view it is that the first subscript (the row) has the more weight, the following subscripts have smaller weight: `A[ROW_HEAVY, column_light]`.

Consider this snippet:
```vb
ROWS = 2
COLUMNS = 4
DIM A[ROWS, COLUMNS] ' 2D array of dimensions 2 X 4
FOR row = 1 TO ROWS ' 1 to 2
  FOR column = 1 TO COLUMNS ' 1 to 4
    A[row, column] = (row - 1) * 10 + column
  NEXT column
NEXT row
```

Visually this 2-dimension array `A[]` is represented as follows:

          |  column=1   |  column=2   |  column=3   |  column=4
----------|-------------|-------------|-------------|------------
**row=1** | A[1,1] = 1  | A[1,2] = 2  | A[1,3] = 3  | A[1,4] = 4
**row=2** | A[2,1] = 11 | A[2,2] = 12 | A[2,3] = 13 | A[2,4] = 14

In basica internal memory however, `A[]` is similar to a 1-dimension array composed of the following values: `1, 2, 3, 4, 11, 12, 13, 14`.

This can be checked by using `DEBUG` commands to dump the array:

```vb
DEBUG.ON
DEBUG.DUMP.ARRAY A[]
```

...will display `1.0  2.0  3.0  4.0  11.0  12.0  13.0  14.0`.

As [previously seen](#array-dimensions), basica lower boundary value is always `1`.

Upper boundary value can be obtained at run-time via the [UBOUND](#ubound) function or the [ARRAY.LEN](#array-len) statement. Dimensions of an array can be retrieved with the [ARRAY.DIMS](#array-dims) function.

**See also:**
* [Array structure](#array-structure)
* [Array dimensions](#array-dimensions)
* [Subscripts and Segments](#subscripts-and-segments)
* [String arrays](#string-arrays)
* [Array operations](#array-operations)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# Array Operations
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
* [ARRAY.STDDEV](#array-stddev)
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

**See also:**
* [Array structure](#array-structure)
* [Array dimensions](#array-dimensions)
* [Subscripts and Segments](#subscripts-and-segments)
* [String arrays](#string-arrays)
* [Internal representation of arrays](#internal-representation-of-arrays)

Back to [Array, List, Stack and Bundle](#array-list-stack-and-bundle)

<!------------------------------------------------------------------------------->
# Communication Control
The following functions can be used for external communications:
* [Bluetooth Commands](#bluetooth-commands) (sub-group)
* [EMAIL.SEND](#email-send)
* [FTP Commands](#ftp-commands) (sub-group)
* [GRABURL](#graburl)
* [HTTP.POST](#http-post)
* [PHONE.CALL](#phone-call)
* [PHONE.DIAL](#phone-dial)
* [PHONE.RCV.INIT](#phone-rcv-init)
* [PHONE.RCV.NEXT](#phone-rcv-next)
* [SMS.RCV.INIT](#sms-rcv-init)
* [SMS.RCV.NEXT](#sms-rcv-next)
* [SMS.SEND](#sms-send)
* [Socket (TCP/IP) Commands](#socket-tcp-ip-commands) (sub-group)
* [WIFI.INFO](#wifi-info)
* [WIFI.LOCK](#wifi-lock)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Bluetooth Commands
The following commands can be used to communicate with a device by bluetooth:
* [BT.CLOSE](#bt-close)
* [BT.CONNECT](#bt-connect)
* [BT.DEVICE.NAME](#bt-device-name)
* [BT.DISCONNECT](#bt-disconnect)
* [BTREADREADY.RESUME](#btreadready-resume)
* [BT.OPEN](#bt-open)
* [BT.READ.BYTES](#bt-read-bytes)
* [BT.READ.READY](#bt-read-ready)
* [BT.RECONNECT](#bt-reconnect)
* [BT.SET.UUID](#bt-set-uuid)
* [BT.STATUS](#bt-status)
* [BT.WRITE](#bt-write)
* [ON.BTREADREADY](#on-btreadready)

Back to [Communication Control](#communication-control)

<!------------------------------------------------------------------------------->
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

<!------------------------------------------------------------------------------->
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

**See also:**
* [Working with resources](#working-with-resources)
* [Paths explained](#paths-explained)

Back to [Command summary](#command-summary)

<!------------------------------------------------------------------------------->
# Memory Management
The following functions manipulate memory and its allocation/deallocation:
* [ARRAY.COPY](#array-copy)
* [ARRAY.DELETE](#array-delete)
* [ARRAY.DIMS](#array-dims)
* [ARRAY.LOAD](#array-load)
* [AUDIO.LOAD](#audio-load)
* [AUDIO.RELEASE](#audio-release)
* [BUNDLE.CLEAR](#bundle-clear)
* [BUNDLE.CREATE](#bundle-create)
* [DIM](#dim)
* [FONT.CLEAR](#font-clear)
* [FONT.DELETE](#font-delete)
* [FONT.LOAD](#font-load)
* [GLOBAL](#global)
* [GR.BITMAP.CREATE](#gr-bitmap-create)
* [GR.BITMAP.CROP](#gr-bitmap-crop)
* [GR.BITMAP.DELETE](#gr-bitmap-delete)
* [GR.BITMAP.LOAD](#gr-bitmap-load)
* [GR.BITMAP.SCALE](#gr-bitmap-scale)
* [LET](#let)
* [LIST.CLEAR](#list-clear)
* [LIST.CREATE](#list-create)
* [LOWMEMORY.RESUME](#lowmemory-resume)
* [ON.LOWMEMORY](#on-lowmemory)
* [REDIM](#redim)
* [SOUNDPOOL.LOAD](#soundpool-load)
* [SOUNDPOOL.RELEASE](#soundpool-release)
* [SOUNDPOOL.UNLOAD](#soundpool-unload)
* [STACK.CLEAR](#stack-clear)
* [STACK.CREATE](#stack-create)
* [SWAP](#swap)
* [UNDIM](#undim)

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

There is no case in basica variable names: to basica, the variable `gLoP` is the same as the variable `glop` or as the variable `GLOP`.

## Variable Types
basica has only two types of variables: variables that hold numbers and variables that hold strings. Variables that hold strings end with the character "$". Variables that hold numbers do not end in "$".

These are all numeric variable names:
```vb
Age = 20
amount = agE * 2      ' 40
HEIGHT = AMouNT + aGe ' 60
```

And these are all string variable names:
```vb
First_Name$ = "Nicolas"
Street$ = FIRST_name$ + " St."    ' "Nicolas St."
A$ = "Welcome to " + sTReeT$      ' "Welcome to Nicolas St."
```

In technical detail, basica numbers are double-precision 64-bit IEEE 754 floating point numbers. Their range of values is 4.94065645841246544e-324d to 1.79769313486231570e+308d (positive or negative). basica strings are a series of 0 or more bytes (ASCII value 0-255) and can be encoded with different [charsets](#string-encoding), for different uses. By default basica strings can either be UTF-16 `TEXT` strings or ISO-8859-1 `BINARY` buffers.

There are two classes of variables: [Scalars](#scalars) and [Arrays](#arrays).

## Scalars

A scalar is a variable that can hold only one value.
basica variables do not need to be declared (except if you want them [GLOBAL](#global)). This is a big difference with Visual Basic, PowerBasic and FreeBasic: in basica, any new variable name is considered a valid variable.
If you use a numeric scalar without assigning it a value, it has the value 0.0. If you use a string scalar without assigning it a value, its value is the empty string "".

## Arrays

See [Array structure](#array-structure).

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

The `OPEN` statement also provides an optional charset parameter `CHR = charSet$`. This specifies the encoding charset for this file: "UTF-8", "UTF-16" (basica's default), "UTF-16BE", "UTF-16LE", "US-ASCII" or "ISO-8859-1". Since text files consist of text alone, the selected charset is enforced by basica. All data read or written to the file is automatically forced to the selected charset, regardless of the type of variables or expressions used. With binary or zip files, this specification has no effect.

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
**Note that APPEND access is not supported in ZIP mode. This is an Android OS limitation.**

* *fileNum* is a [numeric variable](#variables) destined to store the unique integer value identifying the file.

* *bufferSize* (optional, `BINARY` or `TEXT` modes only) specifies the size of the buffer to be used by basica. The default buffer size, if not specified, is the whole size of the file to `OPEN`. Changing *bufferSize* is an advanced technique that you will rarely need to use. You should only do it when the file is very large, to avoid Out Of Memory errors. In this case you should use a smaller buffer size (minimum size available is 8096 bytes) and move the **BOF**/**SOF** carret (**B**eginning/**S**tart **O**f **F**ile) accordingly. See [SETBOF](#setbof)/[SETSOF](#setbof) statements.

* *charSet$* (optional, `TEXT` mode only) is a string expression specifying the charset encoding to be used. Default is "UTF-16". You can choose among: "UTF-8", "UTF-16", "UTF-16BE", "UTF-16LE", "US-ASCII" and "ISO-8859-1". See [String encoding](#string-encoding).

**Restrictions:**
Attempting to `OPEN` a file for `READ` that does not exist returns a *fileNum* of `0`. It is always a good idea to test that *fileNum* is true (not zero) before proceeding to do read or write operations.

If you try to `OPEN` a nonexistent file for `WRITE` or `APPEND`, a new file is automatically created. For this reason, Internet files may only be opened in `READ` mode.

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
  PRINT "Zip I/O ok"
END SUB  ' end procedure Zip IO

CALL TextWrite()
CALL TextAppend()
CALL TextRead()
CALL BinaryIO()
CALL ZipIO()
```

<!------------------------------------------------------------------------------->
# RETURN (disambiguation)
See:
* [GOSUB/RETURN](#gosub)
* [RETURN result{$}](#function) in a FUNCTION

<!------------------------------------------------------------------------------->
# ITERATE (disambiguation)
See:
* [ITERATE DO](#do) to iterate a DO/{LOOP} UNTIL loop
* [ITERATE FOR](#for) to iterate a FOR/NEXT loop
* [ITERATE WHILE](#while) to iterate a WHILE/WEND loop

<!------------------------------------------------------------------------------->
# INPUT (disambiguation)
See:
* [INPUT](#input) to input text from the console
* [INPUT.BOX](#input-box) to show a box-input (notepad) dialog
* [INPUT.LINE](#input-line) to show a line-input dialog
* [LINE INPUT](#line-input) to read a line from a TEXT file

<!------------------------------------------------------------------------------->
# END (disambiguation)
See:
* [END](#end) to end the current program and display the console
* [END FUNCTION](#function) to end a FUNCTION declaration
* [END IF](#if-end-if-block) to end an IF block
* [END SELECT](#select-case) to end a SELECT CASE block
* [END SUB](#sub) to end a SUB declaration

<!------------------------------------------------------------------------------->
# EXIT (disambiguation)
See:
* [EXIT](#exit) to exit the program and go back to the Home screen
* [EXIT DO](#do) to exit a DO/UNTIL loop
* [EXIT FOR](#for) to exit a FOR/NEXT loop
* [EXIT FUNCTION](#function) to exit a FUNCTION
* [EXIT SUB](#sub) to exit a SUB
* [EXIT WHILE](#while) to exit a WHILE/WEND loop

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
TODO

**See also:**
* [PERMISSION](#permission-statement)

<!------------------------------------------------------------------------------->
# INSTR function
**Purpose:**
Search a [string](#variable-types) for the existence of a second string.

**Syntax:**
> y = INSTR( {*Position*,} *main$*, *sub$* )

**Remarks:**
`INSTR` returns the position of *sub$* within *main$* starting at *Position*. `INSTR` has a (clearer) refactor: the [IS_IN](#is_in-function) function.

Appart from the different name and order of parameters, `INSTR` behaves exactly the same as `IS_IN`, so please refer to the [IS_IN](#is_in-function) function for details of use.

**See also:**
* [IS_IN](#is_in-function) (refactor)
* [JOIN](#join) and [JOIN.ALL](#join-all)
* [LCASE$](#lcase) and [UCASE$](#ucase)
* [LEFT$](#left), [RIGHT$](#right) and [MID$](#mid)
* [SPLIT](#split) and [SPLIT.ALL](#split-all)
* [TALLY](#tally)
* [TRIM$](#trim), [LTRIM$](#ltrim) and [RTRIM$](#rtrim)
* [WORD$](#word)

**Examples:**
```vb
e$ = "abc123def456def456abc123"
PRINT "e$ = " + e$
p$ = "1  4  7  0  3  6  9  2"
PRINT "     " + p$

i = INSTR(e$, "def")
PRINT "INSTR(e$, \"def\") = " + INT$(i)

i = INSTR(-1, e$, "def")
PRINT "INSTR(-1, e$, \"def\") = " + INT$(i)

i = INSTR(6, e$, "3")
PRINT "INSTR(6, e$, \"3\") = " + INT$(i)

i = INSTR(7, e$, "3")
PRINT "INSTR(7, e$, \"3\") = " + INT$(i)

i = INSTR(-1, e$, "3")
PRINT "INSTR(-1, e$, \"3\") = " + INT$(i)

i = INSTR(-2, e$, "3")
PRINT "INSTR(-2, e$, \"3\") = " + INT$(i)
```

<!------------------------------------------------------------------------------->
# IS_IN function
**Purpose:**
Search a [string](#variable-types) for the existence of a second string.

**Syntax:**
> y = IS_IN( sub$, main$ {,*Position*} )

**Remarks:**
`IS_IN` returns the position of *sub$* within *main$*. The return value is indexed to `1`, while `0` means "not found". `IS_IN` is a more easy-to-read refactor of [INSTR](#instr-function) because it complies with basica's second [dogma](#dogmata):

> the command names should always indicate the order of the parameters

`IS_IN(sub$, main$)` must be read "IS `sub$` IN `main$` ?".
The answer is either "no" (`IS_IN` returns `0`) or "yes" (`IS_IN` returns the index of the match.)

`IS_IN(sub$, main$, Position)` must be read "IS `sub$` IN `main$`, STARTING AT `Position` ?".

* *Position* specifies the character position to begin the search. If *Position* is `1` or greater, *main$* is searched left to right. The value `1` starts at the first character, `2` the second, etc. If *Position* is `-1` or less, *main$* is searched from right to left. The value `-1` starts at the last character, `-2` the second to last, etc. If *Position* is not given, the default value of `+1` is assumed.

```vb
x = IS_IN("y", "xyz")  ' returns 2.0
x = IS_IN("a", "xyz")  ' returns 0.0
a$ = "My Dog" : b$ = " "
x = IS_IN(b$, a$)      ' returns 3.0
```

**It is important to note that in all cases, even when *Position* is negative, the return value of `IS_IN` is the absolute position of the match, from left to right, starting with the first character.**

`IS_IN` is case-sensitive, meaning that upper-case and lower-case letters must match exactly in *sub$* and *main$*. If you want to do a case-**in**sensitive search, use `IS_IN(LCASE$(sub$), LCASE$(main$))`.

**Restrictions:**
Special search terms are evaluated in this sequence:

1. If *Position* is zero, or beyond the length of *main$*, the value `0` is returned.
2. If *main$* is an empty string `""`, the value `0` is returned.
3. If *sub$* is an empty string `""`, the absolute *Position* value (default of `1`) is returned.

**See also:**
* [INSTR](#instr-function) (legacy)
* [JOIN](#join) and [JOIN.ALL](#join-all)
* [LCASE$](#lcase) and [UCASE$](#ucase)
* [LEFT$](#left), [RIGHT$](#right) and [MID$](#mid)
* [SPLIT](#split) and [SPLIT.ALL](#split-all)
* [TALLY](#tally)
* [TRIM$](#trim), [LTRIM$](#ltrim) and [RTRIM$](#rtrim)
* [WORD$](#word)

**Examples:**
```vb
e$ = "abc123def456def456abc123"
PRINT "e$ = " + e$
p$ = "1  4  7  0  3  6  9  2"
PRINT "     " + p$

i = IS_IN("def", e$)
PRINT "IS_IN(\"def\", e$) = " + INT$(i)

i = IS_IN("def", e$, -1)
PRINT "IS_IN(\"def\", e$, -1) = " + INT$(i)

i = IS_IN("3", e$, 6)
PRINT "IS_IN(\"3\", e$, 6) = " + INT$(i)

i = IS_IN("3", e$, 7)
PRINT "IS_IN(\"3\", e$, 7) = " + INT$(i)

i = IS_IN("3", e$, -1)
PRINT "IS_IN(\"3\", e$, -1) = " + INT$(i)

i = IS_IN("3", e$, -2)
PRINT "IS_IN(\"3\", e$, -2) = " + INT$(i)
```
