---
description: Need to login before u start script
---

# ✉ WhatsApp spammer

```
import pywhatkit
import pyautogui as pt

import time

def send_message_instant():

    limit = int(input('Enter message limit: '))
    mobile = input('Enter phone number: ')
    spam_message = input('Enter spam message: ')

    pywhatkit.sendwhatmsg_instantly(phone_no=mobile,message=spam_message, wait_time=10)
    i = 0
    time.sleep(10)
    while i < limit:
        pt.typewrite(spam_message)
        pt.press('Enter')
        i += 1


def main():
    send_message_instant()

if __name__ == '__main__':
        main()
```
