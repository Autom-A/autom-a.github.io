---
title: "utils.hosts_selected.py"
date: 2023-12-05T03:18:43+01:00
draft: false
---

<a id="utils.hosts_selected.SingletonHostsSelected"></a>

## SingletonHostsSelected Objects

```python
class SingletonHostsSelected()
```

This class is a sigleton object for HostsSelected class

<a id="utils.hosts_selected.Host"></a>

## Host Objects

```python
class Host()
```

This class represents one host object to export it to yml for the ansible inventory

<a id="utils.hosts_selected.Host.__init__"></a>

#### \_\_init\_\_

```python
def __init__(hostname: str, host_ip: str, host_port: int)
```

Create Host instance and fill hostname, host_ip and host_port

**Arguments**:

- `hostname` _str_ - The name of the host
- `host_ip` _str_ - The ip or fqdn of the host
- `host_port` _int_ - The ssh port of the host
  

**Raises**:

- `ValueError` - If there are missing value, raise the Exception

<a id="utils.hosts_selected.Host.set_connection_method"></a>

#### set\_connection\_method

```python
def set_connection_method(connection_method: int, username: str,
                          pass_or_keyfile: str)
```

Fill connection_method, username and pass_or_keyfile.

**Arguments**:

- `connection_method` _HostConnectionMethod_ - Value from the Enum, define user/password or user/keyfile connection method
- `username` _str_ - user to connect on host using ssh
- `pass_or_keyfile` _str_ - password or the path of the keyfile to connect on host using ssh
  

**Raises**:

- `ValueError` - If there are missing value, raise the Exception

<a id="utils.hosts_selected.Host.set_sudo_access"></a>

#### set\_sudo\_access

```python
def set_sudo_access(sudo_username: str, sudo_password: str)
```

Fill sudo_username and sudo_password to permits privilege escalation

**Arguments**:

- `sudo_username` _str_ - username of a user with sudo privilege
- `sudo_password` _str_ - password of a user with sudo privilege
  

**Raises**:

- `ValueError` - If there are missing value, raise the Exception

<a id="utils.hosts_selected.Host.get_yml"></a>

#### get\_yml

```python
def get_yml() -> str
```

Render the Host instance into a string with yml syntax for the Ansible inventory file

**Raises**:

- `ValueError` - If the value of connection_method is not in the Enum
  

**Returns**:

- `str` - The yml string

<a id="utils.hosts_selected.HostsSelected"></a>

## HostsSelected Objects

```python
class HostsSelected(SingletonHostsSelected)
```

This class keep in memory which hosts are selected and their configuration

<a id="utils.hosts_selected.HostsSelected.add_host"></a>

#### add\_host

```python
def add_host(host: dict)
```

Create a host and add it to the list of hosts

**Arguments**:

- `host` _dict_ - Dict that contains value to add host
  

**Raises**:

  HostAlreadyAdded : If the hostname already exists
- `ValueError` - If there are missing value, raise the Exception

<a id="utils.hosts_selected.HostsSelected.is_hostname_unique"></a>

#### is\_hostname\_unique

```python
def is_hostname_unique(new_hostname: str) -> bool
```

Check if the hostname has already been added

**Arguments**:

- `new_hostname` _str_ - The hostname to check
  

**Raises**:

- `ValueError` - If there are missing value, raise the Exception
  

**Returns**:

- `bool` - True if the hostname is unique else False
