# kitty-password
Password manager for kitty

macOS ships with a great password manager called KeyChain which happens to have an cli tool. This tool, `security`, allows the user to create keychains and passwords as well as grab passwords from it.

### Requirements
kitty>
fzf>
macOS>


## Creating a keychain and populating it
Albeit the general system keychain could be used with this script, the most convenient way would be to create a specific keychain for kitty. Let's do it:
```bash
security create-keychain -P kitty.keychain
```
this will prompt for a password to protect the keychain. 

Then we need to populate the keychain, which can also be done within the command line
```bash
 security add-generic-password -a USER_NAME -s PASSWORD_NAME -w PASSWORD kitty.keychain
```
> Remeber, in order for this command to not enter in your shell history you should preppend it with a blank space.


## Using this kitten

To use this plugin we should just download the python file
```bash
wget -O ~/.config/kitty/kittens/password.py FILL
```

We create a mapping in our `~/.config/kitty/kitty.conf` file
```conf
map cmd+BACKSLASH kitten kittens/password.py security find-generic-password -w -l
```
