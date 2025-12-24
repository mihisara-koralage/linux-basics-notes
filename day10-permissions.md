# Day 10 – Linux Users and Permissions

## Linux Users
Linux is a multi-user operating system. Each file and process belongs to a user.

- root – Superuser with full system access
- Normal users – Limited permissions
- Service users – Used to run applications and services

Command used:
- whoami – Shows the current user
- /etc/passwd – Contains user information

---

## Linux Groups
Groups are used to manage permissions for multiple users.

- Users can belong to one or more groups
- Permissions can be assigned to a group instead of individual users

Commands used:
- groups – Shows groups of the current user
- /etc/group – Lists all groups

Groups are commonly used in DevOps for:
- Web servers
- CI/CD tools
- Docker access

---

## File Permissions
File permissions define who can read, write, or execute a file.

Example:
```text
-rwxr-xr--  ```

Meaning:

- First character: file type (- file, d directory)
- rwx – Owner permissions
- r-x – Group permissions
- r-- – Others permissions

Permission types:

- r – read
- w – write
- x – execute

Command used:

- ls -l – View file permissions

##chmod – Change Permissions

Used to modify file permissions.

Symbolic method:
- chmod u+x script.sh

Numeric method:
- chmod 755 script.sh

Numeric meaning:

- 7 = read + write + execute
- 5 = read + execute
- 4 = read only

Executable scripts must have execute permission.

- chown – Change Ownership

Used to change file owner and group.

Example:

- sudo chown user:group file.txt

This is important when:

- Applications cannot access files
- Deployments fail due to permission issues

##Why Permissions Matter in DevOps

Permissions are critical in DevOps because:

- Incorrect permissions can break deployments
- Services may fail to start
- Security risks can occur if permissions are too open
- Understanding permissions helps prevent production issues.

##What I Practiced

- Checking file permissions
- Changing permissions using chmod
- Changing file ownership using chown
- Understanding how permissions affect execution
