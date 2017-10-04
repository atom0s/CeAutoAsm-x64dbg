# CeAutoAsm-x64dbg
An x64dbg plugin that allows users to execute Cheat Engine auto assembler scripts within x64dbg.

**Donations:** [Donate via Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=7U7Q2GRT6KUJN)

**Note: At this time, this plugin only supports the 32bit version of x64dbg!**

# Overview

The CeAutoAsm plugin is a wrapper around a mini-project of mine, ceautoasm.dll.

ceautoasm.dll is Cheat Engine's internal auto assembler ripped out into a standalone library that can be used pretty much 
anywhere in a Windows environment. ceautoasm.dll uses the latest Cheat Engine code base for its internal workings with as
minimal changes to the original code as needed to make it work. 

Some features of the auto assembler and internals have been removed to limit file size and ease of use.

**Removed Features (General)**
 * All ARM / JNI / Unix / Mono features removed.
 * All Lua features are removed.
 * All driver/kernel level features removed.
 * All DBVM features removed.
 * Structure / Extended debug information resolving removed. (May restore later.)

**Removed Features (Auto Assembler Engine)**
 * Prologues _[Removed due to not using Lua/Plugin features.]_
 * Commands _[Removed due to not using Lua/Plugin features.]_
 * Plugins _[Removed due to not using Lua/Plugin features.]_
 * INCLUDE() macro. _[Removed due to overhead/bloat. May be restored later.]_
 * KALLOC() macro. _[Removed due to not using kernel features.]_
 * LOADLIBRARY() macro. _[Removed due to overhead/bloat. Lot of code changes required to work with this library.]_
 * LUACALL() macro. _[Removed due to not using Lua features.]_
 * REASSEMBLE() macro. _[Removed due to requiring unwanted UI related things / disassembler engine.]_

# Features

CeAutoAsm implements the following commands for x64dbg:

**ceautoasm.getaddress [parsable_string]**
  * Parses a Cheat Engine based string that can be interpreted as an address.

**ceautoasm.goto [parsable_string]**
  * Parses a Cheat Engine based string that can be interpreted as an address and goes to it in the CPU window.

**ceautoasm.script.enable [script_name]**
  * Executes the enable section of the given script.

**ceautoasm.script.disable [script_name]**
  * Executes the disable section of the given script. 
  

Scripts should be stored within a folder named cescripts within the main directory of the x64dbg path. 

For example, if using x32dbg.exe:
```
x32dbg Path : C:\Tools\x64dbg\release\x32\x32dbg.exe
Scripts Path: C:\Tools\x64dbg\release\x32\cescripts\
```

Within the cescripts folder, you will need to create sub-folders named the same 
name as the file you are debugging. For example, if I am debugging calc.exe, then
my scripts for calc.exe will be placed in:
```
C:\Tools\x64dbg\release\x32\cescripts\calc.exe\<scripts here>
```
# Installation

Here is a quick rundown of installing this plugin:

  * Download this repository via the 'Download Zip' feature of Github.
  * Extract the contents of the zip to your desktop.
  * Open your x64dbg install folder.

Copy the x32 and x64 folders from the extracted zip over the x64dbg folder.

If done properly, Windows should ask you to overwrite at least the plugins folder.

# Credits, Thanks, Links

 * atom0s - Main coder of the plugin, ceautoasm.dll project. 
   * Site: [atom0s.com](http://atom0s.com)
 * Dark Byte - For Cheat Engine in general.
   * Site: [https://github.com/cheat-engine/cheat-engine](https://github.com/cheat-engine/cheat-engine)
 * x64dbg
   * Site: [https://x64dbg.com](https://x64dbg.com)
   * Code: [https://github.com/x64dbg/x64dbg](https://github.com/x64dbg/x64dbg)