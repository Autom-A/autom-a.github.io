---
title: "app.table.component.js"
date: 2023-12-05T03:08:25+01:00
draft: false
---

## Functions

<dl>
<dt><a href="#renderRecommendationLine">renderRecommendationLine(item)</a></dt>
<dd><p>Render recommendation line adding elements to the DOM</p>
</dd>
<dt><a href="#generateButtonRadio">generateButtonRadio(line, id)</a> ⇒ <code>HTMLElement</code></dt>
<dd><p>Generate button radio and fill it from local storage</p>
</dd>
<dt><a href="#unSavedIdSelected">unSavedIdSelected(id)</a></dt>
<dd><p>Unsave id from the local storage</p>
</dd>
<dt><a href="#renderInventoryLine">renderInventoryLine(host)</a></dt>
<dd><p>Render inventory line adding elements to the DOM</p>
</dd>
<dt><a href="#renderCell">renderCell(textDisplayed)</a></dt>
<dd><p>Render cell</p>
</dd>
</dl>


<a name="renderRecommendationLine"></a>

### renderRecommendationLine(item)
Render recommendation line adding elements to the DOM


| Param | Type | Description |
| --- | --- | --- |
| item | <code>Recommendation</code> | Recommendation retrieve by the back |

<a name="generateButtonRadio"></a>

### generateButtonRadio(line, id) ⇒ <code>HTMLElement</code>
Generate button radio and fill it from local storage

**Returns**: <code>HTMLElement</code> - th element containing a element with radio.  

| Param | Type | Description |
| --- | --- | --- |
| line | <code>Recommendation</code> | Recommendation line HTML |
| id | <code>string</code> | ID Item |

<a name="unSavedIdSelected"></a>

### unSavedIdSelected(id)
Unsave id from the local storage


| Param | Type | Description |
| --- | --- | --- |
| id | <code>string</code> | ID Item |

<a name="renderInventoryLine"></a>

### renderInventoryLine(host)
Render inventory line adding elements to the DOM


| Param | Type | Description |
| --- | --- | --- |
| host | <code>Inventory</code> | Host from inventory |

<a name="renderCell"></a>

### renderCell(textDisplayed)
Render cell


| Param | Type | Description |
| --- | --- | --- |
| textDisplayed | <code>Recommendation</code> | Text added in the celle |
