## AES-ECB ( With Key)

Consider you get Key + Cipher

and want to decrypt it

In python :
```
from Crypto.Util.Padding import pad, unpad
from Crypto.Cipher import AES
from base64 import b64encode,b64decode

key = 'Efs87PVJJXwwC2mSJNU0PQ=='
cipher = 'U0ZTzO0SHx07mV9/EMYBmlb844clcmwbIpLH5=='

def encrypt(plaintext,key):
    cipher = AES.new(key,AES.MODE_ECB)
    return b64encode(cipher.encrypt(pad(plaintext.encode(),16))).decode()
    
def decrypt(ciphertext,key):
    cipher = AES.new(b64decode(key),AES.MODE_ECB)
    return unpad(cipher.decrypt(b64decode(ciphertext.encode())),16).decode()
    
print(decrypt(cipher,key))
```

## AES-ECB (Padding Attack)

What's a padding attack ? 
Aes-ECB being a block Cipher
if you can prepend data to the cipher like : 
where you dont know the clear text
```
Custom_Data + clear text = Cipher
```
you can 'push' the letters one by one off the last block and try all alphanum until the whole block is known
