# Step 1 Boot Kali Linux and launch the Terminal

```
Start your computer and boot into Kali Linux
If you don't yet have a Kali Linux machine, install the OS onto a Virtual Machine
Once the operating system has fully loaded, open the terminal interface.
```

# Step 2 Locate the Target File

```
Identify the target file that contains the hashed passwords that you want to crack.
Use the Terminal interface to navigate to the directory where your target file is located.
```

# Step 3 Preparing the Password Hashes

```
John the Ripper requires that the hashed passwords be in a specific format.
If the target file contains unsalted MD5 hashes, then you can proceed to the next step.
Otherwise you will need to convert the hashes to a compatible format.
```

# Step 4 Running John the Ripper

```
In the terminal, enter the following command to initiate the John the Ripper program.

John [path/to/target/file]

John the Ripper will start processing the password hashes using the default settings.
```

# Step 5 Monitoring your Progress and Results

```
John the Ripper will display its progress and estimated time remaining.
Once John the Ripper has finished processing, it will display the cracked passwords
(if successful) or indicate the inability to crack certain passwords.
```

# Step 6 Analyzing the Results

```
Examine the results displayed by John the Ripper in the Terminal.
Cracked passwords will be displayed alongside their corresponding hashes.
Use the obtained passwords responsibly and ensure that they conform to any applicable laws or policies.
```

# John The Ripper Hash Formats

