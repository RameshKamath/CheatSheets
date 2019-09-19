# **ssh Cheat Sheet File**

>**Note:** replace `<objectNames>` with objects.
# Client side
`ssh <serverUsername>@<serverAddress>` - connects to ssh enabled/listening `Server` in given `<serverAddress>` with given `<serverUsername>` .

## Login from client side.

* when client is connecting to ssh Server, the server looks in `<serverUserName>/.ssh/authorized_keys` file for public key of the client.

    > when connecting for first time ssh prompts to store the servers as known host in clients `.ssh/known_hosts` file.

* If key pair or Public key of client is not available in server's `authorized_keys` file. Then ssh prompts client for `serverUsername`'s Password.

* when client terminal is logged into server the terminal's user name changes to `<serverUsername>@<serverAddress>`


# Server side
`sshd` - For server side ssh that listen for client ssh requests.


---

# Key Generation
`ssh-keygen` - generates private and public key pair.

> **Note:** This command will give options to select `File Name` to save the key, add passphrase.

when key pair is generated:

* The file with just `File Name` is the private key.
* The file with `File Name` with `.pub` extension is the public key.

    >**Note:** ***Public key*** is given to server and stored in "`<ServerUserName>/.ssh/authorized_keys/`" folder.

    > ***Private key*** is stored with client in "`<userName>/.ssh/`" folder.

## Using new Identity(***private key***) on ssh
> private key from "`<userName>/.ssh/id_rsa`" is used automatically.

if new key pair login doesn't work then use:

`ssh-add <privateKey>` - This will add private key as new identity to ssh.

---
# Other commands
## Secure file copy from client to server
`scp <clientFile> <serverUsername>@<serverAddress>:<serverFile>` - copy's file from client to Server securely.

## Adding public key to server with one command
```bash
cat ~/.ssh/<publicKeyFilename>.pub | ssh <serverUsername>@<serverAddress> "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```
---

# ssh Server Configuration

## sshd_config file location

`/etc/ssh/sshd_config`           - For linux(ubuntu).

`%programdata%/ssh/sshd_config`  - For windows.

## Important things to disable in server sshd_config
```
PermitRootLogin no
PasswordAuthentication no
```
> **Note:** After this Reload `sshd`

---

Go to [open-ssh](https://www.openssh.com/) to know more.