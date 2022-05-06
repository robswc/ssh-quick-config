# ssh-quick-config
Quickly and easily generates your SSH config file and handles ssh keys.

# Installation

Installation can be done in one of two ways.

The first is to simple use `wget` to download the latest version from GitHub.

```
sudo wget https://raw.githubusercontent.com/robswc/upreq/main/upreq
```

or, to make things easier

```
sudo wget https://raw.githubusercontent.com/robswc/upreq/main/upreq;sudo mv upreq /bin;sudo chmod +x /bin/upreq
```

The above set of commands will download via `wget`, move the file into your `/bin` and set the nessesary permissions.  This allows you to call `sshqc` anywhere.

### Dependencies

The `sshqc` script requires two additional pieces of software
