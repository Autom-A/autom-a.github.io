---
title: "utils.path.py"
date: 2023-12-05T03:21:27+01:00
draft: false
---

<a id="utils.path.list_dir_in_dir"></a>

#### list\_dir\_in\_dir

```python
def list_dir_in_dir(path: str) -> list[str]
```

This method is a os.listdir wrapper to return only directories without the .git dir

**Arguments**:

- `path` _str_ - Dir to list
  

**Returns**:

- `list[str]` - List of the directories contained in path

