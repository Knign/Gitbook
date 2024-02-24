# Javascript - Authentication 2

<figure><img src="../../.gitbook/assets/1 (68).png" alt=""><figcaption></figcaption></figure>

When we click on the login button, a dialog box pops up prompting us to enter the username and password.

Let's check the source code.

<figure><img src="../../.gitbook/assets/2 (66).png" alt=""><figcaption></figcaption></figure>

* We can see that the `login.js` file is where the script is being imported from. We can follow the link to check it out.

<figure><img src="../../.gitbook/assets/3 (60).png" alt=""><figcaption></figcaption></figure>

So this is where the input authentication takes place.

```javascript
function connexion(){
    var username = prompt("Username :", "");
    var password = prompt("Password :", "");
    var TheLists = ["GOD:HIDDEN"];
    for (i = 0; i < TheLists.length; i++)
    {
        if (TheLists[i].indexOf(username) == 0)
        {
            var TheSplit = TheLists[i].split(":");
            var TheUsername = TheSplit[0];
            var ThePassword = TheSplit[1];
            if (username == TheUsername && password == ThePassword)
            {
                alert("Vous pouvez utiliser ce mot de passe pour valider ce challenge (en majuscules) / You can use this password to validate this challenge (uppercase)");
            }
        }
        else
        {
            alert("Nope, you're a naughty hacker.")
        }
    }
}
```

There is an array `TheLists` containing one element: `GOD:HIDDEN`.

It checks if the username entered by the user matches the username from the current element in the `TheLists` array (using `TheLists[i].indexOf(username) == 0`).

If there is a match, it splits the current element into username and password using `split(":")`, and then it compares the entered username and password with the stored values. If both match, it displays an alert with a success message.

Let's enter the credentials.

<figure><img src="../../.gitbook/assets/4 (55).png" alt=""><figcaption></figcaption></figure>

## Password

```
HIDDEN
```
