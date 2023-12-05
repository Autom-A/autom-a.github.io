---
title: "app.question.component.js"
date: 2023-12-05T03:01:10+01:00
draft: false
---

## Functions

<dl>
<dt><a href="#renderQuestion">renderQuestion(_id)</a></dt>
<dd><p>If the modal template is already instatiated, the function open it else it creates 
the modal. It takes the configuration of the question to choose which elements need to 
be added to the modal (select, input, chips, ...)</p>
</dd>
<dt><a href="#getAnswersValues">getAnswersValues(id, indexQuestion)</a> ⇒ <code>answer</code></dt>
<dd><p>Get answer value by id recommendation and index question from local storage</p>
</dd>
<dt><a href="#initializeMaterializeComponent">initializeMaterializeComponent()</a></dt>
<dd><p>Initialize Material components. This function need to be called after adding components
to the DOM. This method is useful because in our case, our components are returned
by our functions before adding them to the DOM. Some errors appears with Select component
with this workflow.
It&#39;s base on global scope variable &#39;MATERIALIZE_FIFO&#39;</p>
</dd>
<dt><a href="#renderQuestionBtn">renderQuestionBtn()</a></dt>
<dd><p>Create validation button and bind it with the click event.</p>
</dd>
<dt><a href="#renderQuestionField">renderQuestionField(_id, index, one_field, answerStored)</a> ⇒ <code>HTMLElement</code></dt>
<dd><p>Render question from &#39;render_field_str&#39; method in case of &#39;str&#39; : input
Render question from &#39;render_field_list_str&#39; method in case of &#39;list<str>&#39; : chips
Render question from &#39;render_field_choice_str&#39; method in case of &#39;choice<str>&#39; : select</p>
</dd>
<dt><a href="#renderFieldStr">renderFieldStr(_id, index, one_field, answerStored)</a> ⇒ <code>HTMLElement</code></dt>
<dd><p>Render question method in case of &#39;str&#39; : it creates an input</p>
</dd>
<dt><a href="#renderFieldListStr">renderFieldListStr(_id, index, one_field, answerStored)</a> ⇒ <code>HTMLElement</code></dt>
<dd><p>Render question method in case of &#39;list<str>&#39; : it creates a chips element</p>
</dd>
<dt><a href="#renderFieldChoiceStr">renderFieldChoiceStr(_id, index, one_field, answerStored)</a> ⇒ <code>HTMLElement</code></dt>
<dd><p>Render question method in case of &#39;choice<str>&#39; : it creates a select element
The Select element is an</p>
</dd>
<dt><a href="#retrieveListStrData">retrieveListStrData(inputComponent, configType)</a></dt>
<dd><p>Get data from chips in case of &#39;list<str>&#39;, it takes values from a chips elements and
add it to the local storage</p>
</dd>
<dt><a href="#retrieveStr">retrieveStr(inputComponent, configType)</a></dt>
<dd><p>Get data from input in case of &#39;str&#39;, it takes valueand
add it to the local storage</p>
</dd>
<dt><a href="#storeAnswerInLocalStorage">storeAnswerInLocalStorage(inputComponent, dataToSave, configType)</a></dt>
<dd><p>Update local storage with a new value. If the answer value is empty, it&#39;s remove from local storage.
If there&#39;s already a value present, we update this value.</p>
</dd>
<dt><a href="#storeSelectedIds">storeSelectedIds(id)</a></dt>
<dd><p>Manage selected IDS. Based on verification about storage item with UUID of the recommendation.
If an item with the same id does not exists, we remove the id from the data
We also check the local storage to create it if it&#39;s not exists.</p>
</dd>
<dt><a href="#storeAnswerData">storeAnswerData(id, valueFormat, dataToSave)</a></dt>
<dd><p>Store answer data to localStorage</p>
</dd>
<dt><a href="#formatValueToStore">formatValueToStore(inputComponent, dataToSave, configType)</a> ⇒ <code>string</code></dt>
<dd><p>Format a value in order to be store in local storage. It&#39;s a JSON format with three keys :
value, formatType, index</p>
</dd>
</dl>

<a name="renderQuestion"></a>

### renderQuestion(_id)
If the modal template is already instatiated, the function open it else it creates 
the modal. It takes the configuration of the question to choose which elements need to 
be added to the modal (select, input, chips, ...)

**Summary**: Display a modal template and fill it from config question  

| Param | Type | Description |
| --- | --- | --- |
| _id | <code>\_id</code> | question UUID |

<a name="getAnswersValues"></a>

### getAnswersValues(id, indexQuestion) ⇒ <code>answer</code>
Get answer value by id recommendation and index question from local storage

**Returns**: <code>answer</code> - answer - if exists or null  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>string</code> | id of recommendation |
| indexQuestion | <code>number</code> | index of the question |

<a name="initializeMaterializeComponent"></a>

### initializeMaterializeComponent()
Initialize Material components. This function need to be called after adding components
to the DOM. This method is useful because in our case, our components are returned
by our functions before adding them to the DOM. Some errors appears with Select component
with this workflow.
It's base on global scope variable 'MATERIALIZE_FIFO'

**Summary**: Initialize Material components wich need to be added to the DOM before
init  
<a name="renderQuestionBtn"></a>

