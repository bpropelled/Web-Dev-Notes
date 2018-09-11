## Console Notes

### Make the console output look nice
- to make the console nice looking with CSS, do the following
```js
console.log('%c a colorful message', 'background: green; color: white; display: block;');
```

### Make an empty file from cmd
```cmd
echo > test.txt
```

this will mkae a file with one line "Echo is on"
to make this an empty file just do this
```cmd
echo.> test.txt
```

or add items into it bby putting them before the ">"

```cmd
echo hey this is cool > test.txt
```

## Stylish Console Logs
You can style the text you display via console.log() with CSS. Just stick “%c” at the beginning of your string, then add a second string parameter for the CSS. Like so:
```cmd
console.log('%cHey, look at me, being all fancy and stuff!', 'font-size: 26px; font-weight: bold; color: purple;')
```


## CMD CHEAT SHEET

[Source](http://simplyadvanced.net/blog/cheat-sheet-for-windows-command-prompt/ "Permalink to Cheat Sheet for Windows Command Prompt")

# Cheat Sheet for Windows Command Prompt

I got bored today, found some command line links that I had and decided to read them all. The following is my command prompt reference in case I forget any of it. This can also be used as a how-to guide if you are new to the Windows command line. You can open the your program and start testing out the features. Just make sure you don't accidentally delete anything important.  
Here's the results: (if you are new to this, then first see cd and dir)  
Feel free to leave feedback!

 

#### To open the Windows command prompt you may do one of the following:

* Click Start -> Programs -> Accessories -> Command Prompt
* Click Start (or hit the Windows key), type "cmd" in search, then hit [ENTER]
* Windows Key + R (#r, not the pound symbol) brings up Run. Then type "cmd" then [ENTER]
* SHIFT + right-click in any folder or desktop, then select "open command window here"

## **Basic Command Prompt Commands**

x /? = provides syntax info and complete list of all parameters for x (a command, like "cd")  
cd = change directory  
cd .. = move to the parent directory  
cd = move to the root of current drive  
cd x = move to the currentx directory  
cd z: = change to the z root directory (as opposed to c:)  
copy x y = copy file x to directory y (Ex: D:gamesgalaga.exe C:programs[awesome.exe]), [] = optional  
copy file con = display file contents in console  
copy con file.txt = create text file in the console window, end with ctrl+z (^z or F6)  
date = change the date  
del = delete/erase  
del x = deletes all files/folders fitting x  
del . = deletes all files within current directory  
del *.* = deletes all files within current directory  
dir = display contents of current directory (Ex: dir [c:][programs]), [] = optional  
dir *.txt = list all .txt files in current directory  
dir *.? = list all files with extensions one character in length in current directory  
dir /w /p *.* = display all contents one screen at a time  
dir | more = display all contents one line at a time  
dir /? = provides syntax info and complete list of all dir parameters  
echo = send command line input to display (by default)  
echo sometext » somefile.txt = append line(s) of text to any file  
echo sometext > somefile.txt = overwrites file with sometext  
erase = delete/erase  
exit = exit the command prompt  
filename.txt = opens filename.txt in current directory in Notepad (or default .txt program)  
format z: = format z drive [Ex: use to format a disc or flash drive]  
mkdir x = make directory x in current directory  
move x y = more or rename x to y  
q = escapes sequential display of contents (i.e. the more parameter)  
rd x = remove/delete directory x if it's empty  
ren x y = rename file x to y  
time = change the time  
type file = display the contents of the file 'file' (displays file contents in console)  
type file |more = display the contents one line at a time

## **Advanced Command Prompt Commands**

ipconfig [/all] = display network adapter information (advanced)  
netstat –n = display local address and addresses you are connected to (advanced)  
netstat –nb = above with name of foreign addresses (advanced) (this shows your private IP, if you are behind a router or proxy, then your public IP address will be different)  
ping google.com = how long it takes for your computer to talk to google.com  
_**_

## **Convert output of one process into the input of another process**

Send contents of script.js to the system debug.exe file:  
type script.js | c:programs]debug.exe  
programsdebug.exe < script.js

## **Send directory listing to a printer or file**

dir > prn (theoretically to a printer)  
dir > somefile.txt  
dir *.mp3 > c:UsersDanDesktopmusiclist.txt = print all .mp3 files in current directory to musiclist.txt

## **Customize the DOS command prompt**

prompt /? = display prompt options  
prompt $p$g = display current directory followed by a greater-than symbol (Windows default)  
prompt $p$g$t = display time after the default prompt  
prompt [%computername%][%username%] $g = display computer name followed by username  
prompt = reset prompt to default

color 0a = change prompt color to matrix green and screen color to black  
color 84 = change colors to red on grey  
0 = black  
1 = blue  
2 = green  
3 = cyan  
4 = red  
5 = magenta  
6 = yellow  
7 = white  
8 = grey  
9 = bright blue  
a = bright green  
b = bright cyan  
c = bright red  
d = bright magenta  
e = bright yellow  
f = bright white

## **Modify any file extension associations**

[assoc .extension=fileType]  
assoc /? = prints this information  
assoc = display list of current file extensions recognized by your computer (any fileType value may be used)  
assoc > fileextensions.txt = print list to somefile.txt in current directory  
assoc .txt = displays current file association of .txt (.docx, .html, .zip, .htaccess, assoc textfile, et cetera)  
assoc .txt= = will delete the association for the given file extension

File Extension Tips/Ideas:  
\- Windows by default doesn't know the following extensions, but check anyways with "assoc .", "assoc .htaccess" and "assoc .xml" anyways just to be sure. If the extension is defined already, then you may not need to change it.  
assoc .=txtfile = associate extensionless files with Notepad  
assoc .htaccess=txtfile = associate nameless .htaccess files with Notepad  
assoc .xml=txtfile = associate XML files with Notepad

## **Miscellaneous**

Acceptable characters: A-Z a-z 0-9 $ # & @ ! ( ) – { } ' ` _ ~  
Unacceptable characters: | < > ^ + = ? / [ ] " ; , * : %

? = wildcard for any single character  
* = wildcard for any/all characters/files  
> = redirects output to (overwrite) a file or device  
» = redirects output to (append to) a file or device  
< = directs data from a file or device to a program or device  
« = directs additional data from a file or device to a program or device  
nul = black hole

### **Environmental Variables via the DOS command prompt**

* System-generated upon Windows startup:  
%DATE% = Tue 08/02/2011  
%TIME% = 14:23:33.37  
%SYSTEMROOT% = C:Windows  
%COMPUTERNAME% = DAN-PC
* System-generated upon user login:  
%USERNAME% = Dan  
%USERDOMAIN% = Dan-PC
* Local machine variables for all users:  
%PATH% = C:Windowssystem32  
%HOMEPATH% = UsersDan  
%HOMEDRIVE% = C:  
(Hint: Use echo)

### **Function Keys**

F1 = Sequential, individual repeat of previously entered characters  
F2 = Copies any number of characters from the previous command line  
F3 = Repeats the contents of the previous command line  
F4 = Deletes any number of characters from the previous command line  
F5 = Return to the previous command line  
F6 = Enters the characters ^z (CTRL+z), indicating "end of file"  
F7 = Displays a history of command-line entries for the current session (50-line cache)  
F8 = Sequentially displays previous command-line entries  
F9 = Enables user to recall previous command lines by number (0 = first line)

  ## Create an Alias or setup CMD or BAT file to run on CMD startup everytime
you may make the alias(es) persistent with the following steps,

1. Create a .bat or .cmd file with your DOSKEY commands.
2. Run regedit and go to HKEY_CURRENT_USER\Software\Microsoft\Command Processor
3. Add String Value entry with the name AutoRun and the full path of your .bat/.cmd file.

For example, %USERPROFILE%\alias.cmd, replacing the initial segment of the path with %USERPROFILE% is useful for syncing among multiple machines.

This way, every time cmd is run, the aliases are loaded.

For completeness, here is a template to illustrate the kind of aliases one may find useful.
```cmd
@echo off

:: Temporary system path at cmd startup

set PATH=%PATH%;"C:\Program Files\Sublime Text 2\"

:: Add to path by command

DOSKEY add_python26=set PATH=%PATH%;"C:\Python26\"
DOSKEY add_python33=set PATH=%PATH%;"C:\Python33\"

:: Commands

DOSKEY ls=dir /B
DOSKEY sublime=sublime_text $*  
    ::sublime_text.exe is name of the executable. By adding a temporary entry to system path, we don't have to write the whole directory anymore.
DOSKEY gsp="C:\Program Files (x86)\Sketchpad5\GSP505en.exe"
DOSKEY alias=notepad %USERPROFILE%\Dropbox\alias.cmd

:: Common directories

DOSKEY dropbox=cd "%USERPROFILE%\Dropbox\$*"
DOSKEY research=cd %USERPROFILE%\Dropbox\Research\
```
Note that the $* syntax works after a directory string as well as an executable which takes in arguments. So in the above example, the user-defined command dropbox research points to the same directory as research.
As Rivenfall pointed out, it is a good idea to include a command that allows for convenient editing of the env.cmd file. See alias above. If you are in a cmd session, enter cmd to restart cmd and reload the env.cmd file.

### What is a batch file?
These are simple text files containing some lines with commands that get executed in sequence, one after the other. These files have the special extension BAT or CMD. Files of this type are recognized and executed through an interface (sometimes called a shell) provided by a system file called the command interpreter. In Windows XP/ Vista the command interpreter is the file cmd.exe. The large assortment of versatile commands available in Windows XP/Vista/7 makes batch files a powerful tool.
Constructing a batch file consists of nothing more than opening any text editor like the accessory Notepad, entering some lines containing commands, and saving the file with an extension BAT or CMD. (The CMD extension is limited to newer Windows systems and is not recognized in Windows 9x/Me systems. In Windows XP, Vista, and 7 there is little practical difference between the two extensions.) Don't use Wordpad or Word unless you are very careful to save all files in pure text format. The commands themselves are often quite simple and there is no need to learn a programming language. Those who wish can explore the intricacies that are available with branching and looping but here I will confine the discussion to some straightforward application to everyday tasks. The focus will be on saving time and effort for some routine stuff like system housekeeping and simple file management.

Running a batch file is a simple matter of clicking on it. Batch files can also be run in a command prompt or the Start-Run line. In that case, the full path name must be used unless the file's path is in the path environment.

### Constructing a batch file
In the following discussion it is assumed that the Introductory page and the page on Commands have been read.
The first line in a batch file often consists of this command
**@echo off**
By default, a batch file will display its commands as it runs. The purpose of this first command is to turn off this display. The command "echo off" turns off the display for the whole script, except for the "echo off" command itself. The "at" sign "@" in front makes the command apply to itself as well. This nuance isn't really all that important in the context here but I mention it because it is often seen in scripts. The scripts we will discuss are very brief and omitting this line won't make any great difference. However, as a matter of good practice, we will enter it in our scripts.