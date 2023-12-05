---
title: "app.selection.component.js"
date: 2023-12-05T03:05:19+01:00
draft: false
---

## Functions

<dl>
<dt><a href="#fillSelector">fillSelector(type, values, verificationFunction)</a></dt>
<dd><p>Fill selector with values and bind verification function</p>
</dd>
<dt><a href="#loadDataFromStorage">loadDataFromStorage(select_item, selectorId)</a></dt>
<dd><p>Load data of the selector from storage</p>
</dd>
<dt><a href="#storeInLocalStorage">storeInLocalStorage(value, selectorId)</a></dt>
<dd><p>Store data of the selector into storage</p>
</dd>
<dt><a href="#removeValidButtonAttribute">removeValidButtonAttribute(attributeName)</a></dt>
<dd><p>Remove an attribute to valid button</p>
</dd>
<dt><a href="#setValidButtonDisabledAttribute">setValidButtonDisabledAttribute(bool, attributeName)</a></dt>
<dd><p>Change disabled attribute in validation button</p>
</dd>
<dt><a href="#reinitSelector">reinitSelector(selector)</a></dt>
<dd><p>Reinit selector options, remove all options except the first one.</p>
</dd>
<dt><a href="#resetChildSelector">resetChildSelector(childName)</a></dt>
<dd><p>Reset child</p>
</dd>
</dl>

<a name="fillSelector"></a>

### fillSelector(type, values, verificationFunction)
Fill selector with values and bind verification function


| Param | Type | Description |
| --- | --- | --- |
| type | <code>type</code> | name of the selector |
| values | <code>type</code> | values |
| verificationFunction | <code>type</code> | values |

<a name="loadDataFromStorage"></a>

### loadDataFromStorage(select_item, selectorId)
Load data of the selector from storage


| Param | Type | Description |
| --- | --- | --- |
| select_item | <code>M.FormSelect</code> | Select element |
| selectorId | <code>string</code> | id of the selector |

<a name="storeInLocalStorage"></a>

### storeInLocalStorage(value, selectorId)
Store data of the selector into storage


| Param | Type | Description |
| --- | --- | --- |
| value | <code>string</code> | value to store |
| selectorId | <code>string</code> | id of the selector |

<a name="removeValidButtonAttribute"></a>

### removeValidButtonAttribute(attributeName)
Remove an attribute to valid button


| Param | Type | Description |
| --- | --- | --- |
| attributeName | <code>string</code> | Name of the attribute |

<a name="setValidButtonDisabledAttribute"></a>

### setValidButtonDisabledAttribute(bool, attributeName)
Change disabled attribute in validation button


| Param | Type | Description |
| --- | --- | --- |
| bool | <code>boolean</code> | value of disabled attribute |
| attributeName | <code>string</code> | Name of the attribute |

<a name="reinitSelector"></a>

### reinitSelector(selector)
Reinit selector options, remove all options except the first one.

**Summary**: Remove all options in the dom except the first because in our case this first option is
used as a placeholder for the moment  

| Param | Type | Description |
| --- | --- | --- |
| selector | <code>M.FormSelect</code> | selector to clean |

<a name="resetChildSelector"></a>

### resetChildSelector(childName)
Reset child

**Summary**: In our workflow reset a child selector has to reinit a child ONLY if the child
is already visible  

| Param | Type | Description |
| --- | --- | --- |
| childName | <code>string</code> | child name selector |

