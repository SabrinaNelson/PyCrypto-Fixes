=================================================================
DISCLAIMER:
-----------------------------------------------------------------
Even though PyCrypto is depreciated, it can still be used to teach how cryptography works. I have a fixed a few things so that anything using the Crypto library can be used by those running Python38-32 on Windows 10. So far, I have only needed to do three things to get PyCrypto to run. 

Note, this is NOT a patch that makes PyCrypto more secure! This is a patch that makes it possible to run and use PyCrypto on Windows 10 while using Python38-32! I am not exprienced enough in Python to make it more secure! 

I am also not the original owner, so I will not take any credit for anything! I am just posting a guide for educational purposes. If you wish to install the libraries that use the Crypto library, please go to the following links:

https://github.com/chrissimpkins/crypto
https://github.com/dlitz/pycrypto
https://github.com/Legrandin/pycryptodome/tree/master/lib

https://pypi.org/project/crypto/
https://pypi.org/project/pycrypto/
https://pypi.org/project/pycryptodome/
https://pypi.org/project/pycryptodomex/

=================================================================
FIXES:
------------------------------------------------------------------

FIX 1: Making Crypto Useable

To apply the first fix, you are going to want to do the following:

1) Find a file named "crypto" (all lowercase) in the directory "C:\Program Files (x86)\Python38-32\Lib\site-packages" on your computer, depending on where you installed it and Python

2) Rename "crypto" to "Crypto"

You will now be able to use the Crypto library.

------------------------------------------------------------------

FIX 2: Winrandom Error

To apply the second fix:

1) Go to "C:\Program Files (x86)\Python38-32\Lib\site-packages\Crypto\Random\OSRNG" in your directory

2) Open the file named "nt.py" with Notepad++ or any other code editor that supports the Python language

3) Go to line 29 and change "import winrandom" to "from .import winrandom"

Winrandom now should now be useable.

------------------------------------------------------------------

FIX 3: Time.Clock() Error

To apply the third fix:

1) Go to "C:\Program Files (x86)\Python38-32\Lib\site-packages\Crypto\Random" in your directory

2) Open up the file named "_UserFriendlyRNG.py" in Notepad++ or any other code editor that supports the Python language

3) Look for all instances of "time.clock()" that are in the file

4) Replace each "time.clock()" with "time.perf_counter()"

You can now use the _UserFriendlyRNG.py to help generate RNG.