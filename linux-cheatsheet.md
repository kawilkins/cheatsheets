Linux Cheatsheet
===============

# Table of Contents
- [User Management](#User-Management)
- [SSH Key Generation](#SSH-Key-Generation)

# User Management 

## Add & remove a user

Let us add a user.

```bash
useradd -m username
```

This will add a user with a home directory.  Replace `username` with the username of your choice.

For login screens where seeing a users actual name instead of their username is desired add a `-C` as follows:

```bash
useradd -m username -C "Full Name"
```

The option `-C` denotes that we are commenting the user as their proper name.
Replace `Full Name` with the desired or proper name of the user.

## Adding a user to a group

```bash
usermod -aG group username
```

This command modifies a user to be joined to a group (i.e. sudo).
Replace `group` and `username` with the desired group and username.

## User password

```bash
passwd username
```

This command modifies the password for the user.
You will be prompted for the new user password.

To set a temporary password that will force the user to change their password upon logging in for the first time after setting the password:

```bash
chage -d 0 username
```

What this command does is use the `-d` flag/option to set the age limit of the password to `0`.
This effectively causes the password to immediately expire.
When the user logs in with the password, they will be prompted to change their password.

## Change user type

It is entirely possible to change a user from a "regular" user to a system user.
For example, you might have a system administrator user account that you don't want shown on the login page.
As super user:

```bash
cd /var/lib/AccountsService/users/
```

Edit the file that corresponds with the user you are editing.
The boolean value of `SystemAccount` is by default set to false.

# SSH Key Generation

## ED25519

```
ssh-keygen -t ed25519
```

## RSA

```
ssh-keygen -t rsa -b 4096
```

## Explanation

The above examples will create a SSH key of either type (ED25519 or RSA).
The commands will introduce a prompt which will ask you to name the file of the SSH key.
Some users may prefer to have a separate key generated, but it is not required.
However, checking with your system administrator regarding the specific SSH key policy or practice for your organization is a good idea.

Additionally, you may use the `-C` flag to comment each SSH key.
Some network resources or online services may require or recommend a comment.
