<span style = "font-family: Calibri">
## Packet Tracer Activity 2.3.7
## Aim: Navigate the IOS

### Objectives:
#### Part 1: Establish Basic Connections, Access the CLI and Explore Help
##### Step 1: Connect PC1 to S1 using a console cable
a. Click the **Connections** icon (the one that looks like a lightnigh bolt) in the lower left corner of the Packet Tracer window.
b. Select the light blue Console calbe by clicking it. The mouse pointer will change to what appears to be a connector with a cable dangling from it.
c. Click **PC1**. A window displays an option for an RS-232 connection. Connect the cable to the RS-232 port.
d. Drag the other end of the console connection to the S1 switch and click the switch to access the connection list.
e. Select the **Console** port to complete the connection.

##### Step 2: Establish a terminal session with S1.
a. Click **PC1** and then select the **Desktop** tab.
b. Click the **Terminal** application icon. Verify that the Port configuration default settings are correct.
*What is the setting for bits per second?*
# TODO: ADD ANSWER HERE
c. The screen thet appears may have several messages displayed. Somewhere on the screen there should be a **Press RETURN to get started!** message. Press ENTER.
*What is the prompt displayed on the screen?*
# TODO: ADD ANSWER HERE

##### Step 3: Explore the IOS Help.
a. The IOS can provide help for commands depending on the level accessed. The prompt currently displayed is called **User EXEC**, and the device is waiting for a command. The most basic form of help is to type a question mark (**?**) at the prompt to display a list of commands
```
S1> ?
```
*Which command begins with the letter 'C'?*
# TODO: ADD ANSWER HERE
a. At the prompt, type **t** and then a question mark (**?**).
```
S1> t?
```
*Which commands are displayed?*
# TODO: ADD ANSWER HERE
At the prompe, type **te** and then a question mark (**?**).
```
S1> te?
```
*Which commands are displayed?*
# TODO: ADD ANSWER HERE
This type of help is known as context-sensitive help. It provides more information as the commands are expanded.

#### Part 2: Explore EXEC Modes
##### Step 1: Enter privileged EXEC mode.
a. At the prompt, type the question mark (**?**).
```
S1> ?
```
*What information is displayed for the enable command?*
# TODO: ADD ANSWER HERE
b. Type **en** and press the **Tab** key.
```
S1> en<Tab>
```
*What displays after pressing the Tab key?*
# TODO: ADD ANSWER HERE
This is called command completion (or tab completion). When part of a command is typed, the **Tab** key can be used to complete the partial command. If the characters typed are enough to make the command unique, as in the case of the **enable** command, the remaining portion of the command is displayed.
*What would happen if you typed **te\<Tab\>** at the prompt?*
# TODO: ADD ANSWER HERE
c. Enter the **enable** command and press ENTER.
*How does the prompt change?*
# TODO: ADD ANSWER HERE
d. When prompted, type the question mark (**?**).
```
S1# ?
```
One command starts with the letter ‘C’ in user EXEC mode.
*How many commands are displayed now that privileged EXEC mode is active? (**Hint**: you could type c? to list just the commands beginning with ‘C’.)*
# TODO: ADD ANSWER HERE

##### Step 2: Enter Global Configuration mode.
a. When in privileged EXEC mode, one of the commands starting with the letter ‘C’ is **configure**. Type either the full command or enough of the command to make it unique. Press the **/<Tab/>** key to issue the command and press ENTER.
```
S1# configure
```
*What is the message that is displayed?*
# TODO: ADD ANSWER HERE
b. Press Enter to accept the default parameter that is enclosed in brackets **/[terminal/]**.
*How does the prompt change?*
# TODO: ADD ANSWER HERE
c. This is called global configuration mode. This mode will be explored further in upcoming activities and labs. For now, return to privileged EXEC mode by typing *end*, *exit*, or *Ctrl-Z*.
```
S1(config)# exit
S1#
```

#### Part 3: Set the Clock
##### Step 1: Use the clock command.
a. Use the **clock** command to further explore Help and command syntax. Type **show clock** at the privileged EXEC prompt.
```
S1# show clock
```
*What information is displayed? What is the year that is displayed?*
# TODO: ADD ANSWER HERE
b. Use the context-sensitive help and the **clock** command to set the time on the switch to the current time. Enter the command **clock** and press ENTER.
```
S1# clock<ENTER>
```
*What information is displayed?*
# TODO: ADD ANSWER HERE
c. The `% Incomplete command` message is returned by the IOS. This indicates that the **clock** command needs more parameters. Any time more information is needed, help can be provided by typing a space after the command and the question mark (**?**).
```
S1# clock ?
```
*What information is displayed?*
# TODO: ADD ANSWER HERE
d. Set the clock using the **clock set** command. Proceed through the command one step at a time.
```
S1# clock set ?
```
*What information is being requested?*
# TODO: ADD ANSWER HERE
*What would have been displayed if only the **clock set** command had been entered, and no request for help was made by using the question mark?*
# TODO: ADD ANSWER HERE
e. Based on the information requested by issuing the **clock set ?** command, enter a time of 3:00 p.m. by using the 24-hour format of 15:00:00. Check to see if more parameters are needed.
```
S1# clock set 15:00:00 ?
```
The output returns a request for more information:
```
<1-31> Day of the month
MONTH Month of the year
```
f. Attempt to set the date to 01/31/2035 using the format requested. It may be necessary to request additional help using context-sensitive help to complete the process. When finished, issue the **show clock** command to display the clock setting. The resulting command output should display as:
```
S1# show clock
*15:0:4.869 UTC Tue Jan 31 2035
```
g. If you were not successful, try the following command to obtain the output above:
```
S1# clock set 15:00:00 31 Jan 2035
```

