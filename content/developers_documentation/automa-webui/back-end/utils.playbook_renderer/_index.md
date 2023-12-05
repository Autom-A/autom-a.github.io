---
title: "utils.playbook_renderer.py"
date: 2023-12-05T03:23:42+01:00
draft: false
---

<a id="utils.playbook_renderer.playbook_render_write"></a>

#### playbook\_render\_write

```python
def playbook_render_write(dir_path: str, variables: dict)
```

This function take the playbook.yml.j2 template to inject into all answers from
user input. After this, the function is writing the playbook as 'playbook.yml'
in the directory

**Arguments**:

- `dir_path` _str_ - The path of the recommendation where template is stored
- `variables` _dict_ - A dict containing variable names and variable values to
  render in the template

**Raises**:

- `PathDoesNotExist` - If the specified path does not exist

