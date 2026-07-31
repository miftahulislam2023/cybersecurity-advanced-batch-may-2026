# Today's Topics
- Pipelines (cat, sort, uniq, grep, head, tail, tee)
  - grep (global regular expression print) -> pattern searching using regular expression
    - -v -> invert match
    - -n -> line number
    - -c -> count
    - -r -> recursive search
  - tail -> show last lines
  -  -f -n -> follow tail
  - head -> show first lines
  - tee -> simultaneously output to file and screen
- cURL & wget
- User and Group Management
  - sudo su -> log in as root
  - exit -> exit from user
  - id -> print uid, gid, group
  - /etc/shadow -> password file (encrypted password)
  - /etc/passwd -> user information
  - /etc/group -> group information
  - getent passwd miftah
  - man 5 passwd

## /etc/passwd - The 7 Columns of `/etc/passwd`

The `/etc/passwd` file stores essential account information for Linux/Unix systems. Each line represents a user account, with information separated into seven distinct fields.

| Column | Field Name          | Description                                                                                                                                       | Example              |
| :----- | :------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------ | :------------------- |
| **1**  | **Username**        | The login name used by the user to access the system.                                                                                             | `jdoe`               |
| **2**  | **Password**        | Historically held the encrypted password. Today, it usually displays an `x` to indicate that the actual hash is securely stored in `/etc/shadow`. | `x`                  |
| **3**  | **User ID (UID)**   | A unique numeric ID assigned to identify the user to the operating system (e.g., `root` is always `0`).                                           | `1001`               |
| **4**  | **Group ID (GID)**  | The numeric ID of the user's primary group.                                                                                                       | `1001`               |
| **5**  | **Comment (GECOS)** | Optional descriptive information, often containing the user's full name, office number, or phone contact.                                         | `John Doe, Room 402` |
| **6**  | **Home Directory**  | The absolute path to the user's home folder.                                                                                                      | `/home/jdoe`         |
| **7**  | **Login Shell**     | The default command-line interpreter assigned to the user upon login (e.g., `/bin/bash` or `/sbin/nologin` for non-interactive system accounts).  | `/bin/bash`          |

---

### Example Entry

```text
jdoe:x:1001:1001:John Doe, Room 402:/home/jdoe:/bin/bash
```

## Structure of `/etc/shadow`

The `/etc/shadow` file securely stores encrypted user passwords and password aging policies. It is readable only by the `root` user to protect password hashes from offline brute-force attacks.

Fields are separated by colons (`:`):

| Column | Field Name             | Description                                                                     | Example     |
| :----- | :--------------------- | :------------------------------------------------------------------------------ | :---------- |
| **1**  | **Username**           | The account login name (matches `/etc/passwd`).                                 | `jdoe`      |
| **2**  | **Encrypted Password** | The password hash (prefixed with `$id$` for algorithm), or `!` / `*` if locked. | `$6$xyz...` |
| **3**  | **Last Changed**       | Date of last password change (days since Jan 1, 1970 UTC).                      | `19800`     |
| **4**  | **Minimum Age**        | Minimum number of days required before the password can be changed.             | `0`         |
| **5**  | **Maximum Age**        | Maximum number of days the password remains valid.                              | `90`        |
| **6**  | **Warning Period**     | Number of days before password expiration that the user is warned.              | `7`         |
| **7**  | **Inactivity Period**  | Days after expiration before the account is completely disabled.                | `14`        |
| **8**  | **Expiration Date**    | Absolute account expiration date (days since Jan 1, 1970).                      | `20100`     |
| **9**  | **Reserved**           | Reserved field for future use (currently unused).                               | *(empty)*   |

### Example Entry (`/etc/shadow`)
```text
jdoe:$6$qZ8xK9pL$V4m...:19800:0:90:7:14:20100:
```


## Structure of `/etc/group`

- Group name
- Password
- GID
- User list

### Example Entry (`/etc/group`)
```text
eng:x:1001:jdoe,asmith,bchen
```
