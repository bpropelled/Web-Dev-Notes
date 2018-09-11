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

## Netstat

Netstat is a useful tool for checking network and Internet connections. Some useful applications for the average PC user are considered, including checking for malware connections. 

* * *
* * *

## Syntax and switches

The command syntax is ` netstat [-a] [-b] [-e] [-f] [-n] [-o] [-p proto] [-r] [-s] [-t] [-v] [interval]` A brief description of the switches is given in Table I below. Some switches are only in certain Windows versions, as noted in the table.._Note that switches for Netstat use the dash symbol "-" rather than the slash "/"_. 

| ----- |
|  Switch |  Description |  
|  -a |  Displays all connections and listening ports |  
|  -b |  Displays the executable involved in creating each connection or listening port. (Added in XP SP2.)  |  
|  -e |  Displays Ethernet statistics |  
|  -f |  Displays Fully Qualified Domain Names for foreign addresses. (In Windows Vista/7 only) |  
|  -n |  Displays addresses and port numbers in numerical form |  
|  -o |  Displays the owning process ID associated with each connection |  
|  -p proto |  Shows connections for the protocol specified by proto; proto may be any of: TCP, UDP, TCPv6, or UDPv6. |  
|  -r |  Displays the routing table |  
|  -s |  Displays per-protocol statistics |  
|  -t |  Displays the current connection offload state, (Windows Vista/7) |  
|  -v |  When used in conjunction with -b, will display sequence of components involved in creating the connection or listening port for all executables. (Windows XP SP2, SP3) |  
|  [interval] |  An integer used to display results multiple times with specified number of seconds between displays. Continues until stopped by command _ctrl+c_. Default setting is to display once,  | 

## Applications of Netstat

Netstat is one of a number of command-line tools available to check the functioning of a network. ([See this page][10] for discussion of other tools.) It provides a way to check if various aspects of TCP/IP are working and what connections are present. In Windows XP SP2, a new switch "-B" was added that allows the actual executable file that has opened a connection to be displayed. This newer capability provides a chance to catch malware that may be phoning home or using your computer in unwanted ways on the Internet. There are various ways that a system administrator might use the assortment of switches but I will give two examples that might be useful to home PC users. 

### Checking TCP/IP connections

TCP and UDP connections and their IP and port addresses can be seen by entering a command combining two switches:  `netstat -an` An example of the output that is obtained is shown in Figure 1. 

| ----- |
| ![Output for sample netstat command][34] [ ![Pin it!][35] ][36] ![Share on Facebook][37]  | 

The information that is displayed includes the protocol, the local address, the remote (foreign) address, and the connection state. Note that the various IP addresses include port information as well. An explanation of the different connection states is given in Table II>

| ----- |
|  State |  Description |  
|  CLOSED |  Indicates that the server has received an ACK signal from the client and the connection is closed  |  
|  CLOSE_WAIT  |  Indicates that the server has received the first FIN signal from the client and the connection is in the process of being closed  |  
|  ESTABLISHED |  Indicates that the server received the SYN signal from the client and the session is established |  
|  FIN_WAIT_1  |  Indicates that the connection is still active but not currently being used  |  
|  FIN_WAIT_2  |  Indicates that the client just received acknowledgment of the first FIN signal from the server  |  
|  LAST_ACK  |  Indicates that the server is in the process of sending its own FIN signal  |  
|  LISTENING  |  Indicates that the server is ready to accept a connection  |  
|  SYN_RECEIVED  |  Indicates that the server just received a SYN signal from the client  |  
|  SYN_SEND  |  Indicates that this particular connection is open and active  |  
|  TIME_WAIT  |  Indicates that the client recognizes the connection as still active but not currently being used  | 

### Checking for malware by looking at which programs initiate connections

To find out which programs are making connections with the outside world, we can use the command `netstat -b` (Note that for Windows Vista/7, this particular switch requires that the command prompt have elevated privileges.) Actually, it is better to check over a period of time and we can add a number that sets the command to run at fixed intervals. Also, it is best to create a written record of the connections that are made over some period of time. The command can then be written `netstat -b 5 >> C:connections.txt` Note that as written, this command will run with five-second intervals until stopped by entering "_Ctrl+c_", which is a general command to exit. (Some reports say that this can be fairly CPU intensive so it may cause a slower, single-core machine to run sluggishly. It was not noticeable on my dual-core machine.) A simple example of the type of output is shown in Figure 2. Note that the Process ID (PID) is given when using Windows XP. In Windows Vista/7, the switch "o' has to be added to display PIDs. This command can be combined with other tools such as [Task Manager][38] to analyze what executable files and processes are active and are trying to make Internet connections.

| ----- |
| ![][39] [ ![Pin it!][35] ][36] ![Share on Facebook][37]  | 

