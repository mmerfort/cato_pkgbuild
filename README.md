# Cato PKGBUILD

## How to install

Check out the repository and build it.

```shell
git clone https://github.com/mmerfort/cato_pkgbuild
cd cato_pkgbuild
makepkg -si
```

Next, set the account and user in /etc/cato/client.json which is only readable by root.

## Prerequisites for authentication

Just starting the Systemd service does not work. It is required to run Cato once via the command-line.

```
mkdir /tmp/cato
cd /tmp/cato
sudo cato_client --user <user> --account <account>
sudo mv cato_password.cfg /etc/cato/cato_password.cfg
```

## Using Cato

After moving the password file, you can start and enable the service.

```
systemctl --now enable cato_client.service
```

You will need to provide the MFA key again.

```
cato_client --mfa-login
```
