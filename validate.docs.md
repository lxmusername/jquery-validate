# jquery.validate 插件的使用说明

20170407

https://github.com/DiegoLopesLima/validate


# 使用语法

```javascript
  $( '#form' ).validate();
```

# 可以使用自定义属性设置验证

data-conditional        Accepts one or more indexes separated by spaces 
                        from the `conditional` object that should 
                        contain a the boolean return function.
                        接收 一个或多个 由空格分隔的标记, 该标记定义在 `conditional`
                        对象中. 每一个标记都应该是一个返回 boolean 值的函数.


data-ignore-case        Accepts a boolean value to specify if field is case-insensitive.
                        接收一个 boolean 值, 来指定是否忽略大小写. 

data-mask               Accepts a mask to change the field value to the specified format. 
                        The mask should use the character groups of the regular expression 
                        passed to the `data-pattern` attribute.
                        接收掩码来设定字段中数据的格式. 掩码必须使用 `data-pattern` 属性设置
                        的正则表达式匹配组中的字符. 默认值为 ${ 0 }

data-pattern            Accepts a regular expression to test the field value.
                        接收一个正则表达式, 以测试字段的值.

data-prepare            Accepts a index from the `prepare` object that should contain a 
                        function to receive the field value and returns a new value treated.
                        接收一个定义在 `prepare` 对象中的函数名. 该函数接收字段的数据, 
                        并返回一个转换后的数据.

data-required           Accepts a boolean value to specify if field is required.
                        接收一个 boolean 值, 用于指定是否必须输入. 默认值为 false

data-trim               Accepts a boolean value. If true, removes the spaces from the 
                        ends in the field value. (The field value is not changed)
                        接收一个 boolean 值. 如果为 true, 则移除字段结尾的空格( 字段的值不会改变 )
                        默认为 false

data-validate           You can use the `data-validate` to calling extensions.
                        可以使用 `data-validate` 来调用扩展.



# 参数

conditional             Accepts a object to store functions from validation.
                        设置为一个对象, 来存储验证函数.

filter                  Accepts a selector string or function to filter the validated fields.
                        设置为一个字符串或函数, 来筛选验证字段. 默认值为 *.

nameSpace               A namespace used in all delegates events.
                        命名空间用于所有的代理事件. 默认为 validate

onBlur                  Accepts a boolean value. If true, triggers the validation when blur the field.
                        接收一个 boolean 值. 如果为 true, 当字段失去焦点的时候触发验证. 默认为 false.

onChange                Accepts a boolean value. If true, triggers the validation when change the field value.
                        接收一个 boolean 值, 如果为真, 字段发生改变的时候触发验证. 默认为 false.

onKeyup                 Accepts a boolean value. If true, triggers the validation when press any key.
                        接收一个 boolean 值. 如果为 真. 在按下任意键的时候触发验证. 默认为 false.

onSubmit                Accepts a boolean value. If true, triggers the validation when submit the form.
                        接收一个 boolean 值. 如果为 真, 在提交表单的时候触发验证.   默认为 true.

prepare                 Accepts a object to store functions to prepare the field values.
                        接收一个对象, 来存储去预处理字段值的函数.

sendForm                Accepts a boolean value. If false, prevents submit the form (Useful to submit forms via AJAX).
                        接收一个 boolean 值. 如果为 false, 阻止表单提交行为( JAJX 提交数据的时候很有用 ). 默认为 true.

waiAria                 Accepts a boolean value. If false, disables WAI-ARIA.
                        接收一个 boolean 值. 如果为 false, 禁用 WAI-ARIA. 默认为 true.


# 回调函数

valid                   Accepts a function to be calling when form is valid. The context (`this`) is the current 
                        verified form and the parameters are respectively `event` and `options`.
                        接收一个函数, 在表单数据有效的时候会被调用. 上下文( `this` )是当前被验证的表单对象. 同时参数是
                        各自的事件 与 选项.

invalid                 Accepts a function to be calling when form is invalid. The context (`this`) is the current 
                        verified form and the parameters are respectively `event` and `options`.
                        接收一个函数, 在表单数据无效的时候会被调用. 上下文( `this` )是当前被验证的表单对象. 同时参数是
                        各自的事件 与 选项.


eachField               Accepts a function to be calling to each field. The context (`this`) is the current 
                        verified field and the parameters are respectively `event`, `status` and `options`.
                        接收一个函数, 每一个字段都会调用该函数. 上下文( `this` )是当前被验证的表单对象. 同时参数是
                        各自的事件, 状态 与 选项.

eachInvalidField        Accepts a function to be calling when field is invalid. The context (`this`) is the current 
                        verified field and the parameters are respectively `event`, `status` and `options`.
                        接收一个函数, 当字段验证失败的时候会调用该函数. 上下文( `this` )是当前被验证的表单对象. 同时参数是
                        各自的事件, 状态 与 选项.


eachValidField          Accepts a function to be calling when field is valid. The context (`this`) is the current 
                        verified field and the parameters are respectively `event`, `status` and `options`.
                        接收一个函数, 当字段验证成功的时候会调用该函数. 上下文( `this` )是当前被验证的表单对象. 同时参数是
                        各自的事件, 状态 与 选项.


# 移除验证

```javascript
  jQuery('#form').validateDestroy();
```

# 修改 validate 的默认值

直接提供 validate 方法参数, 来修改默认的属性

```javascript
  jQuery.validate({
    sendForm: false,
    onKeyup: true
  });
```

# 创建描述

对验证不成功的字段, 可以提供错误描述信息. 操作步骤:

- 提供需要呈现描述信息的容器标签. 例如 div 标签. 同时提供 id, 例如 'textId'
- 在需要验证的标签中使用 data-describedby 属性, 用于指向容器 id.
- 在验证标签中提供 data-description 属性, 并命名.
- 提供对象属性 description. 并提供该对象属性作为验证信息, 该属性名为 data-description 中描述的名字.
- 验证描述信息也为一个对象. 每一个验证条件都是一个对象属性. 用于描述验证失败时的提示文本.

例如:

```html
<form>
	<input type="text" data-describedby="messages" data-description="test" />
	<span id="messages"></span>
</form>
```

```javascript
$('form').validate({
	description : {
		test : {
			required : '<div class="error">Required</div>',
			pattern : '<div class="error">Pattern</div>',
			conditional : '<div class="error">Conditional</div>',
			valid : '<div class="success">Valid</div>'
		}
	}
});
```

# 创建扩展

可以使用 validateExtend 方法来定义扩展, 该扩展名可以利用 data-validate 属性作用与标签中.


```html
<form>
	<input type="text" name="age" data-validate="age" />
</form>
```

```javascript
jQuery('form').validate();

jQuery.validateExtend({
	age : {
		required : true,
		pattern : /^[0-9]+$/,
		conditional : function(value) {

			return Number(value) > 17;
		}
	}
});
```