### Windows XP batch program to check connections and terminate automatically 

The previous example of using "netstat -b" to check connections at intervals has the disadvantage that it requires manual termination. It is also possible to use a batch file that runs a specified number of times with a given time interval and then terminates automatically. In Windows XP we can make use of a command from the [Windows 2003 Server Tools][20] called "Sleep". A possible batch file is: `@echo off  
echo Checking connections  
for /L %%X in (1,1,100) do (netstat -b >> C:connections.txt)&&(sleep 5)  
` This particular example does 100 iterations of the_ netstat_ command at 30 second intervals and writes the results to a file _C:connections.txt_. By using different combinations of the switches in Table I, the type of output can be varied

# Setup Persistent Aliases & Macros in Windows Command Prompt (cmd.exe) using DOSKey

> Saved from Archive.org, Date: May 14, 2010 Author: Jesse Webb

http://web.archive.org/web/20140330024520/http://devblog.point2.com/2010/05/14/setup-persistent-aliases-macros-in-windows-command-prompt-cmd-exe-using-doskey/

Our development machines here at Point2 are not standardized; we have a mixture of Windows XP, 7, and Mac OSX/Unix computers. I find myself constantly switching back and forth between command prompt interfaces when pair programming. As a result, I catch myself using “ls” to list a directories contents regardless of what system I am on. I am currently using a Windows XP machine for my developer box and I wanted to setup an alias to the “ls” command to actually perform a “dir”. Here is how I accomplished it…

There is a command available in a Window’s shell that let’s you “alias” command to whatever you please: DOSKey. It allows you to create “macros” to execute one or more other commands with a custom name. If you open up a command prompt and type in the following, you will now be able to use “ls” to list the current directory’s contents.

```
DOSKEY ls=dir
```

It also handles command line arguments, either by index or as a collection using $1 – $2 or $* respectively. This allows you to do things perform a “dir” command every time you change directories. This example would be done with the following macro definition.

```
DOSKEY cd=cd $1$Tdir
```

This all sounds very simple and easy until you close your command prompt, open a new one, and realize all of these macros you defined earlier did not persist between instances. The DOSKey command does not save these alias automatically. The DOSKey command does support saving the “currently defined macros” to a file which will allow you to run a simple command in any new shell to load macros from any saved file. The problem is, I already forget to use “dir” instead of “ls” so I know for sure I will not remember to run a certain DOSKey command every time I open up a new command prompt. I needed something more automatic.

I investigated what options I have for running commands as part of every run of cmd.exe. I found out there is a command line argument, \K, that I can use on cmd.exe to tell it to run a ‘.cmd’ or ‘.bat’ file to run commands on startup. So you can run something like to following command to load a shell instance with the following command file being ran automatically.

```
cmd.exe /K C:\path\to\file.cmd
```

This allows you to add all of the commands you want into that file and have them run automatically for the command prompt you are about to open. In order to pass this argument, I created a shortcut to cmd.exe in my Quick Launch toolbar which I could modify and use exclusively for my command prompt instances. This can easily be done by going into your C:\WINDOWS\system32 directory, right-clicking on cmd.exe and selecting “Send to Desktop”. Right click on the newly created shortcut (on your desktop) and select “Properties”. On the Shortcut tab, you will find the “Target” field which you will have to modify to include the command line option. Here is what my configuration looks like:

![](http://i.imgur.com/zKohiXR.jpg)

The only other thing from my configuration worth mentioning is the “Start in” setting I have specified. The value “%HOMEDRIVE%%HOMEPATH%” will open the command prompt in your user’s home directory as opposed to the default which opens the new window in the system32 directory which usually isn’t very helpful.

My doskey.cmd file is also worth taking a look at. It only currently has a few alias for common Unix commands but it will give you a good idea of what kind of things are capable.

```
@echo off

DOSKEY ls=dir
DOSKEY cd=cd $1$Tdir
DOSKEY clear=cls
```

It is probably best to also include the “@echo off” at the top of your script too just so you don’t have to see the noise in the shell running your script. There are also a lot more powerful features to DOSKey that I have yet to experiment with but you can see how easy it is now to add permanent macros into your command prompt.

Another thing worth noting is that you should look at the other tabs in the cmd.exe Shortcut Properties window because it makes it easy to do things like increase the buffer size of text for the shell, change font sizes and color, as well configure the behavior of command history tracking. After tweaking with all these settings, here is my new custom, improved Command Prompt:

![](http://i.imgur.com/0j8Ff7s.jpg)

The only “gotcha” here is that you have to open command prompt window using the Shortcut but there are other tools available which will let you run Shortcuts a simple keystroke so this should not be an issue. I hope this makes every Window’s Command Prompt user’s life a little easier. :)