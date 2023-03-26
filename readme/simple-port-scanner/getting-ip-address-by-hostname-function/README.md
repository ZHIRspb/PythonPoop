# Getting IP address by hostname function

```python
import socket


def get_ip_by_hostname(URL):
    try:
        return socket.gethostbyname(URL)
    except socket.gaierror as error:
        return f'Invalid Hostname - {error}'


```
