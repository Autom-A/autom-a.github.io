---
title: "utils.id_management.py"
date: 2023-12-05T03:20:23+01:00
draft: false
---

<a id="utils.id_management.SingletonRecommendationID"></a>

## SingletonRecommendationID Objects

```python
class SingletonRecommendationID()
```

Sigleton of the RecommendationID class

<a id="utils.id_management.RecommendationID"></a>

## RecommendationID Objects

```python
class RecommendationID(SingletonRecommendationID)
```

This class manage the ID of each recommendation. To avoid to put ID in recommendation
directories and files, the class RecommendationID manage dynamically ID by adding missing pair
ID/path in the ID file. Futhermore, all ID are UUID from the uuid.uuid4()

<a id="utils.id_management.RecommendationID.set_playbooks_location"></a>

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

<a id="utils.id_management.RecommendationID.set_id_file_location"></a>

#### set\_id\_file\_location

```python
def set_id_file_location(path: str)
```

Set the location of the ID/PATH pair file

**Arguments**:

- `path` _str_ - Path of the file
  

**Raises**:

- `VariablePathNotDefined` - If variables are not filled

<a id="utils.id_management.RecommendationID.attribute_new_playbooks"></a>

#### attribute\_new\_playbooks

```python
def attribute_new_playbooks(all_recommendation_paths: list[str])
```

Add missing pair ID/PATH in the file. The pair ID/PATH are not deleted when
a playbook is removed.

**Arguments**:

- `all_recommendation_paths` _list[str]_ - list of all recommendation paths

<a id="utils.id_management.RecommendationID.get_available_playbooks"></a>

#### get\_available\_playbooks

```python
def get_available_playbooks() -> list[str]
```

browse all folders in the playbook folder to retrieve all recommendation paths

**Returns**:

- `list[str]` - all recommendation paths

<a id="utils.id_management.RecommendationID.get_id_from_path"></a>

#### get\_id\_from\_path

```python
def get_id_from_path(path: str) -> str
```

Translate a path to an ID. The ID is used mainly in the front-end

**Arguments**:

- `path` _str_ - path to translate
  

**Raises**:

- `IDDoesNotExist` - If the path doesn't have an ID
- `PathDoesNotExist` - If the specified path does not exist
- `VariablePathNotDefined` - If variables are not filled
  

**Returns**:

- `str` - The path's ID

<a id="utils.id_management.RecommendationID.get_path_from_id"></a>

#### get\_path\_from\_id

```python
def get_path_from_id(id: str) -> str
```

Translate an ID to a path. The path is used mainly in the back-end

**Arguments**:

- `id` _str_ - The id to translate
  

**Raises**:

- `IDDoesNotExist` - If the ID does not exist
- `VariablePathNotDefined` - If variables are not filled
  

**Returns**:

- `str` - The ID's path

