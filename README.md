# vl_select2

1. 安装相应的库
2. 引入select2的css样式

:data="list" //select数组, 如果不用ajax, 这个必须
:model.sync="model" //select值, 必须
:placeholder="placeholder"
:allowclear="allowClear"
:multiple="multiple" //多选

//以下4个位ajax专用
:ajax="ajax" //为一个对象, 具体内容请参考select2的ajax相关参数
:escapemarkup="escapeMarkup"
:templateselection="templateSelection"
:templateresult="templateResult"

//详细请看demo.vue的例子
