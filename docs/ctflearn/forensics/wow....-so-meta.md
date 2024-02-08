# WOW.... So Meta

> This photo was taken by our target. See what you can find out about him from it. https://mega.nz/#!ifA2QAwQ!WF-S-MtWHugj8lx1QanGG7V91R-S1ng7dDRSV25iFbk

<figure><img src="../../.gitbook/assets/1 (65).png" alt=""><figcaption></figcaption></figure>

### Linux

Using the `strings` utility, we can see all the strings included in the image. We can then pipe the command with `grep` in order to filter out the flag.

```
$ strings 95f6edfb66ef42d774a5a34581f19052.jpg | grep "flag"
flag{wow!_data_is_cool}
```



### Windows

On downloading the image we can use [EXIF.tools](https://exif.tools/) to view the image metadata.

<figure><img src="../../.gitbook/assets/2 (63).png" alt=""><figcaption></figcaption></figure>

### Flag

```
CTFlearn{wow!_data_is_cool}
```
