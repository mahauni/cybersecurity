LFI and RFI

for this exploit, you will need to check if is possible to hack in the servidor
first, check if is exploitable with the ../../../etc/passwd, for that you will need a ? in the url. in the commands you can see a example.

after that you will need to gobuster and see if you can find the place where the some files you can send to the servidor, so like any upload.

after that and you find the place to upload the files with the gobuster, you will then enter in the kali /etc/share/webshells and you will find the possible webshells that you can explooit.

you can see possibly what the server is running by try and error, or try the burpsuite and maybe its there some kinda of clue.

anyway, after sending the webshell to the server and changing the parameters in the file you send, you will open and listen to a port in your computer, and after that you will enter in the server if you go the place where you read the file passwd
and instead of reading the passwd file you go to the file you just upload where you found the uploads folder and with the knowledge of which Apache or somehting else you can execute the shell and connect to the server.

after entering is just exploit and try to go up the permissions chain to a root user or something.
