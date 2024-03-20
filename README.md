# whichELF?
Improved Linux `which` reporting both: type and the executable (including size and going the chain of links and scripts as far as possible down to the actual executable).
```
~ $ whichELF? pwd
    pwd
	-> pwd is a shell builtin 
--- and:
	-> /usr/bin/pwd
		->  ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=cf610477f0530f1dbeac1ed8f650f869fb610d10, for GNU/Linux 3.2.0, stripped
			( fileSize = 35328 bytes )
```

Allows to detect how deep the system needs to dive down the chain of indirections to the actual executable:  
```
~ $ whichELF? which
    which
	-> /usr/bin/which
		->  symbolic link to /etc/alternatives/which
			( fileSize = 23 bytes )
			->  symbolic link to /usr/bin/which.debianutils
				( fileSize = 26 bytes )
				->  POSIX shell script, ASCII text executable
					( fileSize = 946 bytes )
#! /bin/sh
    /bin/sh
	-> /bin/sh
		->  symbolic link to dash
			( fileSize = 4 bytes )
			->  ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=f7ab02fc1b8ff61b41647c1e16ec9d95ba5de9f0, for GNU/Linux 3.2.0, stripped
				( fileSize = 125688 bytes )
					-> LAST SCRIPT LINE (may list the actual used or further executable):
						-> exit "$ALLRET"
~ $ 
```
