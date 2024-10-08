---
layout: default
---


# Introduction

I’m passionate about IT and cybersecurity, I would like to employ my skills and what I’ve learned throughout college and the labs that I have worked on. I would love to apply my skills as a IT technician, IT help desk, service desk engineer.



## My Skills:

*   Information Systems: Linux, Windows
  
*   Programming Languaes: Python
  
*   MS Word, Excel

*   Documentation

*   Consistent

*   Deadline Driven
  
*   Good Communication Skills
  
*   Languagues Spoken: English, Bisaya, Tagalog


### IT Industry Certifications

| Certification        | Date          | Verified |
|:-------------|:------------------|:------|
| CompTIA Security+ | June 13, 2024   |  Yes  |
| CompTIA A+           | January 10, 2024 |  Yes  |
| ISC2 Certified in Cybersecurity (CC) | September 28, 2024 | Yes
| CCNA: Switching, Routing, and Wireless Essentials          | June 21, 2024    |  Yes   |
| CCNA: Introduction to Networks        | April 21, 2024|  Yes |
| Introduction to Cybersecurity         | January 10, 2024 |  Yes  |
| IT Essentials         | June 21, 2024 |  Yes  |



## My Cybersecurity Projects

1.  [RCCs Ultimate Relocating Network Infrastructure](https://github.com/7jason771/RCCs-Relocating-Network-Infrastructure)

2.  [RCC CSC RPI Networking Project](https://github.com/7jason771/My_Cyber_Projects/blob/main/CSC_RPI_Project_jsalerno.pdf)

3.  [RCC RTB CTF](https://github.com/7jason771/My_Cyber_Projects/blob/main/2024_RTB_CTF_Setup_Ubuntu.pdf)

4.  [Secure Hacking Lab](https://github.com/7jason771/My_Cyber_Projects/blob/main/SecureHackingLab_jsalerno.pdf)

5.  [Secure Kali Drive](https://github.com/7jason771/My_Cyber_Projects/blob/main/Encrypted_Persistent_Flash_Drive.pdf)

6.  [Gray Box Project](https://github.com/7jason771/My_Cyber_Projects/blob/main/Gray_Box_Test_2_VMs.pdf)

7.  [RPI_DCHP_Server](https://github.com/7jason771/My_Cyber_Projects/blob/main/RPI_DHCP_server_jsalerno.pdf)

8.  [RPI_DNS_Server](https://github.com/7jason771/My_Cyber_Projects/blob/main/RPI_DNS_server_jsalerno.pdf)





### Free Windows Self-Vulnerability Scanner

```python

import socket
import subprocess
import winreg

def check_open_ports(host, port_list):
    open_ports = []
    for port in port_list:
        with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as sock:
            result = sock.connect_ex((host, port))
            if result == 0:
                open_ports.append(port)
    return open_ports

def get_installed_software():
    software_list = []
    reg_path = r"SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall"
    try:
        reg_key = winreg.OpenKey(winreg.HKEY_LOCAL_MACHINE, reg_path, 0, winreg.KEY_READ | winreg.KEY_WOW64_32KEY)
        i = 0
        while True:
            try:
                subkey_name = winreg.EnumKey(reg_key, i)
                subkey = winreg.OpenKey(reg_key, subkey_name)
                try:
                    software_name = winreg.QueryValueEx(subkey, "DisplayName")[0]
                    software_version = winreg.QueryValueEx(subkey, "DisplayVersion")[0]
                    software_list.append((software_name, software_version))
                except FileNotFoundError:
                    pass
                i += 1
            except OSError:
                break
    except Exception as e:
        print(f"Error accessing the registry: {e}")
    return software_list

def check_windows_update():
    try:
        result = subprocess.run(["wmic", "qfe", "list"], capture_output=True, text=True)
        return result.stdout
    except Exception as e:
        return str(e)

def main():
    host = "localhost"
    port_list = [21, 22, 23, 80, 443, 3389]
    print("Checking open ports...")
    open_ports = check_open_ports(host, port_list)
    print(f"Open ports: {open_ports}")

    print("\nChecking installed software...")
    software_list = get_installed_software()
    for software, version in software_list:
        print(f"{software} - {version}")

    print("\nChecking Windows updates...")
    updates = check_windows_update()
    print(updates)

if __name__ == "__main__":
    main()


```



### Free Mac-OS Self-Vulnerability Scanner

```python
import socket
import subprocess

def check_open_ports(host, port_list):
    open_ports = []
    for port in port_list:
        with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as sock:
            result = sock.connect_ex((host, port))
            if result == 0:
                open_ports.append(port)
    return open_ports

def get_installed_software():
    software_list = []
    try:
        result = subprocess.run(["brew", "list", "--versions"], capture_output=True, text=True)
        lines = result.stdout.splitlines()
        for line in lines:
            software, version = line.split()
            software_list.append((software, version))
    except Exception as e:
        print(f"Error accessing Homebrew: {e}")
    return software_list

def check_macos_update():
    try:
        result = subprocess.run(["softwareupdate", "--list"], capture_output=True, text=True)
        return result.stdout
    except Exception as e:
        return str(e)

def main():
    host = "localhost"
    port_list = [21, 22, 23, 80, 443, 3389]
    print("Checking open ports...")
    open_ports = check_open_ports(host, port_list)
    print(f"Open ports: {open_ports}")

    print("\nChecking installed software...")
    software_list = get_installed_software()
    for software, version in software_list:
        print(f"{software} - {version}")

    print("\nChecking macOS updates...")
    updates = check_macos_update()
    print(updates)

if __name__ == "__main__":
    main()

```








<div style="text-align: center;">
    Thank you for visiting my website!
</div>