### renderQuestionBtn()
Create validation button and bind it with the click event.

<a name="renderQuestionField"></a>

### renderQuestionField(_id, index, one_field, answerStored) ⇒ <code>HTMLElement</code>
Render question from 'render_field_str' method in case of 'str' : input
Render question from 'render_field_list_str' method in case of 'list<str>' : chips
Render question from 'render_field_choice_str' method in case of 'choice<str>' : select

**Summary**: Render question depending on the answer type  
**Returns**: <code>HTMLElement</code> - HTMLElement - Brief description of the returning value here.  

| Param | Type | Description |
| --- | --- | --- |
| _id | <code>\_id</code> | UUID of the recommendation |
| index | <code>index</code> | Index of question |
| one_field | <code>one\_field</code> | configuration of the answer |
| answerStored | <code>answerStored</code> | answer if exists or null |

<a name="renderFieldStr"></a>

### renderFieldStr(_id, index, one_field, answerStored) ⇒ <code>HTMLElement</code>
Render question method in case of 'str' : it creates an input

**Returns**: <code>HTMLElement</code> - HTMLElement - Brief description of the returning value here.  

| Param | Type | Description |
| --- | --- | --- |
| _id | <code>\_id</code> | UUID of the recommendation |
| index | <code>index</code> | Index of question |
| one_field | <code>one\_field</code> | configuration of the answer |
| answerStored | <code>answerStored</code> | answer if exists or null |

<a name="renderFieldListStr"></a>

### renderFieldListStr(_id, index, one_field, answerStored) ⇒ <code>HTMLElement</code>
Render question method in case of 'list<str>' : it creates a chips element

**Returns**: <code>HTMLElement</code> - HTMLElement - Brief description of the returning value here.  

| Param | Type | Description |
| --- | --- | --- |
| _id | <code>\_id</code> | UUID of the recommendation |
| index | <code>index</code> | Index of question |
| one_field | <code>one\_field</code> | configuration of the answer |
| answerStored | <code>answerStored</code> | answer if exists or null |

<a name="renderFieldChoiceStr"></a>

### renderFieldChoiceStr(_id, index, one_field, answerStored) ⇒ <code>HTMLElement</code>
Render question method in case of 'choice<str>' : it creates a select element
The Select element is an

**Returns**: <code>HTMLElement</code> - HTMLElement - Brief description of the returning value here.  

| Param | Type | Description |
| --- | --- | --- |
| _id | <code>\_id</code> | UUID of the recommendation |
| index | <code>index</code> | Index of question |
| one_field | <code>one\_field</code> | configuration of the answer |
| answerStored | <code>answerStored</code> | answer if exists or null |

<a name="retrieveListStrData"></a>

### retrieveListStrData(inputComponent, configType)
Get data from chips in case of 'list<str>', it takes values from a chips elements and
add it to the local storage


| Param | Type | Description |
| --- | --- | --- |
| inputComponent | <code>input\_component</code> | Chips element |
| configType | <code>configType</code> | Configuration of the field |

<a name="retrieveStr"></a>

### retrieveStr(inputComponent, configType)
Get data from input in case of 'str', it takes valueand
add it to the local storage


| Param | Type | Description |
| --- | --- | --- |
| inputComponent | <code>input\_component</code> | Chips element |
| configType | <code>configType</code> | Configuration of the field |

<a name="storeAnswerInLocalStorage"></a>

### storeAnswerInLocalStorage(inputComponent, dataToSave, configType)
Update local storage with a new value. If the answer value is empty, it's remove from local storage.
If there's already a value present, we update this value.

**Summary**: Update local storage with a new value.  

| Param | Type | Description |
| --- | --- | --- |
| inputComponent | <code>inputComponent</code> | inputComponent is a DOM Element, it has an id : UUIDRecommendation-index |
| dataToSave | <code>dataToSave</code> | Data already process for the back, this value will be sent |
| configType | <code>configType</code> | config type of the question |

<a name="storeSelectedIds"></a>

### storeSelectedIds(id)
Manage selected IDS. Based on verification about storage item with UUID of the recommendation.
If an item with the same id does not exists, we remove the id from the data
We also check the local storage to create it if it's not exists.

**Summary**: Manage selected IDS stored in store  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>ParamDataTypeHere</code> | ID of recommendation |

<a name="storeAnswerData"></a>

### storeAnswerData(id, valueFormat, dataToSave)
Store answer data to localStorage


| Param | Type | Description |
| --- | --- | --- |
| id | <code>inputComponent</code> | Id of recommendation |
| valueFormat | <code>inputComponent</code> | Data formated by our function to be store |
| dataToSave | <code>inputComponent</code> | data to check if it's not empty in order to remove local storage |

<a name="formatValueToStore"></a>

### formatValueToStore(inputComponent, dataToSave, configType) ⇒ <code>string</code>
Format a value in order to be store in local storage. It's a JSON format with three keys :
value, formatType, index

**Returns**: <code>string</code> - Object - id, valueFormat  

| Param | Type | Description |
| --- | --- | --- |
| inputComponent | <code>inputComponent</code> | Input component is needed to retrieve the index of answer and id recommendation |
| dataToSave | <code>inputComponent</code> | Data in value |
| configType | <code>inputComponent</code> | Configuration of this answer to send type answer to the back |
