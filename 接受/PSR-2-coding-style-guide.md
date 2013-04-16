代码样式规范
==================

本规范是[PSR-1][]基础代码规范的继承和扩展。本规范意图是为了减少不同开发者交叉审查代码时的认知差异。各个成员项目的共性组成了本文的样式规则。当不同的开发者在不同的项目中合作时，将会在这些不同的项目中使用一个共同的标准。 因此，本指南的好处不在于规则本身，而在于共用这些规则。

特性关键词『必须』(MUST)，『禁止』(MUST NOT)，『必要』(REQUIRED)，『将会』(SHALL)，『不会』(SHALL NOT)，『应当』(SHOULD)，『不应』(SHOULD NOT)，『推荐』(RECOMMENDED)，『可以』(MAY)和『可选』(OPTIONAL)在这文档中将被依据[RFC 2119][]标准进行解释。

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/yoozi/fig-standards/blob/zh_CN/接受/PSR-0.md
[PSR-1]: https://github.com/yoozi/fig-standards/blob/zh_CN/接受/PSR-1-basic-coding-standard.md


1. 大纲
-----------

- 代码必须遵守 [PSR-1][]。
- 代码『必须』使用 4 个空格宽度的 Tab 缩进。
- 一行代码长度『应当』是80个字符或者更少，但『不应』超过120个字符。
- 在`namespace`声明下面『必须』有一个空行，并且`use`声明代码块下面也『必须』有一个空行。
- 类的左花括号『必须』放到下一行，右花括号『必须』放在类主体的下一行。
- 方法的左花括号『必须』放在下一行，右花括号『必须』放在方法主体下面。
- 所有的属性和方法『必须』有可见性声明：
    - `abstract`和`final`声明『必须』在可见性之前；
    - `static`声明『必须』在可见性之后。
- 控制结构的关键词『必须』在后面有一个空格； 方法和函数『禁止』有。
- 控制结构的左花括号『必须』放在同一行，右花括号『必须』放在控制主体的下一行。
- 控制结构的左括号后面『禁止』有空格，右括号之前『禁止』有空格。
- 类和方法『必须』添加符合规范的主食。

### 1.1. 示例

本示例包含上面的一些规则简单展示：

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

/**
 *  一句话描述类
 *
 *  在一个空行注释后，详细的类描述由此开始，
 *  主要用于详细说明此类、注意事项等。
 *
 *  通过上面一个新的空行，用于区分和生成两个不同的段落。
 *  
 *
 *  @package    yoozi
 *  @author     Saturn <yangg.hu@yoozi.cn>
 *  @copyright  2013 Yoozi Information Technology Co., Ltd.
 *  @todo       需要完善和重构此代码
 *  @deprecated 本类将在下个版本中弃用，请勿继续调用
 *  @link       http://four.laravel.com/docs/contributing
 */
class Foo extends Bar implements FooInterface
{
     /**
     * 这是一个示例方法
     *
     * @access public
     * @param  string  $a 输入参数1
     * @param  string  $b 输入参数2，可为空
     * @return void
     */
    public function sampleFunction($a, $b = NULL)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    // ------------------------------------------------------------------------
    
    /**
     * 这是另一个示例方法
     *
     * @access public
     * @return void
     */
    final public static function bar()
    {
        // method body
    }
}
```

2. 概括
----------

### 2.1 基础代码规范

代码『必须』遵守 [PSR-1][] 的所有规则。

### 2.2 文件

* 所有的PHP文件『必须』使用Unix LF(换行)作为行结束符。
* 所有PHP文件『必须』以一个空行结束。
* 纯PHP代码的文件关闭标签`?>`『必须』省略。

### 2.3. 行

* 行长度『禁止』有硬限制。
* 行长度的软限制『必须』是120个字符；对于软限制，自动样式检查器『必须』警告但『禁止』报错。
* 行实际长度『不应』超过80个字符；较长的行『应当』被拆分成多个不超过80个字符的后续行。
* 在非空行后面『禁止』有空格。
* 空行『可以』用来改善可读性和区分相关的代码块。
* 一行『不应』多于一个语句。

### 2.4. 缩进

*『禁止』使用直接 Tab 制表符作为缩进方法。
*『必须』使用 4 个*空格宽度*的 Tab 缩进。

需要在 Sublime Text 2 中调整符合本规范的缩进设置，前往菜单栏 `Preferences` => `Setting` 调整缩进默认值：

```
// The number of spaces a tab is considered equal to
"tab_size": 4,

