# information

{% hint style="info" %}
Look at the details of the file
{% endhint %}

{% hint style="info" %}
Make sure to submit the flag as picoCTF{XXXXX}
{% endhint %}

First we have to download the file into the web terminal.

```
$ wget https://mercury.picoctf.net/static/a614a27d4cb251d04c7d2f3f3f76a965/cat.jpg
```

Let's check the file properties using the `file` command.

```
$ file cat.jpg
cat.jpg: JPEG image data, JFIF standard 1.02, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 2560x1598, components 3
```

It is a JPEG image. We can validate this by looking at the header.

```
$ xxd cat.jpg | head
00000000: ffd8 ffe0 0010 4a46 4946 0001 0200 0001  ......JFIF......
00000010: 0001 0000 ffed 0030 5068 6f74 6f73 686f  .......0Photosho
00000020: 7020 332e 3000 3842 494d 0404 0000 0000  p 3.0.8BIM......
00000030: 0013 1c02 7400 0750 6963 6f43 5446 1c02  ....t..PicoCTF..
00000040: 0000 0200 0400 ffe1 0bf9 6874 7470 3a2f  ..........http:/
00000050: 2f6e 732e 6164 6f62 652e 636f 6d2f 7861  /ns.adobe.com/xa
00000060: 702f 312e 302f 003c 3f78 7061 636b 6574  p/1.0/.<?xpacket
00000070: 2062 6567 696e 3d27 efbb bf27 2069 643d   begin='...' id=
00000080: 2757 354d 304d 7043 6568 6948 7a72 6553  'W5M0MpCehiHzreS
00000090: 7a4e 5463 7a6b 6339 6427 3f3e 0a3c 783a  zNTczkc9d'?>.<x:
```

Every image has some metadata unless it has been erased manually. `exiftool` can be used to check this metadata.

```
$ exiftool cat.jpg 
ExifTool Version Number         : 12.40
File Name                       : cat.jpg
Directory                       : .
File Size                       : 858 KiB
File Modification Date/Time     : 2021:03:15 18:24:46+00:00
File Access Date/Time           : 2023:07:18 16:35:56+00:00
File Inode Change Date/Time     : 2023:07:18 16:35:38+00:00
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
```

For the most part, everything seems pretty standard except for the license. Let's decode it using `base64`.

```
$ echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d
picoCTF{the_m3tadata_1s_modified}
```
