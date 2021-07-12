# Python for Windows

## Problems

### 1. pip command not found

**Error Info**

Run pip xxx in CMD

```
C:\Python34> pip install Django
'pip' is not recognized as an internal or external command,
operable program or batch file.
```

Run pip xxx in git bash 

```
pip command not found
```

**Solutions**

**You need to add the path of your pip installation to your PATH system variable**. By default, pip is installed to `C:\Python34\Scripts\pip` (pip now comes bundled with new versions of python), so the path "C:\Python34\Scripts" needs to be added to your PATH variable.

To check if it is already in your PATH variable, type `echo %PATH%` at the CMD prompt.

**To add the path of your pip installation to your PATH variable**, you can use the Control Panel or the `setx` command. For example:

```
setx PATH "%PATH%;C:\Python34\Scripts"
```

### 2. ValueError: check_hostname requires server_hostname

Solution:

关掉网络代理

