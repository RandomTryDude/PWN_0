##  One-Time Pad ( OTP )
> Consider a Secret encrypted with a one-time pad

Say a Secret A , and a Key B |
OTP will take  A XOR it to B |
A ^ B = C |
where C is now our encrypted cipher.

As long as B , the secret, isnt found , the text is virtually impossible to crack

Say B got leaked.
Reverse the function to find it back 

A^B = C

C ^ B = A 

In Python , With both A & B as b64 encoded value : 
```
import base64

def byte_xor(ba1, ba2):
    return bytes([_a ^ _b for _a, _b in zip(ba1, ba2)])

    key = "1gFZlFTJTPvA9AJ26Y4="
ciphertext = "nyE4+XSsIpiyjXICjOo="


key = base64.b64decode(key)
ciphertext = base64.b64decode(ciphertext)


clear_text = byte_xor(key,ciphertext)
print(clear_text)


```
# result
> b'I am encrypted'

