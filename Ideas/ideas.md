* (DONE) ~~Update cors unblocker to recent chrome version~~
* DLL that tampers with all call instructions in a program and re-routes the calls to a sub-routine. Had this working a while ago with bugs.
  * There's a couple issues with this. You can take two approaches (1) Scan for calls, replace calls. (2) Scan for function headers, replace with jmp. WIth method number (1) you might think it's easy just look for calls, until you find out that there can be 8 different call instructions (https://c9x.me/x86/html/file_module_x86_id_26.html). This is almost fine - for most of those you can still edit and replace to call near memory injected functions that return back, but then you have call functions like like "call [eax]" which is hard to rewrite.
  * So then it makes sense to use method 2 - just have a smart way way to scan for methods in the assembly and hook at the beginning. At the beginning of most functions have something like this which takes about 6 bytes 

```asm
func:
  push rbp
  mov rbp, rsp 
```

Which you can then replace with this, which should take 5 bytes (accorording to chatgpt at leasst for a near call with 3 byte address which should be enough)

```asm
newFunc:
  ;; do what you need to here - logging or whatever 
  ;; remove evidence of stack or function call here so that original function returns into caller 
  call originalFunc
  

func:
  call newFunc
```

Probably should work

* Kernal level cheat driver 
* explore wave function collapse
* revamp website, include blogging/articles from cdn
* Hold down on a word to replace it with a simpiler word
* OpenTK (OpenGL) C# Minecraft remake + game engine 
* Your own encryption, even if it's not the best
* redact.local
* C compiler that allows procedures to be compiled in a way where procedures and accessed memoery addresses are continiously changing memory locations & minipulating stack and addressing so that the program becomes very difficult to debug - probably would be cool for hiding what you're program/process/function is doing. (right now I'm imaging a circular chain of functions that are constantly re-writing each other, and if new call to new function then that joins the chain... idk probably might be something worth expanding on)
* Redo Resume page - Take inspiration from how this pasge is layed out https://tokio.rs/
* VS Code plugin/addon to make it so you can just change the color on a filter so you dont have to use the online generator stuffs, btw that online generator stuff is also open source so look at that https://github.com/angel-rs/css-color-filter-generator
* Interesting. For function call tracking / Tracking EIP/RIP. Hardware Performance Monitoring. Intel has LBR (records to registers) or HBR (records to memory). Cool tool: https://github.com/marcusbotacin/BranchMonitoringProject.
* I'm learning Neural Network stuffs and I want a tool to visualize exactly whats happening in a Neural network. Tool to visualize and make / create NNs
* A tool that'll give you a journey thorughout the day, go to cafe 1 spend 30$ then go to another for lunch, library, everything for some duratoin of time
* App where you can see everyone on a map that is also using the app, and you use it to find people that want to chill/hang/meet up around your location. Maybe you can tap on people on that map and send them a message "Hey want to hang out", our you can put up a status for people that see you on the map "I'm currently looking for poeple to go hiking with next this to thib mountain here".

## New

* Alt-tab THAT DOESNT SUCK. Tried many alternatives nothing is good. Need simple search like VS Code's CTRL+P, only tabs to opened tabs unles you do something like start the search with > or #