```
crypt – generic crypt(3)

$ cat hashes.txt
SDbsugeBiC58A
$ john hashes.txt # Doesn't work.  JTR detects hash as "Traditional DES".
$ john --format=crypt hashes.txt
$ cat hashes.txt

username:SDbsugeBiC58A
$ john hashes.txt # Doesn't work.  JTR detects hash as "Traditional DES".
$ john --format=crypt hashes.txt
$ cat hashes.txt

username:SDbsugeBiC58A:::::::
$ john hashes.txt # Doesn't work.  JTR detects hash as "Traditional DES".
$ john --format=crypt hashes.txt
```
```
HTTP Digest access authentication

$ cat hashes.txt
$response$679066476e67b5c7c4e88f04be567f8b$user$myrealm$GET$/$8c12bd8f728afe56d45a0ce846b70e5a$00000001$4b61913cec32e2c9$auth
$ john hashes.txt
$ john --format=hdaa hashes.txt

$ cat hashes.txt
username:$response$679066476e67b5c7c4e88f04be567f8b$user$myrealm$GET$/$8c12bd8f728afe56d45a0ce846b70e5a$00000001$4b61913cec32e2c9$auth
$ john hashes.txt
$ john --format=hdaa hashes.txt

$ cat hashes.txt
username:$response$679066476e67b5c7c4e88f04be567f8b$user$myrealm$GET$/$8c12bd8f728afe56d45a0ce846b70e5a$00000001$4b61913cec32e2c9$auth:::::::
$ john hashes.txt
$ john --format=hdaa hashes.txt
```
```
HMAC MD5

$ cat hashes.txt
what do ya want for nothing?#750c783e6ab0b503eaa86e310a5db738
$ john hashes.txt
$ john --format=hmac-md5 hashes.txt

$ cat hashes.txt
username:what do ya want for nothing?#750c783e6ab0b503eaa86e310a5db738
$ john hashes.txt
$ john --format=hmac-md5 hashes.txt

$ cat hashes.txt
username:what do ya want for nothing?#750c783e6ab0b503eaa86e310a5db738:::::::
$ john hashes.txt
$ john --format=hmac-md5 hashes.txt
```
```
Lotus5

$ cat hashes.txt
355E98E7C7B59BD810ED845AD0FD2FC4
$ john hashes.txt # Doesn't work.  JTR detects hash as "LM DES".
$ john --format=lotus5 hashes.txt

$ cat hashes.txt
username:355E98E7C7B59BD810ED845AD0FD2FC4
$ john hashes.txt # Doesn't work.  JTR detects hash as "LM DES".
$ john --format=lotus5 hashes.txt

$ cat hashes.txt
username:355E98E7C7B59BD810ED845AD0FD2FC4:::::::
$ john hashes.txt # Doesn't work.  JTR detects hash as "LM DES".
$ john --format=lotus5 hashes.txt
```
```
M$ Cache Hash

$ cat hashes.txt
M$test1#64cd29e36a8431a2b111378564a10631
$ john hashes.txt # Doesn't work.  JTR detects hash as "HMAC MD5".
$ john --format=mscash hashes.txt

$ cat hashes.txt
username:M$test1#64cd29e36a8431a2b111378564a10631
$ john hashes.txt # Doesn't work.  JTR detects hash as "HMAC MD5".
$ john --format=mscash hashes.txt

$ cat hashes.txt
username:M$test1#64cd29e36a8431a2b111378564a10631:::::::
$ john hashes.txt # Doesn't work.  JTR detects hash as "HMAC MD5".
$ john --format=mscash hashes.txt
```
```
MS-SQL

$ cat hashes.txt
0x0100A607BA7C54A24D17B565C59F1743776A10250F581D482DA8B6D6261460D3F53B279CC6913CE747006A2E3254
$ john hashes.txt
$ john --format=mssql hashes.txt

$ cat hashes.txt
username:0x0100A607BA7C54A24D17B565C59F1743776A10250F581D482DA8B6D6261460D3F53B279CC6913CE747006A2E3254
$ john hashes.txt
$ john --format=mssql hashes.txt

$ cat hashes.txt
username:0x0100A607BA7C54A24D17B565C59F1743776A10250F581D482DA8B6D6261460D3F53B279CC6913CE747006A2E3254:::::::
$ john hashes.txt
$ john --format=mssql hashes.txt
```
```
MYSQL

$ cat hashes.txt
5d2e19393cc5ef67
$ john hashes.txt # Doesn't work.  JTR detects hash as "MYSQL_fast".
$ john --format=mysql hashes.txt

$ cat hashes.txt
username:5d2e19393cc5ef67
$ john hashes.txt # Doesn't work.  JTR detects hash as "MYSQL_fast".
$ john --format=mysql hashes.txt

$ cat hashes.txt
username:5d2e19393cc5ef67:::::::
$ john hashes.txt # Doesn't work.  JTR detects hash as "MYSQL_fast".
$ john --format=mysql hashes.txt
```
```
Oracle

$ cat hashes.txt
O$SIMON#4F8BC1809CB2AF77
$ john hashes.txt
$ john --format=oracle hashes.txt

$ cat hashes.txt
username:O$SIMON#4F8BC1809CB2AF77
$ john hashes.txt
$ john --format=oracle hashes.txt

$ cat hashes.txt
username:O$SIMON#4F8BC1809CB2AF77:::::::
$ john hashes.txt
$ john --format=oracle hashes.txt
```
```
pdf

$ cat hashes.txt
$pdf$Standard*badad1e86442699427116d3e5d5271bc80a27814fc5e80f815efeef839354c5f*289ece9b5ce451a5d7064693dab3badf101112131415161718191a1b1c1d1e1f*16*34b1b6e593787af681a9b63fa8bf563b*1*1*0*1*4*128*-4*3*2
$ john hashes.txt
$ john --format=pdf hashes.txt

$ cat hashes.txt
username:$pdf$Standard*badad1e86442699427116d3e5d5271bc80a27814fc5e80f815efeef839354c5f*289ece9b5ce451a5d7064693dab3badf101112131415161718191a1b1c1d1e1f*16*34b1b6e593787af681a9b63fa8bf563b*1*1*0*1*4*128*-4*3*2
$ john hashes.txt
$ john --format=pdf hashes.txt

$ cat hashes.txt
username:$pdf$Standard*badad1e86442699427116d3e5d5271bc80a27814fc5e80f815efeef839354c5f*289ece9b5ce451a5d7064693dab3badf101112131415161718191a1b1c1d1e1f*16*34b1b6e593787af681a9b63fa8bf563b*1*1*0*1*4*128*-4*3*2:::::::
$ john hashes.txt
$ john --format=pdf hashes.txt
```
```
rar

$ cat hashes.txt
$rar3$*0*c9dea41b149b53b4*fcbdb66122d8ebdb32532c22ca7ab9ec*24
$ john hashes.txt
$ john --format=rar hashes.txt

$ cat hashes.txt
username:$rar3$*0*c9dea41b149b53b4*fcbdb66122d8ebdb32532c22ca7ab9ec*24
$ john hashes.txt
$ john --format=rar hashes.txt

$ cat hashes.txt
username:$rar3$*0*c9dea41b149b53b4*fcbdb66122d8ebdb32532c22ca7ab9ec*24:::::::
$ john hashes.txt
$ john --format=rar hashes.txt
```
```
Raw SHA-1

$ cat hashes.txt
A9993E364706816ABA3E25717850C26C9CD0D89D
$ john hashes.txt
$ john --format=raw-sha1 hashes.txt

$ cat hashes.txt
username:A9993E364706816ABA3E25717850C26C9CD0D89D
$ john hashes.txt
$ john --format=raw-sha1 hashes.txt

$ cat hashes.txt
username:A9993E364706816ABA3E25717850C26C9CD0D89D:::::::
$ john hashes.txt
$ john --format=raw-sha1 hashes.txt
```
```
Raw SHA-224

$ cat hashes.txt
d63dc919e201d7bc4c825630d2cf25fdc93d4b2f0d46706d29038d01
$ john hashes.txt
$ john --format=raw-sha224 hashes.txt

$ cat hashes.txt
username:d63dc919e201d7bc4c825630d2cf25fdc93d4b2f0d46706d29038d01
$ john hashes.txt
$ john --format=raw-sha224 hashes.txt

$ cat hashes.txt
username:d63dc919e201d7bc4c825630d2cf25fdc93d4b2f0d46706d29038d01:::::::
$ john hashes.txt
$ john --format=raw-sha224 hashes.txt
```
```
Raw SHA-256

$ cat hashes.txt
5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8
$ john hashes.txt # Doesn't work.  JTR detects hash as "Post.Office MD5".
$ john --format=raw-sha256 hashes.txt

$ cat hashes.txt
username:5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8
$ john hashes.txt # Doesn't work.  JTR detects hash as "Post.Office MD5".
$ john --format=raw-sha256 hashes.txt

$ cat hashes.txt
username:5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8:::::::
$ john hashes.txt # Doesn't work.  JTR detects hash as "Post.Office MD5".
$ john --format=raw-sha256 hashes.txt
```
```
ssh

$ cat hashes.txt
$ssh2$2d2d2d2d2d424547494e204453412050524956415445204b45592d2d2d2d2d0a50726f632d547970653a20342c454e435259505445440a44454b2d496e666f3a204145532d3132382d4342432c35413830363832373943304634364539383230373135304133433245433631340a0a2f756954696e4a3452556a6f5a76302b705931694d763163695661724369347a2f62365a694c4161565970794a31685854327463692b593266334c61614578630a6f357772316141464d3437786d526d476f3832492f76434847413952786735776147433970574f475a5675555172447355367463556b434d422b325a344753390a354f44474364444b32674e6574446e62324a764873714154736d3443633633476468695a30734346594c71796d2b576531774359616c78734f3231572b4f676f0a42336f6746464977327232462b714a7a714d37415543794c466869357a476d7536534e6558765534477a784750464a4e47306d414f55497761614e3161446a630a4e326b3462437266796271337a366e436533444273384b3232694e2b3875526e534162434f717a5a5845645971555959354b6b6a326e654354525458494e64670a512b61535359673379355937626f4b6b6a494f727650555748654f796475512b74657273414577376e43564a7a72394e387452673271563450557631434b66700a4f49467742372f39736f6d6a59496a71576f61537a6a784b30633852777a305331706d722b7571726277792b50656f75354d3373656d486c426b4769553237660a776f684b792b4d554e4862734e6a7973535a53456c4e4b734d4950715449567a5a45316d5646412f30754d477164705133627a424f6a58325a6f36656446434f0a6d4a34775961765735774d2b6a6d75564b5056564e7939395a78796570304645644c50354b623263345a6c3053396631342f62366836415069785665377a75760a5662536b4279664a6e797a68494f5942497954374d64773134723441584a56362b5a6f457730397769774d3d0a2d2d2d2d2d454e44204453412050524956415445204b45592d2d2d2d2d0a*771
$ john hashes.txt
$ john --format=ssh hashes.txt

$ cat hashes.txt
username:$ssh2$2d2d2d2d2d424547494e204453412050524956415445204b45592d2d2d2d2d0a50726f632d547970653a20342c454e435259505445440a44454b2d496e666f3a204145532d3132382d4342432c35413830363832373943304634364539383230373135304133433245433631340a0a2f756954696e4a3452556a6f5a76302b705931694d763163695661724369347a2f62365a694c4161565970794a31685854327463692b593266334c61614578630a6f357772316141464d3437786d526d476f3832492f76434847413952786735776147433970574f475a5675555172447355367463556b434d422b325a344753390a354f44474364444b32674e6574446e62324a764873714154736d3443633633476468695a30734346594c71796d2b576531774359616c78734f3231572b4f676f0a42336f6746464977327232462b714a7a714d37415543794c466869357a476d7536534e6558765534477a784750464a4e47306d414f55497761614e3161446a630a4e326b3462437266796271337a366e436533444273384b3232694e2b3875526e534162434f717a5a5845645971555959354b6b6a326e654354525458494e64670a512b61535359673379355937626f4b6b6a494f727650555748654f796475512b74657273414577376e43564a7a72394e387452673271563450557631434b66700a4f49467742372f39736f6d6a59496a71576f61537a6a784b30633852777a305331706d722b7571726277792b50656f75354d3373656d486c426b4769553237660a776f684b792b4d554e4862734e6a7973535a53456c4e4b734d4950715449567a5a45316d5646412f30754d477164705133627a424f6a58325a6f36656446434f0a6d4a34775961765735774d2b6a6d75564b5056564e7939395a78796570304645644c50354b623263345a6c3053396631342f62366836415069785665377a75760a5662536b4279664a6e797a68494f5942497954374d64773134723441584a56362b5a6f457730397769774d3d0a2d2d2d2d2d454e44204453412050524956415445204b45592d2d2d2d2d0a*771
$ john hashes.txt
$ john --format=ssh hashes.txt

$ cat hashes.txt
username:$ssh2$2d2d2d2d2d424547494e204453412050524956415445204b45592d2d2d2d2d0a50726f632d547970653a20342c454e435259505445440a44454b2d496e666f3a204145532d3132382d4342432c35413830363832373943304634364539383230373135304133433245433631340a0a2f756954696e4a3452556a6f5a76302b705931694d763163695661724369347a2f62365a694c4161565970794a31685854327463692b593266334c61614578630a6f357772316141464d3437786d526d476f3832492f76434847413952786735776147433970574f475a5675555172447355367463556b434d422b325a344753390a354f44474364444b32674e6574446e62324a764873714154736d3443633633476468695a30734346594c71796d2b576531774359616c78734f3231572b4f676f0a42336f6746464977327232462b714a7a714d37415543794c466869357a476d7536534e6558765534477a784750464a4e47306d414f55497761614e3161446a630a4e326b3462437266796271337a366e436533444273384b3232694e2b3875526e534162434f717a5a5845645971555959354b6b6a326e654354525458494e64670a512b61535359673379355937626f4b6b6a494f727650555748654f796475512b74657273414577376e43564a7a72394e387452673271563450557631434b66700a4f49467742372f39736f6d6a59496a71576f61537a6a784b30633852777a305331706d722b7571726277792b50656f75354d3373656d486c426b4769553237660a776f684b792b4d554e4862734e6a7973535a53456c4e4b734d4950715449567a5a45316d5646412f30754d477164705133627a424f6a58325a6f36656446434f0a6d4a34775961765735774d2b6a6d75564b5056564e7939395a78796570304645644c50354b623263345a6c3053396631342f62366836415069785665377a75760a5662536b4279664a6e797a68494f5942497954374d64773134723441584a56362b5a6f457730397769774d3d0a2d2d2d2d2d454e44204453412050524956415445204b45592d2d2d2d2d0a*771:::::::
$ john hashes.txt
$ john --format=ssh hashes.txt
```
```
zip

$ cat hashes.txt
$zip$*0*1*8005b1b7d077708d*dee4
$ john hashes.txt
$ john --format=zip hashes.txt

$ cat hashes.txt
username:$zip$*0*1*8005b1b7d077708d*dee4
$ john hashes.txt
$ john --format=zip hashes.txt

$ cat hashes.txt
username:$zip$*0*1*8005b1b7d077708d*dee4:::::::
$ john hashes.txt
$ john --format=zip hashes.txt
```
