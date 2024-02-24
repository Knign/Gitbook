# ASCII

> In Python, the `chr()` function can be used to convert an ASCII ordinal number to a character (the `ord()` function does the opposite).

### Solution

```python
list = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125] 
flag = ""  
for i in list:  
    ascii_char = chr(i)  
    flag += ascii_char  
print(f"{flag}")
```
