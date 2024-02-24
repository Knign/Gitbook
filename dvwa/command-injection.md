# Command Injection

> #### Objective
>
> Remotely, find out the user of the web service on the OS, as well as the machines hostname via RCE.

##

## Security Level: Low

> This allows for direct input into one of many PHP functions that will execute commands on the OS. It is possible to escape out of the designed command and executed unintentional actions. This can be done by adding on to the request, "once the command has executed successfully, run this command". Spoiler: To add a command "&&". Example: 127.0.0.1 && dir.&#x20;

<figure><img src="../.gitbook/assets/1 (44).png" alt=""><figcaption></figcaption></figure>

* Let's enter `127.0.0.1` as the IP address.&#x20;

<figure><img src="../.gitbook/assets/2 (41).png" alt=""><figcaption></figcaption></figure>

* So the application takes the user input and uses that in a `ping` command.
* We can chain multiple commands together using the `&&` operator.

```
127.0.0.1 && cat /etc/passwd
```

<figure><img src="../.gitbook/assets/3 (38).png" alt=""><figcaption></figcaption></figure>

##

## Security Level: Medium

> The developer has read up on some of the issues with command injection, and placed in various pattern patching to filter the input. However, this isn't enough. Various other system syntaxes can be used to break out of the desired command. Spoiler: e.g. background the ping command.

* We can check the source code for each level at the bottom of the page.

<figure><img src="../.gitbook/assets/4 (35).png" alt=""><figcaption></figcaption></figure>

* As we can see, our input characters `&&` are being substituted with empty space.
* Let's try using the pipe `|` operator.&#x20;

<figure><img src="../.gitbook/assets/5 (35).png" alt=""><figcaption></figcaption></figure>

##

## Security Level: High

> In the high level, the developer goes back to the drawing board and puts in even more pattern to match. But even this isn't enough. The developer has either made a slight typo with the filters and believes a certain PHP command will save them from this mistake. Spoiler: [trim()](https://secure.php.net/manual/en/function.trim.php) removes all leading & trailing spaces, right?.

* Let's check what typo the developer has made.

<figure><img src="../.gitbook/assets/6 (35).png" alt=""><figcaption></figcaption></figure>

* As we can see, in the third case, the characters `|` are being replaced with empty space.
* We can provide the same input as above just with a slight modification:

```
127.0.0.1 |cat /etc/passwd
```

<figure><img src="../.gitbook/assets/7 (31).png" alt=""><figcaption></figcaption></figure>