// Set to true to insert spaces when tab is pressed
"translate_tabs_to_spaces": true,

// If translate_tabs_to_spaces is true, use_tab_stops will make tab and
// backspace insert/delete up to the next tabstop
"use_tab_stops": true,
```

调整完毕，请重启编辑器。

> 注意：只用空格，不和制表符混合使用，将会对避免代码差异、补丁、历史和注解中的一些问题有帮助。使用空格还可以使调整细微的缩进来改进行间对齐变得非常简单。

### 2.5. 关键词和 TRUE/FALSE/NULL

* PHP[保留关键字][]『必须』使用小写。
* PHP常量`TRUE`, `FALSE` 和 `NULL`『必须』使用大写。

[保留关键字]: http://php.net/manual/en/reserved.keywords.php

3. Namespace 和 Use 声明
---------------------------------

* 如果存在，`namespace`声明之后『必须』有一个空行。
* 如果存在，所有的`use`声明『必须』放在`namespace`声明的下面。
* 一个`use`关键字『必须』只用于一个声明。
* 在`use`声明代码块后面『必须』有一个空行。

示例:

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... additional PHP code ...

```

4. 类，属性和方法
-----------------------------------

术语『类』指所有的类，接口和特性（traits）。

### 4.1. 扩展和继承

一个类的`extends`和`implements`关键词『必须』和类名在同一行。

类的左花括号『必须』放在下面自成一行；右花括号必须放在类主体的后面自成一行。


```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

`implements`一个列表『可以』被拆分为多个有一次缩进的后续行。如果这么做，列表的第一项『必须』要放在下一行，并且每行『必须』只有一个接口。

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```

### 4.2. 属性

* 所有的属性『必须』声明可见性。
* `var`关键词『禁止』用来声明属性。
* 一个语句『禁止』声明多个属性。
* 属性名称『不应』使用单个下划线作为前缀来表明保护或私有的可见性。
* 一个属性声明看起来应该下面这样的。

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

### 4.3. 方法

* 所有的方法『必须』声明可见性。
* 方法名『不应』只使用单个下划线来表明是保护或私有的可见性。
* 方法名在声明之后『禁止』跟随一个空格。左花括号『必须』放在下面自成一行，并且右花括号『必须』放在方法主体的下面自成一行。左括号后面『禁止』有空格，右括号前面『禁止』有空格。

一个方法定义看来应该像下面这样。 注意括号，逗号，空格和花括号：

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

### 4.4. 方法参数

* 在参数列表中，逗号之前『禁止』有空格，逗号之后『必须』要有一个空格。
* 方法中有默认值的参数必须放在参数列表的最后面。

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

* 参数列表『可以』被分为多个有一次缩进的多个后续行。如果这么做，列表的第一项『必须』放在下一行，并且每行『必须』只放一个参数。
* 当参数列表被分为多行，右花括号和左括号『必须』夹带一个空格放在一起自成一行。

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```

### 4.5. `abstract`，`final`和 `static`

* 如果存在，`abstract`和`final`声明必须放在可见性声明前面。
* 如果存在，`static`声明『必须』跟着可见性声明。

```php
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // method body
    }
}
```

### 4.6. 调用方法和函数

要调用一个方法或函数，在方法或者函数名和左括号之间『禁止』有空格，左括号之后『禁止』有空格，右括号之前『禁止』有空格。函数列表中，逗号之前『禁止』有空格，逗号之后『必须』有一个空格。

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

参数列表『可以』被拆分成多个有一个缩进的后续行。如果这么做，列表中的第一项必须放在下一行，并且每一行『必须』只有一个参数。

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```

5. 控制结构
---------------------

对于控制结构的样式规则概括如下：

- 控制结构关键词之后『必须』有一个空格
- 左括号之后『禁止』有空格
- 右括号之前『禁止』有空格
- 在右括号和左花括号之间『必须』有一个空格
- 代码主体『必须』有一次缩进
- 右花括号『必须』主体的下一行

