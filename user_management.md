# 🧠 1. Types of Users in Linux
---
### Linux systems have three main types of users:

| Type                       | Description                                                                                                                             | Example                   |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| **Root user**              | Superuser with full administrative privileges.                                                                                          | `root`                    |
| **System users**           | Created by the OS or services (e.g., `daemon`, `www-data`, `mysql`). They typically have no login shell and manage background services. | `www-data`, `syslog`      |
| **Regular (normal) users** | Created for human users. Have home directories and login shells.                                                                        | `john`, `admin`, `devops` |


## ➤ UID ranges (from /etc/login.defs)

| UID Range | Type                       |
| --------- | -------------------------- |
| 0         | Root                       |
| 1–999     | System users               |
| 1000+     | Regular users (by default) |


## 📁 2. Important Files Related to User Management

| File                   | Purpose                                                                |
| ---------------------- | ---------------------------------------------------------------------- |
| `/etc/passwd`          | Stores basic user account info (username, UID, GID, home, shell).      |
| `/etc/shadow`          | Stores encrypted passwords and password aging info. (root-only access) |
| `/etc/group`           | Stores group information (group name, GID, members).                   |
| `/etc/gshadow`         | Stores secure group passwords.                                         |
| `/etc/login.defs`      | Default settings for user creation (UID range, password aging, etc.).  |
| `/etc/default/useradd` | Default values used when creating users (home dir, shell, etc.).       |
| `/etc/skel/`           | Template directory copied into a new user’s home directory.            |


### 🧩 Example: /etc/passwd

Each line represents one user.
```
john:x:1001:1001:John Doe:/home/john:/bin/bash
```
| **Fields (colon-separated):**												          	              |				
| ----------------------------------------------------------------------------- |
| 1. `john`		 		  | username												                          |
| 2. `x`		 		    | password placeholder (actual password in /etc/shadow)     |
| 3. `1001` 	 		  | UID													                              |
| 4. `1001`		 		  | primary GID											                          |
| 5. `John Doe`	 		| comment (GECOS field)									                    |
| 6. `/home/john` 	| home directory										                        |
| 7. `/bin/bash` 		| login shell											                          |

### 🧩 Example: /etc/shadow
> The /etc/shadow is a text-based password file. The shadow file stores the hashed passphrase (or “hash”) format for Linux user account with additional properties related to the user password. This shadow file is directly accessible only to the root user.

```
john:$6$salt$encryptedhash:19500:0:99999:7:::
```
1. `Username` : A valid account name, which exist on the system.
2. `Password` : Your encrypted password is in hash format. The password should be minimum 15-20 characters long including special characters, digits, lower case alphabetic and more. Usually password format is set to $id$salt$hashed, The $id is the algorithm prefix used On GNU/Linux as follows
    - `$1$` is MD5
    - `$2a$` is Blowfish
    - `$2y$` is Blowfish
    - `$5$` is SHA-256
    - `$6$` is SHA-512
    - `$y$` is yescrypt
3. `Last password change (lastchanged)` : The date of the last password change, expressed as the number of days since Jan 1, 1970 (Unix time). The value 0 has a special meaning, which is that the user should change her password the next time she will log in the system. An empty field means that password aging features are disabled.
4. `Minimum` : The minimum number of days required between password changes i.e. the number of days left before the user is allowed to change her password again. An empty field and value 0 mean that there are no minimum password age.
5. `Maximum` : The maximum number of days the password is valid, after that user is forced to change her password again.
6. `Warn` : The number of days before password is to expire that user is warned that his/her password must be changed
7. `Inactive` : The number of days after password expires that account is disabled.
8. `Expire` : The date of expiration of the account, expressed as the number of days since Jan 1, 1970.

### 🧩 Example: /etc/default/useradd

**Example content:**
```
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/bash
SKEL=/etc/skel
CREATE_MAIL_SPOOL=yes
```
> Defines default behavior for useradd.


### 🧩 Example: /etc/login.defs

```
UID_MIN 1000
UID_MAX 60000
GID_MIN 1000
GID_MAX 60000
PASS_MAX_DAYS 99999
PASS_MIN_DAYS 0
PASS_WARN_AGE 7
```
> Defines system-wide limits and password aging policy.

### 3. The /etc/skel Directory

This directory contains template files copied into a new user’s home directory when created with -m.

**Example contents:**
```
/etc/skel/
├── .bash_logout
├── .bashrc
└── .profile
```
---

# 👤 User Management Commands

## ➤ Create User

### Syntax
```
useradd <options> username
```

#### Create user
```
useradd john
```
#### With options:
```
useradd -m -d /home/john -s /bin/bash -c "John Doe" john
```

| Option | Description                          |
| ------ | ------------------------------------ |
| `-m`   | Create home directory                |
| `-d`   | Specify home directory path          |
| `-s`   | Specify login shell                  |
| `-c`   | Comment (user’s full name)           |
| `-e`   | Account expiration date (YYYY-MM-DD) |
| `-u`   | Specify custom UID                   |
| `-g`   | Primary group                        |
| `-G`   | Add to secondary groups              |

#### Set password
```
passwd username
```




