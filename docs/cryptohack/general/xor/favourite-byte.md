# Favourite byte

> I've hidden some data using XOR with a single byte, but that byte is a secret. Don't forget to decode from hex first.

### Solution

<pre class="language-python"><code class="lang-python"><strong>from pwn import xor
</strong>
hex_string = '73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d'
byte_string = bytes.fromhex(hex_string)
flag = ""

for num in range(256):
    result = xor(byte_string, num)
    if b'crypto' in result:
        break
flag = result.decode()
print(flag)
</code></pre>
