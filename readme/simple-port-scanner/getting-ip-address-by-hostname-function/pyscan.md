# PyScan

```python
import pyfiglet
import sys
import socket
from datetime import datetime
from IPy import IP
from get_ip import get_ip_by_hostname

print(pyfiglet.figlet_format("Port scanner"))

target = input("Target IP address or target Hostname: ")
target = get_ip_by_hostname(target)

print(f'\033[38;5;64mSet range of scanning ports\033[0m')

start_port = int(input('Enter start scan port: '))

stop_port = int(input('Enter the final scan port: '))


try:
    IP(target)  

    print(f'{"*" * 50}\n'
          f'Started scanning \033[38;5;184m{target}\033[0m at \033[4m{datetime.now().strftime("%Y-%m-%d %H:%M:%S")}\033[0m\n'
          f'{"*" * 50}\n')
    try:

        for port in range(start_port, stop_port + 1):
            s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            socket.setdefaulttimeout(1)

            result = s.connect_ex((target, port))
            if result == 0:
                print("[*] {} port is open".format(port))
            s.close()

    except KeyboardInterrupt:
        print("\n*****Exiting Program! Bye!*****")
        sys.exit()
    except socket.gaierror:
        print("\n*****Hostname Could Not Be Resolved!*****")
        sys.exit()
    except socket.error:
        print("\n*****Server not responding!*****")
        sys.exit()


except Exception as ex:
    print(f'\033[38;5;196m{ex} (please check your IP address or hostname is correct)\033[0m')
```