##### Step 2: Explore additional command messages.
a. The IOS provides various outputs for incorrect or incomplete commands. Continue to use the **clock** command to explore additional messages that may be encountered as you learn to use the IOS.
b. Issue the following commands and record the messages:
```
S1# cl<tab>
```
*What information was returned?*
# TODO: ADD ANSWER HERE
```
S1# clock
```
*What information was returned?*
# TODO: ADD ANSWER HERE
```
S1# clock set 25:00:00
```
*What information was returned?*
# TODO: ADD ANSWER HERE
```
S1# clock set 15:00:00 32
```
*What information was returned?*
# TODO: ADD ANSWER HERE

### Topology Used:
![](2.3.7.png)

### Switch CLI:
#### Part 1:
```
Press RETURN to get started!
 
 
 
S1>?
Exec commands:
  connect     Open a terminal connection
  disable     Turn off privileged commands
  disconnect  Disconnect an existing network connection
  enable      Turn on privileged commands
  exit        Exit from the EXEC
  logout      Exit from the EXEC
  ping        Send echo messages
  resume      Resume an active network connection
  show        Show running system information
  ssh         Open a secure shell client connection
  telnet      Open a telnet connection
  terminal    Set terminal line parameters
  traceroute  Trace route to destination
S1>t?
telnet  terminal  traceroute  
S1>te?
telnet  terminal
```

#### Part 2:
```
S1>?
Exec commands:
  connect     Open a terminal connection
  disable     Turn off privileged commands
  disconnect  Disconnect an existing network connection
  enable      Turn on privileged commands
  exit        Exit from the EXEC
  logout      Exit from the EXEC
  ping        Send echo messages
  resume      Resume an active network connection
  show        Show running system information
  ssh         Open a secure shell client connection
  telnet      Open a telnet connection
  terminal    Set terminal line parameters
  traceroute  Trace route to destination
S1>en
S1>enable 
S1#?
Exec commands:
  clear       Reset functions
  clock       Manage the system clock
  configure   Enter configuration mode
  connect     Open a terminal connection
  copy        Copy from one file to another
  debug       Debugging functions (see also 'undebug')
  delete      Delete a file
  dir         List files on a filesystem
  disable     Turn off privileged commands
  disconnect  Disconnect an existing network connection
  enable      Turn on privileged commands
  erase       Erase a filesystem
  exit        Exit from the EXEC
  logout      Exit from the EXEC
  more        Display the contents of a file
  no          Disable debugging informations
  ping        Send echo messages
  reload      Halt and perform a cold restart
  resume      Resume an active network connection
  setup       Run the SETUP command facility
  show        Show running system information
  ssh         Open a secure shell client connection
  telnet      Open a telnet connection
  terminal    Set terminal line parameters
  traceroute  Trace route to destination
  undebug     Disable debugging functions (see also 'debug')
  write       Write running configuration to memory, network, or terminal
```
#### Part 3:
```
S1#cconfigure 
S1#configure 
S1#configure terminal 
Enter configuration commands, one per line.  End with CNTL/Z.
S1(config)#exit
S1#
%SYS-5-CONFIG_I: Configured from console by console
 
S1#show clock
*10:33:21.111 UTC Mon Mar 1 1993
S1#clock
% Incomplete command.
S1#clock ?
  set  Set the time and date
S1#clock set ?
  hh:mm:ss  Current Time
S1#clock set 15:00:00 ?
  <1-31>  Day of the month
  MONTH   Month of the year
S1#clock set 15:00:00 31?
<1-31>  
S1#clock set 15:00:00 31 ?
  MONTH  Month of the year
S1#clock set 15:00:00 31 Jan ?
  <1993-2035>  Year
S1#clock set 15:00:00 31 Jan 2035
S1#show clock
15:0:2.193 UTC Wed Jan 31 2035
S1#cl
S1#cl
S1#clock
% Incomplete command.
S1#clock set 25:00:00
             ^
% Invalid input detected at '^' marker.
	
S1#clock set 15:00:00 32
                      ^
% Invalid input detected at '^' marker.
	
S1#
```

---
</span>
