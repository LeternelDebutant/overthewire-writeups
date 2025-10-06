# Bandit 2

## Level information

### Level Goal

The password for the next level is stored in a file called - located in the home directory
Commands you may need to solve this level

[ls](https://manpages.ubuntu.com/manpages/noble/man1/ls.1.html) , [cd](https://manpages.ubuntu.com/manpages/noble/man1/cd.1posix.html) , [cat](https://manpages.ubuntu.com/manpages/noble/man1/cat.1.html) , [file](https://manpages.ubuntu.com/manpages/noble/man1/file.1.html) , [du](https://manpages.ubuntu.com/manpages/noble/man1/du.1.html) , [find](https://manpages.ubuntu.com/manpages/noble/man1/find.1.html)

### Helpful Reading Material

* [Google Search for “dashed filename”](https://www.google.com/search?q=dashed+filename)
* [Advanced Bash-scripting Guide - Chapter 3 - Special Characters](https://linux.die.net/abs-guide/special-chars.html)

## Solution

When we're connected to the VM, with the command ```ls```, we can see our dashed filename.

```bash
bandit1@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit2 bandit1 33 Aug 15 13:16 -
```

Using the command ```cat -``` will not work. This instruction does not tell you to display the content of the file ```-``` but instead it tells you to display whatever input you wrote. For example, in my case, I decided to write the word "test" in the terminal after entering the command ```cat -``` and after pressing ```Enter```, it just displayed what I wrote.

```bash
bandit1@bandit:~$ cat -
test
test
```

To summarize, the dash ```-``` acts as a redirection from/to STDIN or STDOUT. To be able to display the content of the file, what you need is to specify the full or relative path of the file when using the ```cat``` command.

```bash
bandit1@bandit:~$ pwd
/home/bandit1
bandit1@bandit:~$ cat /home/bandit1/-
<REDACTED>
bandit1@bandit:~$ 
```

```bash
bandit1@bandit:~$ cat ./-
<REDACTED>
bandit1@bandit:~$ 
```
