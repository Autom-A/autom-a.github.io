---
title: "utils.supported_systems.py"
date: 2023-12-05T03:32:51+01:00
draft: false
---

<a id="utils.supported_systems.SingletonSupportedSystems"></a>

## SingletonSupportedSystems Objects

```python
class SingletonSupportedSystems()
```

This class is a sigleton object for SupportedSystems class

<a id="utils.supported_systems.SupportedSystems"></a>

## SupportedSystems Objects

```python
class SupportedSystems(SingletonSupportedSystems)
```

This class saves and checks path of the env selected by user.

<a id="utils.supported_systems.SupportedSystems.reset_params"></a>

#### reset\_params

```python
def reset_params()
```

Reset varibles of path, used when they are errors

<a id="utils.supported_systems.SupportedSystems.get_entire_path"></a>

#### get\_entire\_path

```python
def get_entire_path()
```

The method checks and return the complete environment path else raise Exception

**Raises**:

- `PathDoesNotExist` - If the specified path does not exist
- `VariablePathNotDefined` - If variables are not filled
  

**Returns**:

- `str` - The complete environment path selected by the user

<a id="utils.supported_systems.SupportedSystems.set_playbooks_location"></a>

#### set\_playbooks\_location

```python
def set_playbooks_location(path: str)
```

Check and set the location of the playbook directory

**Arguments**:

- `path` _str_ - The path of the playbook location
  

**Raises**:

- `PathDoesNotExist` - If the specified path does not exist
- `VariablePathNotDefined` - If variables are not filled

<a id="utils.supported_systems.SupportedSystems.get_os"></a>

#### get\_os

```python
def get_os() -> list[str]
```

Search for OS directories contained in the playbook directory

**Raises**:

- `VariablePathNotDefined` - If variable  are not filled
  

**Returns**:

- `list[str]` - The list of OS availables in {playbook}/

<a id="utils.supported_systems.SupportedSystems.get_os_type"></a>

#### get\_os\_type

```python
def get_os_type() -> list[str]
```

Search for OS type directories contained in the OS directory selected

**Raises**:

- `PathDoesNotExist` - If the specified path does not exist
- `VariablePathNotDefined` - If variables are not filled
  

**Returns**:

- `list[str]` - The list of OS type availables in {playbook}/{OS}/

<a id="utils.supported_systems.SupportedSystems.get_os_version"></a>

#### get\_os\_version

```python
def get_os_version() -> list[str]
```

Search for OS version directories contained in the OS type selected

**Raises**:

- `PathDoesNotExist` - If the specified path does not exist
- `VariablePathNotDefined` - If variables are not filled
  

**Returns**:

- `list[str]` - The list of OS version availables in {playbook}/{OS}/{OS_TYPE}/

<a id="utils.supported_systems.SupportedSystems.set_os"></a>

#### set\_os

```python
def set_os(os: str) -> None
```

Set the OS selected by the user

**Arguments**:

- `os` _str_ - OS name selected
  

**Raises**:

- `VariablePathNotDefined` - If variables are not filled

<a id="utils.supported_systems.SupportedSystems.set_os_type"></a>

#### set\_os\_type

```python
def set_os_type(os_type: str)
```

Set the OS type selected by the user

**Arguments**:

- `os_type` _str_ - OS type name selected
  

**Raises**:

- `PathDoesNotExist` - If the specified path does not exist
- `VariablePathNotDefined` - If variables are not filled

<a id="utils.supported_systems.SupportedSystems.set_os_version"></a>

#### set\_os\_version

```python
def set_os_version(os_version: str)
```

Set the OS version selected by the user

**Arguments**:

- `os_version` _str_ - OS version name selected
  

**Raises**:

- `PathDoesNotExist` - If the specified path does not exist
- `VariablePathNotDefined` - If variables are not filled
