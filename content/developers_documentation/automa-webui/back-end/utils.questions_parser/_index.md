---
title: "utils.questions_parser.py"
date: 2023-12-05T03:30:05+01:00
draft: false
---

<a id="utils.questions_parser.read_questions_file"></a>

#### read\_questions\_file

```python
def read_questions_file(path: str) -> dict
```

Take a recommendation path and read the questions.yml file linked to

**Arguments**:

- `path` _str_ - Path of the recommendation
  

**Raises**:

- `PathDoesNotExist` - If the path {path}/questions.yml does not exist
  

**Returns**:

- `dict` - A dict that represents the questions.yml file

<a id="utils.questions_parser.list_categories"></a>

#### list\_categories

```python
def list_categories(supported_systems: SupportedSystems) -> list[str]
```

List categories contained in the environment selected by the user

**Arguments**:

- `supported_systems` _SupportedSystems_ - singleton that contains the user env selection
  

**Raises**:

- `PathDoesNotExist` - If the specified path does not exist
- `VariablePathNotDefined` - If variables are not filled
  

**Returns**:

- `list[str]` - The list of categories in the path

<a id="utils.questions_parser.list_reference"></a>

#### list\_reference

```python
def list_reference(category: str,
                   supported_systems: SupportedSystems) -> list[str]
```

List all reference base (ANSSI, CIS, etc) from a category

**Arguments**:

- `category` _str_ - The category to list
- `supported_systems` _SupportedSystems_ - singleton that contains the user env selection
  

**Returns**:

- `list[str]` - the list of references contained in the category

<a id="utils.questions_parser.list_recommendations"></a>

#### list\_recommendations

```python
def list_recommendations(category: str, reference: str,
                         supported_systems: SupportedSystems) -> list[str]
```

List recommendation available in the reference directory in a category

**Arguments**:

- `category` _str_ - One of the category available in env selected
- `reference` _str_ - The reference to list
- `supported_systems` _SupportedSystems_ - singleton that contains the user env selection
  

**Raises**:

- `PathDoesNotExist` - If the specified path does not exist
- `VariablePathNotDefined` - If variables are not filled
  

**Returns**:

- `list[str]` - The list of recommendations in the reference dir from the category

<a id="utils.questions_parser.is_type_ok"></a>

#### is\_type\_ok

```python
def is_type_ok(type_asked: str, answer) -> bool
```

This method check is the type provided by the user is correct

**Arguments**:

- `type_asked` _str_ - type asked in the questions.yml file
- `answer` __type__ - answer provided by the user
  

**Returns**:

- `bool` - True if the type corresponds, else False

<a id="utils.questions_parser.check_answers"></a>

#### check\_answers

```python
def check_answers(r_path: str, answer_list: list[dict]) -> dict[str]
```

Take the answer provided by the user and check if it is conform in comparaison
of the questions.yml. It check, the type, the real format, if value exists in case of
required "true". If everything is correct, return the dict object to inject in the
playbook template (playbook.yml.j2).

**Arguments**:

- `r_path` _str_ - path of the recommendation
- `answer_list` _list[dict]_ - list of the answers provided by the user
  

**Raises**:

- `AnswerIsRequired` - If the answers is present but no value
- `WrongAnswerType` - If the type provived textually of in object instance is wrong
- `PathDoesNotExist` - If the specified path does not exist
- `IndexError` - If there are missing answers
  

**Returns**:

- `dict[str]` - The answers the inject in playbook template
