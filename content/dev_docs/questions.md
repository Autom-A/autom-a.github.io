---
title: "Questions"
date: 2023-11-65T16:31:13+02:00
draft: false
---

# questions.yml

This file contain the specification of the useful variables for the playbook jinja template.

## Example

```yml
---
id: "The ID of the rule"
title: "The title of the Rule"
description: "The description of the rule"
author: "The author name"
last_modified: "MM/DD/YYYY of the corresponding last modifiction"
tags:
  - "Tag1"
  - "Tag2"

questions:
  - title: "The first value to fill"
    name: "The name of the variable to render with this result"
    required: "A boolean to say if the value can be None or not"
    type: "One of the defined types"
    value: "None by default, the value filled by this question"

  - title: "The first value to fill"
    name: "The name of the variable to render with this result"
    required: "A boolean to say if the value can be None or not"
    type: "One of the defined types"
    value: "None by default, the value filled by this question"

### EXAMPLE ###
---
id: "R42"
title: "This rule is an example"
description: "You will answer a famous question: what is the life answer ?"
author: "aiglematth"
last_modified: "10/24/2023"
tags:
  - "life"
  - "answer"

questions:
  - title: "What is the answer of the life ?"
    name: "life_answer"
    required: yes
    type: "u8"
    value:

  - title: "Are you sure of your answer ?"
    name: "are_you_sure"
    required: yes
    type: "bool"
    value:
```

## Types

| Type    | Description       |
|---------|-------------------|
| str     | Basic string type |
| list<x> | List of type x    |