每个结构的主体『必须』被括在花括号里。这结构看上去更标准化，并且当加新行的时候可以减少引入错误的可能性。

### 5.1. `if`，`elseif`，`else`

一个`if`结构看起来应该像下面这样。注意括号，空格，花括号的位置；并且`else`和`elseif`和前一个主体的右花括号在同一行。

```php
<?php
if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```

关键词`elseif``应该`替代`else if`使用以保持所有的控制关键词像一个单词。


### 5.2. `switch`，`case`

一个`switch`结构看起来应该像下面这样。注意括号，空格和花括号。`case`语句必须从`switch`处缩进，并且`break`关键字（或其他中止关键字）『必须』和`case`主体缩进在同级。如果一个非空的`case`主体往下落空则『必须』有一个类似`// no break`的注释。

```php
<?php
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```

### 5.3. `while`，`do while`

一个`while`语句看起来应该像下面这样。注意括号，空格和花括号的位置。

```php
<?php
while ($expr) {
    // structure body
}
```

同样的，一个`do while`语句看起来应该像下面这样。注意括号，空格和花括号的位置。

```php
<?php
do {
    // structure body;
} while ($expr);
```

### 5.4. `for`

一个`for`语句看起来应该像下面这样。注意括号，空格和花括号的位置。

```php
<?php
for ($i = 0; $i < 10; $i++) {
    // for body
}
```

### 5.5. `foreach`

一个`foreach`语句看起来应该像下面这样。注意括号，空格和花括号的位置。

```php
<?php
foreach ($iterable as $key => $value) {
    // foreach body
}
```

### 5.6. `try`, `catch`

一个`try catch`语句看起来应该像下面这样。注意括号，空格和花括号的位置。

```php
<?php
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}
```

6. 闭包
-----------

* 闭包在声明时`function`关键词之后『必须』有一个空格，并且`use`之前也需要一个空格。
* 左花括号『必须』在同一行，右花括号『必须』在主体的下一行。
* 参数列表和变量列表的左括号之后『禁止』有空格，其右括号之前也『禁止』有空格。
* 在参数列表和变量列表中，逗号之前『禁止』有空格，逗号之后『必须』有空格。
* 闭包带默认值的参数『必须』放在参数列表后面。

一个闭包声明看起来应该像下面这样。注意括号，空格和花括号的位置。

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};
```

参数和变量列表『可以』被分成多个带一次缩进的后续行。如果这么做，列表的第一项『必须』放在下一行，并且一行『必须』只放一个参数或变量。

当最终列表（不管是参数还是变量）被分成多行，右括号和左花括号『必须』夹带一个空格放在一起自成一行。

下面是一个参数和变量列表被分割成多行的示例。

```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};
```

注意如果在函数或者方法中把闭包作为一个参数调用，如上格式规则同样适用。

```php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
```

## 7 注释

所有注释『必须』遵循“[文档块(DocBlock)](http://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_phpDocumentor.howto.pkg.html#basics.docblock)”，从而通过文档生成工具 PHPDocumentor 自动生成 API 文档。 

### 7.1 类注释

每个类、方法（函数）的头部『必须』加入如下代码片段，用来描述类、方法的功能和类别等。

```
/**
 *  类的一句话描述
 *
 *  类的描述、说明、注意事项等
 *
 *  @package     （必填）项目内部英文代号
 *  @author     （必填）英文名 <邮箱>
 *  @copyright   （必填）2013 yoozi.cn
 *  @todo       （可选）需要完善的内容，多个 todo 则在新行创建新的 @todo
 *  @deprecated  （可选）即将在接下来的版本中弃用 
 *  @link       （可选）指向资源链接或文档链接
 */
 ```

### 7.2 方法/函数注释

 ```
 /**
 *  （必填）方法的一句话描述
 *
 *  （可选）方法的描述、说明、注意事项等
 *
 * @todo   security check
 * @access public
 * @param  string
 * @return string
 */
