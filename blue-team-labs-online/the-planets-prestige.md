# The Planet's Prestige

## What is the email service used by the malicious actor?

To find the email service used by the malicious actor we need to check the `Received` field after opening the email in a text-editor.

<figure><img src="../.gitbook/assets/1 (77).png" alt=""><figcaption></figcaption></figure>

### Answer

```
emkei.cz
```



## What is the Reply-To email address?

If we open the file using [Thunderbird](https://www.thunderbird.net/en-US/), we can find the `Reply-To` email address.

<figure><img src="../.gitbook/assets/2 (75).png" alt=""><figcaption></figcaption></figure>

### Answer

```
negeja3921@pashter.com
```



## What is the filetype of the received attachment which helped to continue the investigation?

Let's open the PDF file attached to the email.

<figure><img src="../.gitbook/assets/3 (66).png" alt=""><figcaption></figcaption></figure>

So the file isn't opening. Maybe it is not really a PDF.

Using the `file` utility we can check the actual format of the file.

```
$ file PuzzleToCoCanDa.pdf 
PuzzleToCoCanDa.pdf: Zip archive data, at least v2.0 to extract
```

### Answer

```
zip
```



## What is the name of the malicious actor?

Now that we know it is a ZIP file, we can rename it to `PuzzleToCoCanDa.zip` and then unzip it.

```
$ unzip PuzzleToCoCanDa.pdf
Archive:  PuzzleToCoCanDa.pdf
  inflating: PuzzleToCoCanDa/DaughtersCrown  
  inflating: PuzzleToCoCanDa/GoodJobMajor  
  inflating: PuzzleToCoCanDa/Money.xlsx  
```

We can see that the ZIP file contains a file called `GoodJobMajor`.

If we use the `exiftool` utility on that file to check the metadata we can find the name of the malicious actor.

```
$ exiftool GoodJobMajor 
ExifTool Version Number         : 12.42
File Name                       : GoodJobMajor
Directory                       : .
File Size                       : 28 kB
File Modification Date/Time     : 2021:01:26 11:14:22-05:00
File Access Date/Time           : 2023:09:28 11:06:29-04:00
File Inode Change Date/Time     : 2023:09:28 10:51:42-04:00
File Permissions                : -rw-rw-r--
File Type                       : PDF
File Type Extension             : pdf
MIME Type                       : application/pdf
PDF Version                     : 1.5
Linearized                      : No
Author                          : Pestero Negeja
Producer                        : Skia/PDF m90
Page Count                      : 1
```

### Answer

```
Pestero Negeja
```



## What is the location of the attacker in this Universe?

On opening the `Money.xlsx` file, we can see that there are two sheets: `Sheet1` and `Sheet3`.&#x20;

<figure><img src="../.gitbook/assets/4 (53).png" alt=""><figcaption></figcaption></figure>

Let's covert both the sheets to text files so that we can view the content better.

If we open the `Sheet3.txt` file we can see some text that appears to be encrypted.

<figure><img src="../.gitbook/assets/5 (51).png" alt=""><figcaption></figcaption></figure>

The `==` at the end indicates that the encryption is Base64.

We can use Cyberchef to decrypt the text.

<figure><img src="../.gitbook/assets/6 (46).png" alt=""><figcaption></figcaption></figure>

### Answer

```
The Martian Colony, Beside Interplanetary Spaceport
```



## What could be the probable C\&C domain to control the attacker’s autonomous bots?

The attacker's name is `Pestero Negeja` and the reply-to email is `negeja3921@pashter.com` so we can guess the C\&C domain used by the attacker.

### Answer

```
pashter.com
```
