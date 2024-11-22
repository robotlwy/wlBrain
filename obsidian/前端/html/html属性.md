[HTML 全局属性 | 菜鸟教程](https://www.runoob.com/tags/ref-standardattributes.html)
[HTML5 表单属性 | 菜鸟教程](https://www.runoob.com/html/html5-form-attributes.html)
[HTML \<form> 标签 | 菜鸟教程](https://www.runoob.com/tags/tag-form.html)


# \<form> 

New ：HTML5 中的新属性。

| 属性                                                                         | 值                                                                          | 描述                                              |
| :------------------------------------------------------------------------- | :------------------------------------------------------------------------- | :---------------------------------------------- |
| [accept](https://www.runoob.com/tags/att-form-accept.html)                 | _MIME_type_                                                                | HTML5 不支持。规定服务器接收到的文件的类型。（文件是通过文件上传提交的）         |
| [accept-charset](https://www.runoob.com/tags/att-form-accept-charset.html) | _character_set_                                                            | 规定服务器可处理的表单数据字符集。                               |
| [action](https://www.runoob.com/tags/att-form-action.html)                 | _URL_                                                                      | 规定当提交表单时向何处发送表单数据。                              |
| [autocomplete](https://www.runoob.com/tags/att-form-autocomplete.html)New  | on  <br>off                                                                | 规定是否启用表单的自动完成功能。                                |
| [enctype](https://www.runoob.com/tags/att-form-enctype.html)               | application/x-www-form-urlencoded  <br>multipart/form-data  <br>text/plain | 规定在向服务器发送表单数据之前如何对其进行编码。（适用于 method="post" 的情况） |
| [method](https://www.runoob.com/tags/att-form-method.html)                 | get  <br>post                                                              | 规定用于发送表单数据的 HTTP 方法。                            |
| [name](https://www.runoob.com/tags/att-form-name.html)                     | _text_                                                                     | 规定表单的名称。                                        |
| [novalidate](https://www.runoob.com/tags/att-form-novalidate.html)New      | novalidate                                                                 | 如果使用该属性，则提交表单时不进行验证。                            |
| [target](https://www.runoob.com/tags/att-form-target.html)                 | _blank  <br>_self  <br>_parent  <br>_top                                   | 规定在何处打开 action URL。                             |
# \<input>

New : HTML5新标签。

| 属性                                                                             | 值                                                                                                                                                                                                                                                                     | 描述                                                                            |
| :----------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------------------- |
| [accept](https://www.runoob.com/tags/att-input-accept.html)                    | audio/\* video/\* image/* _MIME_type_                                                                                                                                                                                                                                 | 规定通过文件上传来提交的文件的类型。 (只针对type="file")                                           |
| [align](https://www.runoob.com/tags/att-input-align.html)                      | left right top middle bottom                                                                                                                                                                                                                                          | HTML5已废弃，不赞成使用。规定图像输入的对齐方式。 (只针对type="image")                                 |
| [alt](https://www.runoob.com/tags/att-input-alt.html)                          | _text_                                                                                                                                                                                                                                                                | 定义图像输入的替代文本。 (只针对type="image")                                                |
| [autocomplete](https://www.runoob.com/tags/att-input-autocomplete.html)New     | on off                                                                                                                                                                                                                                                                | autocomplete 属性规定 \<input> 元素输入字段是否应该启用自动完成功能。                                |
| [autofocus](https://www.runoob.com/tags/att-input-autofocus.html)New           | autofocus                                                                                                                                                                                                                                                             | 属性规定当页面加载时 \<input> 元素应该自动获得焦点。                                               |
| [checked](https://www.runoob.com/tags/att-input-checked.html)                  | checked                                                                                                                                                                                                                                                               | checked 属性规定在页面加载时应该被预先选定的 \<input> 元素。 (只针对 type="checkbox" 或者 type="radio") |
| [disabled](https://www.runoob.com/tags/att-input-disabled.html)                | disabled                                                                                                                                                                                                                                                              | disabled 属性规定应该禁用的 \<input> 元素。                                               |
| [form](https://www.runoob.com/tags/att-input-form.html)New                     | _form_id_                                                                                                                                                                                                                                                             | form 属性规定 \<input> 元素所属的一个或多个表单。                                              |
| [formaction](https://www.runoob.com/tags/att-input-formaction.html)New         | _URL_                                                                                                                                                                                                                                                                 | 属性规定当表单提交时处理输入控件的文件的 URL。(只针对 type="submit" 和 type="image")                   |
| [formenctype](https://www.runoob.com/tags/att-input-formenctype.html)New       | application/x-www-form-urlencoded multipart/form-data text/plain                                                                                                                                                                                                      | 属性规定当表单数据提交到服务器时如何编码(只适合 type="submit" 和 type="image")。                       |
| [formmethod](https://www.runoob.com/tags/att-input-formmethod.html)New         | get post                                                                                                                                                                                                                                                              | 定义发送表单数据到 action URL 的 HTTP 方法。 (只适合 type="submit" 和 type="image")            |
| [formnovalidate](https://www.runoob.com/tags/att-input-formnovalidate.html)New | formnovalidate                                                                                                                                                                                                                                                        | formnovalidate 属性覆盖 <form> 元素的 novalidate 属性。                                 |
| [formtarget](https://www.runoob.com/tags/att-input-formtarget.html)New         | _blank _self _parent _top _framename_                                                                                                                                                                                                                                 | 规定表示提交表单后在哪里显示接收到响应的名称或关键词。(只适合 type="submit" 和 type="image")                 |
| [height](https://www.runoob.com/tags/att-input-height.html)New                 | _pixels_                                                                                                                                                                                                                                                              | 规定 \<input>元素的高度。(只针对type="image")                                            |
| [list](https://www.runoob.com/tags/att-input-list.html)New                     | _datalist_id_                                                                                                                                                                                                                                                         | 属性引用 \<datalist> 元素，其中包含 \<input> 元素的预定义选项。                                   |
| [max](https://www.runoob.com/tags/att-input-max.html)New                       | _number date_                                                                                                                                                                                                                                                         | 属性规定 \<input> 元素的最大值。                                                         |
| [maxlength](https://www.runoob.com/tags/att-input-maxlength.html)              | _number_                                                                                                                                                                                                                                                              | 属性规定 \<input> 元素中允许的最大字符数。                                                    |
| [min](https://www.runoob.com/tags/att-input-min.html)New                       | _number date_                                                                                                                                                                                                                                                         | 属性规定 \<input>元素的最小值。                                                          |
| [multiple](https://www.runoob.com/tags/att-input-multiple.html)New             | multiple                                                                                                                                                                                                                                                              | 属性规定允许用户输入到 \<input> 元素的多个值。                                                  |
| [name](https://www.runoob.com/tags/att-input-name.html)                        | _text_                                                                                                                                                                                                                                                                | name 属性规定 \<input> 元素的名称。                                                     |
| [pattern](https://www.runoob.com/tags/att-input-pattern.html)New               | _regexp_                                                                                                                                                                                                                                                              | pattern 属性规定用于验证 \<input> 元素的值的正则表达式。                                         |
| [placeholder](https://www.runoob.com/tags/att-input-placeholder.html)New       | _text_                                                                                                                                                                                                                                                                | placeholder 属性规定可描述输入 \<input> 字段预期值的简短的提示信息 。                                |
| [readonly](https://www.runoob.com/tags/att-input-readonly.html)                | readonly                                                                                                                                                                                                                                                              | readonly 属性规定输入字段是只读的。                                                        |
| [required](https://www.runoob.com/tags/att-input-required.html)New             | required                                                                                                                                                                                                                                                              | 属性规定必需在提交表单之前填写输入字段。                                                          |
| [size](https://www.runoob.com/tags/att-input-size.html)                        | _number_                                                                                                                                                                                                                                                              | size 属性规定以字符数计的 \<input> 元素的可见宽度。                                             |
| [src](https://www.runoob.com/tags/att-input-src.html)                          | _URL_                                                                                                                                                                                                                                                                 | src 属性规定显示为提交按钮的图像的 URL。 (只针对 type="image")                                   |
| [step](https://www.runoob.com/tags/att-input-step.html)New                     | _number_                                                                                                                                                                                                                                                              | step 属性规定 \<input> 元素的合法数字间隔。                                                 |
| [type](https://www.runoob.com/tags/att-input-type.html)                        | button  <br>checkbox  <br>color  <br>date  <br>datetime  <br>datetime-local  <br>email  <br>file  <br>hidden  <br>image  <br>month  <br>number  <br>password  <br>radio  <br>range  <br>reset  <br>search  <br>submit  <br>tel  <br>text  <br>time  <br>url  <br>week | type 属性规定要显示的 \<input> 元素的类型。                                                 |
| [value](https://www.runoob.com/tags/att-input-value.html)                      | _text_                                                                                                                                                                                                                                                                | 指定 \<input> 元素 value 的值。                                                      |
| [width](https://www.runoob.com/tags/att-input-width.html)New                   | _pixels_                                                                                                                                                                                                                                                              | width 属性规定 \<input> 元素的宽度。 (只针对type="image")                                  |
## type
| 值                 | 描述                                                |
| ----------------- | ------------------------------------------------- |
| button            | 定义可点击的按钮（通常与 JavaScript 一起使用来启动脚本）。               |
| checkbox          | 定义复选框。                                            |
| colorNew          | 定义拾色器。                                            |
| dateNew           | 定义 date 控件（包括年、月、日，不包括时间）。                        |
| datetimeNew       | 定义 date 和 time 控件（包括年、月、日、时、分、秒、几分之一秒，基于 UTC 时区）。 |
| datetime-localNew | 定义 date 和 time 控件（包括年、月、日、时、分、秒、几分之一秒，不带时区）。      |
| emailNew          | 定义用于 e-mail 地址的字段。                                |
| file              | 定义文件选择字段和 "浏览..." 按钮，供文件上传。                       |
| hidden            | 定义隐藏输入字段。                                         |
| image             | 定义图像作为提交按钮。                                       |
| monthNew          | 定义 month 和 year 控件（不带时区）。                         |
| numberNew         | 定义用于输入数字的字段。                                      |
| password          | 定义密码字段（字段中的字符会被遮蔽）。                               |
| radio             | 定义单选按钮。                                           |
| rangeNew          | 定义用于精确值不重要的输入数字的控件（比如 slider 控件）。                 |
| reset             | 定义重置按钮（重置所有的表单值为默认值）。                             |
| searchNew         | 定义用于输入搜索字符串的文本字段。                                 |
| submit            | 定义提交按钮。                                           |
| telNew            | 定义用于输入电话号码的字段。                                    |
| text              | 默认。定义一个单行的文本字段（默认宽度为 20 个字符）。                     |
| timeNew           | 定义用于输入时间的控件（不带时区）。                                |
| urlNew            | 定义用于输入 URL 的字段。                                   |
| weekNew           | 定义 week 和 year 控件（不带时区）。                          |
# \<textarea>
New：HTML5 中的新属性。

|属性|值|描述|
|:--|:--|:--|
|[autofocus](https://www.runoob.com/tags/att-textarea-autofocus.html)New|autofocus|规定当页面加载时，文本区域自动获得焦点。|
|[cols](https://www.runoob.com/tags/att-textarea-cols.html)|_number_|规定文本区域内可见的宽度。|
|[disabled](https://www.runoob.com/tags/att-textarea-disabled.html)|disabled|规定禁用文本区域。|
|[form](https://www.runoob.com/tags/att-textarea-form.html)New|_form_id_|定义文本区域所属的一个或多个表单。|
|[maxlength](https://www.runoob.com/tags/att-textarea-maxlength.html)New|_number_|规定文本区域允许的最大字符数。|
|[name](https://www.runoob.com/tags/att-textarea-name.html)|_text_|规定文本区域的名称。|
|[placeholder](https://www.runoob.com/tags/att-textarea-placeholder.html)New|_text_|规定一个简短的提示，描述文本区域期望的输入值。|
|[readonly](https://www.runoob.com/tags/att-textarea-readonly.html)|readonly|规定文本区域为只读。|
|[required](https://www.runoob.com/tags/att-textarea-required.html)New|required|规定文本区域是必需的/必填的。|
|[rows](https://www.runoob.com/tags/att-textarea-rows.html)|_number_|规定文本区域内可见的行数。|
|[wrap](https://www.runoob.com/tags/att-textarea-wrap.html)New|hard  <br>soft|规定当提交表单时，文本区域中的文本应该怎样换行。|
# \<button>
New ：HTML5 中的新属性。

| 属性                                                                              | 值                                                                          | 描述                                                                      |
| :------------------------------------------------------------------------------ | :------------------------------------------------------------------------- | :---------------------------------------------------------------------- |
| [autofocus](https://www.runoob.com/tags/att-button-autofocus.html)New           | autofocus                                                                  | 规定当页面加载时按钮应当自动地获得焦点。                                                    |
| [disabled](https://www.runoob.com/tags/att-button-disabled.html)                | disabled                                                                   | 规定应该禁用该按钮。                                                              |
| [form](https://www.runoob.com/tags/att-button-form.html)New                     | _form_id_                                                                  | 规定按钮属于一个或多个表单。                                                          |
| [formaction](https://www.runoob.com/tags/att-button-formaction.html)New         | _URL_                                                                      | 规定当提交表单时向何处发送表单数据。覆盖 form 元素的 action 属性。该属性与 type="submit" 配合使用。        |
| [formenctype](https://www.runoob.com/tags/att-button-formenctype.html)New       | application/x-www-form-urlencoded  <br>multipart/form-data  <br>text/plain | 规定在向服务器发送表单数据之前如何对其进行编码。覆盖 form 元素的 enctype 属性。该属性与 type="submit" 配合使用。 |
| [formmethod](https://www.runoob.com/tags/att-button-formmethod.html)New         | get  <br>post                                                              | 规定用于发送表单数据的 HTTP 方法。覆盖 form 元素的 method 属性。该属性与 type="submit" 配合使用。      |
| [formnovalidate](https://www.runoob.com/tags/att-button-formnovalidate.html)New | formnovalidate                                                             | 如果使用该属性，则提交表单时不进行验证。覆盖 form 元素的 novalidate 属性。该属性与 type="submit" 配合使用。  |
| [formtarget](https://www.runoob.com/tags/att-button-formtarget.html)New         | _blank  <br>_self  <br>_parent  <br>_top  <br>_framename_                  | 规定在何处打开 action URL。覆盖 form 元素的 target 属性。该属性与 type="submit" 配合使用。       |
| [name](https://www.runoob.com/tags/att-button-name.html)                        | _name_                                                                     | 规定按钮的名称。                                                                |
| [type](https://www.runoob.com/tags/att-button-type.html)                        | button  <br>reset  <br>submit                                              | 规定按钮的类型。                                                                |
| [value](https://www.runoob.com/tags/att-button-value.html)                      | _text_                                                                     | 规定按钮的初始值。可由脚本进行修改。                                                      |
# \<select>
New：HTML5 中的新属性。

| 属性                                                                    | 值         | 描述                        |
| :-------------------------------------------------------------------- | :-------- | :------------------------ |
| [autofocus](https://www.runoob.com/tags/att-select-autofocus.html)New | autofocus | 规定在页面加载时下拉列表自动获得焦点。       |
| [disabled](https://www.runoob.com/tags/att-select-disabled.html)      | disabled  | 当该属性为 true 时，会禁用下拉列表。     |
| [form](https://www.runoob.com/tags/att-select-form.html)New           | _form_id_ | 定义 select 字段所属的一个或多个表单。   |
| [multiple](https://www.runoob.com/tags/att-select-multiple.html)      | multiple  | 当该属性为 true 时，可选择多个选项。     |
| [name](https://www.runoob.com/tags/att-select-name.html)              | _text_    | 定义下拉列表的名称。                |
| [required](https://www.runoob.com/tags/att-select-required.html)New   | required  | 规定用户在提交表单前必须选择一个下拉列表中的选项。 |
| [size](https://www.runoob.com/tags/att-select-size.html)              | _number_  | 规定下拉列表中可见选项的数目。           |
# \<option>
| 属性                                                               | 值        | 描述                        |
| :--------------------------------------------------------------- | :------- | :------------------------ |
| [disabled](https://www.runoob.com/tags/att-option-disabled.html) | disabled | 规定此选项应在首次加载时被禁用。          |
| [label](https://www.runoob.com/tags/att-option-label.html)       | _text_   | 定义当使用 <optgroup> 时所使用的标注。 |
| [selected](https://www.runoob.com/tags/att-option-selected.html) | selected | 规定选项（在首次显示在列表中时）表现为选中状态。  |
| [value](https://www.runoob.com/tags/att-option-value.html)       | _text_   | 定义送往服务器的选项值。              |
# \<optgroup>
| 属性                                                                 | 值        | 描述        |
| :----------------------------------------------------------------- | :------- | :-------- |
| [disabled](https://www.runoob.com/tags/att-optgroup-disabled.html) | disabled | 规定禁用该选项组。 |
| [label](https://www.runoob.com/tags/att-optgroup-label.html)       | _text_   | 为选项组规定描述。 |
# \<fieldset>
New ：HTML5 中的新属性。

| 属性                                                                    | 值         | 描述                      |
| :-------------------------------------------------------------------- | :-------- | :---------------------- |
| [disabled](https://www.runoob.com/tags/att-fieldset-disabled.html)New | disabled  | 规定该组中的相关表单元素应该被禁用。      |
| [form](https://www.runoob.com/tags/att-fieldset-form.html)New         | _form_id_ | 规定 fieldset 所属的一个或多个表单。 |
| [name](https://www.runoob.com/tags/att-fieldset-name.html)New         | _text_    | 规定 fieldset 的名称。        |
# \<label>
New：HTML5 新属性。

|属性|值|描述|
|:--|:--|:--|
|[for](https://www.runoob.com/tags/att-label-for.html)|_element_id_|规定 label 与哪个表单元素绑定。|
|[form](https://www.runoob.com/tags/att-label-form.html)New|_form_id_|规定 label 字段所属的一个或多个表单。|