public function xml_encode($str)
 ```

### 7.3 行间注释

通常我们需要对复杂逻辑的代码编写行间注释，以达到提醒其他开发人员、增加代码可读性的作用。

行注释需要注意如下几点：

1. 使用 `//` 双左斜线开启每个行注释，且第一个字符与斜线间保持一个空格的距离。
2. 每行注释不要超过 70 个字符，超过部分请折多行。
3. 使用行注释时，在大的注释块和代码间留一个空行。

```
// break up the string by newlines
$parts = explode("\n", $str);

// A longer comment that needs to give greater detail on what is
// occurring and why can use multiple single-line comments.  Try to
// keep the width reasonable, around 70 characters is the easiest to
// read.  Don't hesitate to link to permanent external resources
// that may provide greater detail:
//
// http://example.com/information_about_something/in_particular/

$parts = $this->foo($parts);
```

### 7.4 方法、函数的注释间隔

不同方法、函数间请使用如下 `注释间隔` 区分开，以此增加代码在阅读上的结构感。此间隔的缩进取决于同级方法、函数的缩进距离。同时，本间隔上下需要分别留一个空行。

```
// ------------------------------------------------------------------------
```

```
 /**
 * 设置经度
 *
 * @access protected
 * @return void
 */
protected function setLongitude()
{
    $this->data['longitude'] = $this->post['longitude'];
}

// ------------------------------------------------------------------------

 /**
 * 设置经度
 *
 * @access protected
 * @return void
 */
protected function setLatitude()
{
    $this->data['latitude'] = $this->post['latitude'];
}
```

## 8 代码布局

### 8.1 类内部方法排序

类方法排序遵循：`public`、`protected`、`private`的顺序。

```
__construct
__destruct
public
protected
private
```

### 8.2 类属性声明的排序

```
public
protected
private
```

### 8.3 行间空行的使用

行间空行的使用是一门艺术，是程序员对代码节奏的控制。说它是艺术，是因为它并没有很好的规律可言。优秀的程序员能够比较好的控制好空行的使用，从而提高代码的可读性。

我的经验：

1. 将逻辑上联系不太紧密的代码块，通过空行分隔开。
2. 不要使用每行一个空行的编码风格。
3. 具体操作请各位自己把握。
4. 每个程序员写满 50 万行代码之后，艺术风格开始显现。:)

下面举个简单的例子：

```
/**
 * Render the final page
 *
 * @access public
 * @return void
 */
public function render()
{
    // Call hook: pre render
    $this->call_pre_render_hook();

    // Iterator all the possible elements handlers
    $handlers = array_keys($this->page_elements);
    foreach($handlers as $handler) {
        $this->{'set_' . $handler}();
    }

    // 信息被删除
    if($this->post['is_deleted']) {
        // 用户删除
        if($post['deleted_by'] == 'user') {
            $this->template->title(lang('posts.is_deleted'))
                ->set_metadata('description', lang('txt_post_deleted'), 'meta')
                ->build('posts/deleted');
            return;
        }

        // 信息已被归档
        show_404();
    }

    // 信息违反规则
    if($this->post['is_abused']) {
        $this->template->title(lang('posts.is_abused'))
            ->set_metadata('description', lang('txt_post_deleted'), 'meta')
            ->build('posts/deleted');
        return;
    }

    // 信息需要人工审核
    if($this->post['is_cursed'] {
        $this->template->title(lang('posts.is_abused'))
            ->build('posts/cursed');
        return;
    }

    // Call hook: before render
    $this->call_post_render_hook();

    // Build and show the final page...
    CI()->template
        ->set_partial('inline_js', 'posts/posts_js')
        ->inject_partial('active_category', $this->post['parent_category']['cate_id'])
        ->set_metadata('og:title', $this->data['title'], 'property')
        ->set_metadata('og:type', 'website', 'property')
        ->set_metadata('og:url', $this->data['post_url'], 'property')
        ->build('posts/posts', $this->data);
}
```

9. 结论
--------------

在该指南中有很多风格的元素和做法有意被忽略掉。这些包括但不局限于：

- 全局变量和全局常量的声明
- 方法声明
- 操作符和赋值
- 行间对齐
- 注释和文档块
- 类名前缀和后缀
- 最佳实践

游子开发团队会不断完善此文档，请各位开发成员持续关注。