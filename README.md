# whichELF?
Improved Linux `which` reporting both: type and the executable (including size).
```
~ $ whichELF? pwd
    pwd
	-> pwd is a shell builtin 
--- and:
	-> /usr/bin/pwd
		->  ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=cf610477f0530f1dbeac1ed8f650f869fb610d10, for GNU/Linux 3.2.0, stripped
			( fileSize = 35328 bytes )
```
