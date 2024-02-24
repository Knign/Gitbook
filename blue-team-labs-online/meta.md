# Meta

{% hint style="warning" %}
Always open malware in a secure environment like a VM.
{% endhint %}

{% hint style="info" %}
We will be using the [REMnux](https://remnux.org/) distribution which is specifically made for reverse engineering.
{% endhint %}

##

## What is the camera model?

We can find the metadata of the images using the `exiftool` utility and then use `grep` to filter the output.

```
$ exiftool uploaded_1.JPG | grep "Model"
Camera Model Name               : Canon EOS 550D
Canon Model ID                  : EOS Rebel T2i / 550D / Kiss X4
Lens Model                      : EF-S55-250mm f/4-5.6 IS
```

### Answer

```
Canon EOS 550D
```

##

## Question 2

> When was the picture taken?

* This time we have to filter the output for occurrences of `Date`.

```
$ exiftool uploaded_1.JPG | grep "Date"
File Modification Date/Time     : 2021:11:26 11:35:07-05:00
File Access Date/Time           : 2023:09:17 09:49:16-04:00
File Inode Change Date/Time     : 2023:09:17 09:48:15-04:00
Modify Date                     : 2021:11:02 13:20:23
Date/Time Original              : 2021:11:02 13:20:23
Create Date                     : 2021:11:02 13:20:23
Create Date                     : 2021:11:02 13:20:23.32
Date/Time Original              : 2021:11:02 13:20:23.32
Modify Date                     : 2021:11:02 13:20:23.32
```

The `Create Date` field is what we are interested in.

### Answer

```
2021:11:02 13:20:23
```



## What does the comment on the first image says?

Let's filter for `Comment`.

```
$ exiftool uploaded_1.JPG | grep "Comment"
Comment                         : relying on altered metadata to catch me?
```

### Answer

```
relying on altered metadata to catch me?
```



## Where could the criminal be?

For this question we have to perform some reverse image searches which we can do using [Google Image Search](https://images.google.com/).

<figure><img src="../.gitbook/assets/meta 1.png" alt=""><figcaption></figcaption></figure>

As we can see `uploaded_1.JPG` is an picture of the Pashupatinath temple in Kathmandu.

Let's look up `uploaded_2.png` to verify.

<figure><img src="../.gitbook/assets/meta 2.png" alt=""><figcaption></figcaption></figure>

Our results tell us that `uploaded_2.png` is a picture of a historical landmark in Kathmandu called Nasal Chowk.

### Answer

```
Kathmandu
```
