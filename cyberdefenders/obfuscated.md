# Obfuscated

{% hint style="warning" %}
Always open malware in a secure environment like a VM.
{% endhint %}

{% hint style="info" %}
We will be using the [REMnux](https://remnux.org/) distribution which is specifically made for reverse engineering.
{% endhint %}

##

> Q1. What is the sha256 hash of the doc file?

* We can obtain the sha256 hash using the `sha256sum` command.

```
$ sha256sum 49b367ac261a722a7c2bbbc328c32545 
ff2c8cadaa0fd8da6138cce6fce37e001f53a5d9ceccd67945b15ae273f4d751  49b367ac261a722a7c2bbbc328c32545
```

##

> Q2. Multiple streams contain macros in this document. Provide the number of lowest one.

* Using the `oledump` utility we can analyze the streams of data contained in a file.

```
$ oledump.py 49b367ac261a722a7c2bbbc328c32545 
  1:       114 '\x01CompObj'
  2:       284 '\x05DocumentSummaryInformation'
  3:       392 '\x05SummaryInformation'
  4:      8017 '1Table'
  5:      4096 'Data'
  6:       483 'Macros/PROJECT'
  7:        65 'Macros/PROJECTwm'
  8: M    7117 'Macros/VBA/Module1'
  9: m    1104 'Macros/VBA/ThisDocument'
 10:      3467 'Macros/VBA/_VBA_PROJECT'
 11:      2964 'Macros/VBA/__SRP_0'
 12:       195 'Macros/VBA/__SRP_1'
 13:      2717 'Macros/VBA/__SRP_2'
 14:       290 'Macros/VBA/__SRP_3'
 15:       565 'Macros/VBA/dir'
 16:        76 'ObjectPool/_1541577328/\x01CompObj'
 17: O   20301 'ObjectPool/_1541577328/\x01Ole10Native'
 18:      5000 'ObjectPool/_1541577328/\x03EPRINT'
 19:         6 'ObjectPool/_1541577328/\x03ObjInfo'
 20:    133755 'WordDocument'
```

* As we can see, the 8th stream is the lowest one with a macro.

##

> Q3. What is the decryption key of the obfuscated code?

* Let's specify the 8th stream and turn on `verbose` mode.

```
$ oledump.py 49b367ac261a722a7c2bbbc328c32545 -s 8 -v

--snip--;
Set R66BpJMgxXBo2h = CreateObject("WScript.Shell")
R66BpJMgxXBo2h.Run """" + OBKHLrC3vEDjVL + """" + " EzZETcSXyKAdF_e5I2i1"
--snip--;
```

* We can also use `olevba` to find VBA Macros.
* The `maintools.js` file is being accessed. If we scroll up we can see the decryption key used as the first command-line argument.

```
$ olevba 49b367ac261a722a7c2bbbc328c32545 

--snip--;
Set R66BpJMgxXBo2h = CreateObject("WScript.Shell")
R66BpJMgxXBo2h.Run """" + OBKHLrC3vEDjVL + """" + " EzZETcSXyKAdF_e5I2i1"
--snip--;
```

##

> Q4. What is the name of the dropped file?

* We can find the dropped file in the output of `olevba`.

```
$ olevba 49b367ac261a722a7c2bbbc328c32545 

--snip--;
+----------+--------------------+---------------------------------------------+
|Type      |Keyword             |Description                                  |
+----------+--------------------+---------------------------------------------+
|AutoExec  |AutoOpen            |Runs when the Word document is opened        |
|AutoExec  |AutoClose           |Runs when the Word document is closed        |
|Suspicious|Environ             |May read system environment variables        |
|Suspicious|Open                |May open a file                              |
|Suspicious|Put                 |May write to a file (if combined with Open)  |
|Suspicious|Binary              |May read or write a binary file (if combined |
|          |                    |with Open)                                   |
|Suspicious|Kill                |May delete a file                            |
|Suspicious|Shell               |May run an executable file or a system       |
|          |                    |command                                      |
|Suspicious|WScript.Shell       |May run an executable file or a system       |
|          |                    |command                                      |
|Suspicious|Run                 |May run an executable file or a system       |
|          |                    |command                                      |
|Suspicious|CreateObject        |May create an OLE object                     |
|Suspicious|Windows             |May enumerate application windows (if        |
|          |                    |combined with Shell.Application object)      |
|Suspicious|Xor                 |May attempt to obfuscate specific strings    |
|          |                    |(use option --deobf to deobfuscate)          |
|Suspicious|Base64 Strings      |Base64-encoded strings were detected, may be |
|          |                    |used to obfuscate strings (option --decode to|
|          |                    |see all)                                     |
|IOC       |maintools.js        |Executable file name                         |
+----------+--------------------+---------------------------------------------+
```

##

> Q5. This script uses what language?

* The dropped file is `main.js` which uses Javascript.

##

> Q6. What is the name of the variable that is assigned the command-line arguments?
