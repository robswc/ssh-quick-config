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

## Dependencies

The `sshqc` script requires an additional piece of software.

### sshpass
sshpass is a utility designed for running ssh using the mode referred to as "keyboard-interactive" password authentication, but in non-interactive mode.
#### Ubuntu
```
apt-get install sshpass
```
#### OS X
- [Requires xcode and command line tools](http://guide.macports.org/chunked/installing.xcode.html)
- Requires homebrew
The following is an unofficial brew package (warning, may not be up-to-date!)
```
brew install https://raw.githubusercontent.com/kadwanev/bigboybrew/master/Library/Formula/sshpass.rb
```

## Usage

### Basic
To use `sshqc` simply supply it, via `|` (pipe) with `name===host===password;` pairs.  Where `name` is the of the server/host, `host` is the host (i.e. user@192.168.0.10) and `password` is the password for the **host** user. 

```bash
echo "MyServer===rob@192.168.0.10===MySecretPass007!" | sudo ./sshqc
```

The above command will:

- Log into your server, using the provided credentials.
- Copy the server's public key, saving it to `~/.ssh/name.key`.
- Add the local user's public key to the server's `authorized_keys` file.
- Generate a block of code in your `~/.ssh/config`, allowing you to connect with `ssh name`

### Advanced

```bash
cat servers.txt | sudo ./sshqc
```

The above command will do the same things as the basic, except it will instead be reading the server credentials from a text file.
The format of the text file should be:

```
MyServer1===rob@192.168.0.11===MySecretPass007!;MyServer2===rob@192.168.0.12===MySecretPass007!
```

All the server pairs _must_ be on one line, seperated by a `;` - or else the script will not work.