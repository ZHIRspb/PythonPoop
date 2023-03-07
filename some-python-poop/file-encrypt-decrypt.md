---
description: Files encryption/decryption by pyAesCrypt w/ password
---

# 🗃 File encrypt/decrypt

```python
import pyAesCrypt

passwd = input ('File encrypt password: ')
pyAesCrypt.encryptFile('UR_FILE', 'ENCRYPTED_FILE_NAME', passwd)
#decrypt
# passwd = input ('File decrypt password: ')
# pyAesCrypt.decryptFile('ENCRYPTED_FILE_NAME', 'DECRYPTED_FILE_NAME', passwd)
```
