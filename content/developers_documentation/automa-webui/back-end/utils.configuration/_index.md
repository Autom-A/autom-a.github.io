---
title: "utils.configuration.py"
date: 2023-12-05T03:17:01+01:00
draft: false
---

<a id="utils.configuration.SingletonConfiguration"></a>

## SingletonConfiguration Objects

```python
class SingletonConfiguration()
```

Sigleton of the Configuration class

<a id="utils.configuration.Configuration"></a>

## Configuration Objects

```python
class Configuration(SingletonConfiguration)
```

This class read configuration file and retrieve variables. If a variable is not present
the variable is set with a default value.

<a id="utils.configuration.Configuration.get"></a>

#### get

```python
def get(config_key)
```

return the config value of the key specified in arg

<a id="utils.configuration.Configuration.read_configuration"></a>

#### read\_configuration

```python
def read_configuration()
```

Read the configuration file and set required variables
