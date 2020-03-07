# MySQL Installations


Install requirements

- Microsoft Visual C++ 2013, 2019

### Install ZIP Package

1. my.ini
2. admin cmd, $ mysqld --initialize --user=mysql --console
3. root, password.
4. add mysql to path
5. admin cmd, $ mysqld install MySQL --defaults-file="D:\Tools\Databases\mysql-5.7.22-winx64\bin\my.ini"
6. reopen admin cmd, $ net start mysql
7. $ mysql -u root -p 
8. $ set password = password('new password')
9. template password not right.
   			

### uninstall from zip package

1. $ net stop mysql #stop service

```
$ sc delete mysql # remove service
```

2. Control panel, uninstall mysql
3. remove mysql folder. show hidden files and folders

```
C:\Program Files\MySQL
C:\Program Files (x86)\MySQL
C:\ProgramData\MySQL
And if exists, delete it too
C:\Users\[User-Name]\AppData\Roaming\MySQL
```

4. restart your pc and reinstall MySQL.	