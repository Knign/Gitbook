# Tux!

> The flag is hidden inside the Penguin! Solve this challenge before solving my 100 point Scope challenge which uses similar techniques as this one.&#x20;
>
> [Tux.jpg](https://ctflearn.com/challenge/download/973)

Let's check the metadata of the image using the `exiftool` utility.

```
$ exiftool Tux.jpg
ExifTool Version Number         : 12.40
File Name                       : Tux.jpg
Directory                       : .
File Size                       : 5.6 KiB
File Modification Date/Time     : 2020:07:22 09:33:14+05:30
File Access Date/Time           : 2023:10:09 10:13:06+05:30
File Inode Change Date/Time     : 2023:10:09 10:13:35+05:30
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Comment                         : ICAgICAgUGFzc3dvcmQ6IExpbnV4MTIzNDUK.
Image Width                     : 196
Image Height                    : 216
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 196x216
Megapixels                      : 0.042
```

We can see that the `Comment` field is encoded using Base64. We can use Cyberchef to decode it.&#x20;

<figure><img src="../../.gitbook/assets/1 (90).png" alt=""><figcaption></figcaption></figure>

So the `Comment` was a password. But we don't have anything to unlock yet.

The `binwalk` utility is used for searching a given binary image for embedded files and executable code,

```
$ binwalk -e tux.jpg 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard 1.01

WARNING: Extractor.execute failed to run external extractor 'jar xvf '%e'': [Errno 2] No such file or directory: 'jar', 'jar xvf '%e'' might not be installed correctly
5488          0x1570          Zip archive data, encrypted at least v1.0 to extract, compressed size: 39, uncompressed size: 27, name: flag
5679          0x162F          End of Zip archive, footer length: 22
```

Let's check what embedded files were extracted.

```
$ ls
tux.jpg  _tux.jpg.extracted
```

We can `cd _tux.jpg.extracted` and check what's in there.

```
$ ls
tux.jpg  _tux.jpg.extracted
```

* So there is a ZIP file that we need to extract. This is where the password that we decrypted becomes useful.

```
$ unzip 1570.zip
Archive:  1570.zip
[1570.zip] flag password: 
replace flag? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
 extracting: flag     
```

* Now all we have to do is `cat` the flag.

```
$ cat flag 
CTFlearn{Linux_Is_Awesome}
```

### Flag

```
CTFlearn{Linux_Is_Awesome}
```
