# shell_totp
![gif](https://i.imgur.com/AJ63BuV.gif)

Shell script to show time-based one-time passwords - TOTP. It's like Google Authenticator on a TTY. You execute `tokens` command and view your 2FA codes with a countdown timer.

If `xclip` or `xsel` are installed you can copy a token to clipboard pressing its correspondig key. Paste with the middle button of mouse.

Press `0` (zero) to exit.
```
1) Facetter  : 379139       5) Linkblr   : 963558       9) Tindapp   : 964093
2) Gitgle    : 924596       6) Redck     : 590364       a) Tumbdn    : 895673
3) Goohub    : 447944       7) Sladit    : 761259       b) Twibook   : 323023
4) Instachat : 048232       8) Snapgram  : 865829       c) Whatsder  : 612359

0) Exit

   Remaining :     26 ::::::::::::::::::::::::::....  2018-06-03 11:51:04
```

## Install
It depends on `oathtool` package. You must install it first, like the example below for Debian based distros.
```
$ sudo apt install oathtool
```
Copy the `tokens`, `tokdec` and `tokenc` files to a PATH directory and make them executable.
```
$ cp tokens tokdec tokenc ~/bin/
$ chmod +x ~/bin/tokens ~/bin/tokdec ~/bin/tokenc
```
Copy the `.tokensrc` setup file to your home directory.
```
$ cp .tokensrc ~/
```
It is recommended to also install `xclip` or `xsel` so you can copy tokens to clipboard.
```
$ sudo apt install xclip
```
```
$ sudo apt install xsel
```

## Configure
Create a secrets file like the provided sample one, with a name and a secret at each line, separated by a space.
```
Facetter FFFFFFFFFFFFFFFF
Gitgle GGGGGGGGGGGGGGGG
Goohub HHHHHHHHHHHHHHHH
Instachat IIIIIIIIIIIIIIII
Linkblr LLLLLLLLLLLLLLLL
Redck EEEEEEEEEEEEEEEE
Sladit DDDDDDDDDDDDDDDD
Snapgram SSSSSSSSSSSSSSSS
Tindapp RRRRRRRRRRRRRRRR
Tumbdn TTTTTTTTTTTTTTTT
Twibook BBBBBBBBBBBBBBBB
Whatsder WWWWWWWWWWWWWWWW
```
Edit the `~/.tokensrc` configuration file, adjusting the variables `secretsfile` and `barstyle` according to your setup.

The variable `secretsfile` contains the path and name of the secrets file above, like the excerpt below.
```
secretsfile=~/bin/tokens.secrets
```
You can play with the variable `barstyle` too, if you dare.
```
barstyle='#_'
```
Finally, it's not a bad idea to give some privacy to your secrets file.
```
$ chmod 0600 ~/bin/tokens.secrets
```

## Encrypt
To really protect your secrets file nothing better than encrypt it. The `tokenc` command does this and removes the original secrets file. The next time you run `tokens` it will ask for the passphrase you entered during the encryption.

Later, if you need to add or update your secrets, first decrypt the `tokens.secrets.cipher` with the `tokdec` command. After edit the `tokens.secrets` encrypt it again as before.

## Troubleshoot
Remember that the clock of the system must be correct.

Currently, there is a limit of 61 tokens.

Do not forget the passphrase used during encryption. There are no means to recover it.

## Fun fact
At most of the time this software was written and tested using [Termux](https://termux.com/) on Android.

That's it!
