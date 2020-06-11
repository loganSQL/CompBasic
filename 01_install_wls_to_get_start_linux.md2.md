# 1. [Install WLS](https://medium.com/@gmusumeci/linux-on-windows-totally-how-to-install-wsl-1-and-wsl-2-307c9dd38a36)
* Please use the powershell (Administrator)
##1. Check Windows 10 Build #
* We need to run Windows Build 16215 or later to install WSL 1
```
systeminfo | Select-String "^OS Name","^OS Version"
```
* If not 16215 above, update it https://www.microsoft.com/en-ca/software-download/windows10

##2. install WSL 1
* check whether WSL is enabled
```
Get-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
* if not, enable WSL
```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
##3. restart 
* Then, restart our computer when it is asked.

##4. Installing a Linux Distro on WSL
* download from https://docs.microsoft.com/en-us/windows/wsl/install-manual
or 
* using Microsoft Store to install a Linux Distro (Ubuntu 18.04)

##5. Run the installer
* first time install, if you manually download and unzip to directory
```
ubuntu.exe 
```

##6. subsequently use
```
bash
```

##7. Create a UNIX user
* testuser 
* if forget password, go back to Windows C:
```
ubuntu config --default-user root
```
* reset back the user
```
ubuntu config --default-user testuser
```
##8. Other commands on Ubuntu
* Run distro update / upgrade
```
sudo apt-get update
sudo apt-get upgrade
```

* check current Linux distro
```
lsb_release -a
```

* find your local drives mounted (C:)
```
ll /mnt/c
cd /mnt/c

ls /mnt/c/temp
```

##9. Install gcc compiler for C programming language
* One of the needs for Linux on Windows is the programming in C
* install gcc
```
sudo apt-get install gcc
which gcc
gcc --version
```
* write your first program
```
su testuser
cd /mnt/c/Test
nano hello.c
```
* paste the following
```
#include <stdio.h>
int main()
{
  printf("hello world\n");
  return 0;
}
```
* After writing your program, press Ctrl + O and hit Enter key to save your program. To exit nano press Ctrl + X
* compile the program
```
gcc hello.c -o hello
```
* execute the program
```
./hello
```
* [best tutorial of C]
(https://beginnersbook.com/2014/01/c-tutorial-for-beginners-with-examples/)


##10. Why WSL
```
Frequently Asked Questions
https://msdn.microsoft.com/en-us/commandline/wsl/faq

WSL
This is primarily a tool for developers -- especially web developers and 
those who work on or with open source projects. 
This allows those who want/need to use Bash, common Linux tools (sed, awk, etc.) 
and many Linux-first tools (Ruby, Python, etc.) to use their toolchain on Windows.

testuser:~$ which perl
/usr/bin/perl
testuser:~$ which python3
/usr/bin/python3
testuser:~$ which perl
/usr/bin/perl


```
