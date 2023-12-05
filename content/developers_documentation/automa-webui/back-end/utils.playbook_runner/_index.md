---
title: "utils.playbook_runner.py"
date: 2023-12-05T03:27:52+01:00
draft: false
---

<a id="utils.playbook_runner.run_ansible_playbook"></a>

#### run\_ansible\_playbook

```python
def run_ansible_playbook()
```

This function call runner function from ansible to run the playbook.master.yml with
the inventory.yml

**Raises**:

- `PathDoesNotExist` - If the path of playbook.master.yml or inventory.yml does not exist
