# Ideas 

Here are just a list of some ideas that I want to work on in the future. 

* Doom style game, no engine, Clang or my own programming language once complete.
* Spotify join friends listening session
* GPT from the ground up
* Brimstone Lineup bruteforcer
* Chrome extension to hide youtube videos
* DLL that tampers with all call instructions in a program and re-routes the calls to a sub-routine
* JS inside CSS file
* My own frontend JS framework
* CSS Sucks - make a new styling language and use javascript to do everything inside a canvas, who cares about performance.
* Electronic chessboard with arduino
* Analyze twitch dbd videos and spit out player statistics
* OCR nutrition information and feed it into GPT model to find key product information (calories, protein, sugars, ect)
* Dreambooth version of GPT that is designed for fine-tuning on a codebase / repo.
* Kernal level cheat driver 
* Sleep analysis android app
* (In-Progress) GPT-powered 3d room generator
* Tool to easily train a gpt model on a github repo / codebase; maybe tool to auto-document functions once GPT understands the codebase
* Chrome extension when you highllight a word, it highlights all matches on the same page (basically CTRL+C, CTRL+F, CTRL+V shortcut)
* With kernal access, there must be some way to hook to some internal windows function to constantly monitor EIP/RIP without attaching to a process via debugging (as that doesnt work very well). Do this to somehow work out which functions are being called in a process at any particular time.
  * Might want to read more @ https://learn.microsoft.com/en-us/windows/win32/procthread/scheduling
  * Reading https://devblogs.microsoft.com/pix/analyzing-stalls-and-context-switches-in-timing-captures/ seems like hooking to context switches might not work as they are not garanteed to switch on every EIP/RIP increment. Very likely not to be possible as once a context switch happens, windows unlikely to call any more functions and just lets the cpu move onto next instructions. Maybe look into forcing context switches as much as possible and then hooking onto the context switches?
  * Seems like maybe the only way to do this is setting a thread to priority 31 and hope the tread runs fast enough to check the EIP/RIP of other process threads but I'm not happy with this solution. 
  * Might work by reducing the speed of other CPUs, and increasing the speed of one particular CPU and somehow dedicating that one CPU to reading EIP/RIP of other process threads. (doesnt work) 
  * Seems possible to do this by flooding windows with a massive amount of threads with REALTIME_PRIORITY_CLASS (31) which would all check for a target threads RIP/EIP, while also setting the target thread to lowest possible priority while keeping it running. The more threads you have running, the less chance one of them will but put to sleep, so you can always have at least one thread monitoring the target thread.
  * REALLY doesnt seem like anything is going to work here. Might just need to live-edit x86 instructions in a process and re-route all call instructions to nearby (or absoltue jumps) jmp chains which leads to a my custom logging function. Will work on this. This should also work on games even with anti-cheats probably, even if we just set this up so it logs out into a buffer in its own memory space and read the buffer via kernal or usermode.
