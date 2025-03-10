---
sidebar: false
---

# 更新日志

## [v1.7.5] 2022.01.13
- 新增`try with resources`语法支持
- 修复在使用`log`的情况下`DEBUG`可能造成线程阻塞的问题
- 修复`mybatis`模式中的部分转义错误
- 修复`finally`代码块在部分情况表现与`Java`不一致的问题
- 修复集合、数组扩展方法`distinct`方法返回值是`Set`的`BUG`
- 优化扩展方法缓存，提升调用扩展方法性能
- 优化单表拦截器`API`，调整`UPDATE`执行时机
- 优化代码提示、错误提示

::: tip 提示

`1.x`版本后续除了修复`BUG`以外不会再新增功能，新功能将在2.x版本中

目前`2.x`分支基本开发完毕，在`1.x`基础上的修改项如下：

- 前台使用`vue3`重写，`UI`细节优化
- 支持显示在线人数，他人正在编辑的接口。
- 后台重构，以便更加方便的添加新功能
- 支持`i18n`国际化（目前完成`60%`）
- 支持定时任务在线配置
- 备份机制重构，支持自动全量备份并从全量备份中还原。
- **移除`assert`模块，改用`assert`语法，正在使用`assert`模块的，强烈建议改为`assert`语法，方便后续升级**
- `ElasticSearch`模块(开发中)
- 解构语法(开发中)

需要体验的可以在[Gitee](https://gitee.com/ssssssss-team/magic-api) 下载源码，自行编译`2.x`分支引入使用。

需要注意的是，`2.x`版本并不完全兼容`1.x`版本，需要从`1.x`版本中导出，再从`2.x`中的界面导入。

另外`2.x`版本尚未稳定，请勿在生产环境中使用。正式版本预计在春节后发布。

:::

## [v1.7.4] 2022.01.04
- 新增`mybatis`语法的`<`和`>`自动转义
- 修复在使用 `ResultProvider` 时识别方法签名不正确的问题
- 修复前端语法解析错误 [I4OGMK](https://gitee.com/ssssssss-team/magic-api/issues/I4OGMK)
- 修复单表`save`时主键`primaryValue`获取不到的问题 [PR39](https://gitee.com/ssssssss-team/magic-api/pulls/39)
- 修复无法给数组赋值的`BUG`
- 修复查询历史记录时可能未释放数据库连接的问题
- 修复重命名分组后上传或推送可能会出现同名分组的`BUG`
- 修复`linq` 多个`left join`结果不正确的`BUG`
- 修复`magic-script`部分情况不兼容`log4j`的问题
- 优化`mybatis`语法和`?{}`不兼容的问题

## [v1.7.2] 2021.12.27
- 新增数组&集合去重函数`distinct(e->e.x)`
- 新增`SQL`后置拦截器 [I4NU79](https://gitee.com/ssssssss-team/magic-api/issues/I4NU79)
- 新增`Class`扩展方法`getName`、`getSimpleName`、`getCanonicalName`
- 新增`Map`到`Bson`的隐式转换，方便调用`mongo`相关`API`
- 修复日志组件溢出时未显示滚动条的问题
- 修复请求体`JSON`属性值类型修改后被还原的问题 [I4N708](https://gitee.com/ssssssss-team/magic-api/issues/I4N708)
- 修复部分运算符优先级不正确的问题
- 修复`linq` 多个`left join`结果不正确的`BUG`
- 修复`::date`未传参数时错误信息不提示的问题
- 修复`...`扩展运算符不支持数组的问题
- 优化正则表达式匹配规则，解决部分情况语句解析不正确的问题
- 优化执行结果显示，保持`JSON`原样输出
- 优化代码提示，解决部分场景无法提示的问题，优化部分代码提示高亮


## [v1.7.1] 2021.11.29
- 新增`http`模块的`exceptBytes`方法，用于返回`byte[]`数据
- 修复并发情况下、`MagicScriptContext`会被共享的问题
- 优化`header`获取，`key`不再区分大小写

## [v1.7.0] 2021.11.22
- 新增支持`HEAD`、`PATCH`请求方法 [I4HSB7](https://gitee.com/ssssssss-team/magic-api/issues/I4HSB7)
- 新增支持`import orgssssssss.magicapi.IoUtils`的方式导包(去掉需要加引号的限制)
- 新增`date_format`函数，支持`LocalDate`、`LocalDateTime`等类型
- 新增`String.replace(pattern, replacement)`方法
- 新增复制接口到其他目录下 [I47FV9](https://gitee.com/ssssssss-team/magic-api/issues/I47FV9)
- 修复搜索结果部分情况高亮不正确的问题
- 修复代码高亮部分情况不正确的`BUG`
- 修复不兼容`spring boot 2.6.0`的问题
- 修复`>`、`>=`、`<`、`<=`等运算符不支持`BigInteger`的问题
- 修复`log`模块获取接口名失败时会出现异常的`BUG`
- 优化`collection.group`的`map key`顺序
- 优化代码提示、优化`import`提示，提示可自动导包
- 优化页面加载速度(缩小`/magic/web/classes.txt`的大小)
- 优化代码去除不必要的`ThreadLocal`
- 优化代码编辑器选中样式，修复串位的问题


## [v1.6.4] 2021.11.08
- 新增测试时显示`Response Header`
- 新增支持调用`map`中的`lambda`函数
- 新增接口选项：`不接收未经定义的参数`
- 修复`lambda`调用自身时出现的作用域混乱的问题
- 修复`Oracle`执行`insert`时出现的类型转换异常
- 修复全局搜索部分情况会请求失败的问题
- 优化编辑器字体样式，使用`JetBrains Mono`字体，支持连字
- 优化`mybatis`的`<trim>`在部分情况时无法去除后缀的问题
- 优化分页参数获取，改为配置成表达式，方便从`body`中获取
- 优化拖拽目标节点能突出显示 [I48MQM](https://gitee.com/ssssssss-team/magic-api/issues/I48MQM)
- 优化移动接口后定位混乱的问题
- 优化模板字符串内的代码提示
- 优化错误信息显示
- 优化日志显示

## [v1.6.3] 2021.11.01
- 新增脚本默认数据源的配置功能 [I47VQF](https://gitee.com/ssssssss-team/magic-api/issues/I47VQF)
- 修复`LINQ`的`offset`设置错误
- 修复在编辑器中下载`json`文件时会被识别成`json`结果的问题
- 修复未在编辑器配置`json`结构时，请求携带`RequestBody`造成`body`为`null`的`BUG`
- 修复`json`属性值类型修改后被还原问题
- 修复`mybatis`的部分解析错误 [I4FHWA](https://gitee.com/ssssssss-team/magic-api/issues/I4FHWA) [I4FHT3](https://gitee.com/ssssssss-team/magic-api/issues/I4FHT3)
- 优化`selectValue`方法，改为取第一行第一列
- 优化`selectOne`方法，改为只取第一行
- 优化分页`count`语句，去除`order by`
- 优化代码提示，优化`import`提示
- 优化错误提示，优化变量作用域读写
- 优化编辑器的部分快捷键，修复部分快捷键冲突的问题
- 升级`monaco-editor`至`0.29.1`

## [v1.6.1] 2021.10.26
- 修复设置参数类型无效的问题
- 优化代码提示、悬浮提示、参数提示

## [v1.6.0] 2021.10.25
- **新增`mybatis` `if`、`where`、`set`、`foreach`、`trim`等标签写法**
- 新增`db.select(sqlOrXml,Map)`、`db.page(sqlOrXml,Map)`等方法，支持传入变量信息
- 新增`new_array(String ... items)`、`new_array(int ... items)`等方法
- 修复在配置`magic-api.response`后，参数验证未通过时出现的空指针异常
- 修复`request`模块部分情况获取不到`HttpServletRequest`的问题
- 修复进入断点后，取消断点无效的问题
- 修复在调用`lambda`时，参数与形参个数不一致会产生异常的`BUG`
- 修复异步调用函数时`context`可能混乱的问题
- 修复在递归调用时，变量作用域发生混乱的问题
- 修复`DEBUG`模式部分情况会编译失败的问题
- 优化`?.`操作符，当找不到属性时直接返回`null`不在抛出异常
- 优化在使用`::`转数值时，自动`trim`处理

## [v1.5.3] 2021.10.18
- 新增支持编译缓存容量配置
- 新增单表`API`操作拦截器
- 新增是否持久化返回结果的配置
- 新增编辑器日志保留最多条数配置
- 修复`DEBUG`时`BigDecimal`类型显示不正确的问题
- 修复函数中`log`模块打印的日志`logger name`不正确的问题
- 修复单个表达式中包含`lambda`会编译出错的问题
- 修复编辑器部分组件双向绑定失效的问题
- 修复`page`方法会打印两次`count`语句的问题
- 优化`?.`操作符，支持多级嵌套
- 优化`SQL`参数读取性能
- 优化最近打开对话框的样式

## [v1.5.2] 2021.10.12
- 新增请求参数、`Header`支持`Date`类型
- 修复`import`可能出现的编译错误


## [v1.5.1] 2021.10.11
- 新增自动打开上次未关闭的`tab`页的功能
- 新增`db.page(countSql,sql)`方法
- 修复在某些情况读取`Cookie`会出现空指针异常的`BUG`
- 修复历史记录一直显示`guest`的`BUG`
- 修复历史记录修改时间可能不显示的`BUG`
- 修复在配置自动导入`log`模块时可能发生的空指针异常
- 修复`log`模块代码提示错误的问题


## [v1.5.0] 2021.10.08
- 新增`SQL`参数类型转换器`::sql('clob')`
- 新增请求拦截器方法`afterCompletion`
- 新增集合扩展方法`find`、`findIndex`、`concat`、`toMap`
- 新增`UI`对话框最近打开功能
- 新增`UI`函数、接口快速定位
- 新增`SQL`日志打印配置
- 新增单表`API`的`primary(String, Function)` 方法，用于惰性设置主键值
- 新增单表`API`的`NamedTable.clone`、`Where.clone` 方法
- 修复在未定义变量时，可能造成的变量作用域混乱的问题
- 修复在调用第三方脚本引擎时部分变量丢失的`BUG`
- 修复在有`BigDecimal`类型参与运算时，精度可能不正确的问题
- 修复双重循环`break`会出现死循环的`BUG`
- 修复`linq`中`left join`结果不正确的问题
- 修复`linq`中`having`语句不生效的问题
- 修复部分操作符可能无法匹配类型的问题
- 修复脚本可能出现的`OOM`的`BUG`
- 修复调用函数时，传入`lambda`可能造成的变量作用域混乱的问题
-  修复递归调用时，变量读写混乱的`BUG`
- 优化`log`模块日志显示，将类名改为接口+路径
- 优化历史记录显示，增加显示修改人
- 优化代码格式化，解决不支持`1l`、`1m`、`1d`等写法的问题
- 优化测试数据源连接失败的日志
- 优化`map`类型动态`key`值的写法，由`$key`改为`[key]`
- 优化错误提示，更准确的行列号定位
- 优化`UI`关闭按钮样式
- 文档内容补充以及优化
- `magic-api.backup-config.database`变更为`magic-api.backup-config.datasource`

## [v1.4.5] 2021.09.22
- 新增创建数组方法
- 新增支持设置字体和字号
- 新增`NamedTable`、`Where`类的`page(limit, offset)`方法
- 修复`async`语句不是多线程执行的问题
- 修复在配置禁止导出时，执行导出未弹框显示无权限的`BUG`
- 修复函数中出现异常，错误会混乱的问题
- 修复高版本`JDK`无法创建`List`的问题
- 修复可变参数无法传递数组的`BUG`
- 修复在调用可变参数的方法时，可能出现的空指针的`BUG`
- 修复在变量重名的情况下`SQL`中可能获取不到参数的`BUG`
- 修复模块默认会被自动导入的问题
- 修复在`safari`浏览器下打开空白的问题
- 优化在锁定时，不在自动保存
- 优化`import`语句在找不到类时抛出异常，不在返回`NULL`
- 优化代码提示，修复常量不能提示的问题，优化错误提示

## [v1.4.3] 2021.09.13
- **新增接口&函数锁定和解锁功能**
- 新增前端配置项，可配置驱动类、数据源类型、接口选项、分组选项的默认选项
- 新增支持复制分组功能
- 新增允许替换默认方言实现
- 修复在配置`baseURL`为`/`开头时的拼接错误
- 修复`DEBUG`时修改断点无效的问题
- 修复含有`finally`代码块可能会编译出错的`BUG`
- 修复`NULL`值在部分情况获取不正确的问题
- 修复循环数组时，获取下标不正确的`BUG`
- 修复`LINQ`调用时变量作用域错乱的`BUG`
- 修复当对象为空调用方法时会调用函数的问题
- 优化`Swagger`文档生成，固化`operationId`参数
- 优化`JSON`序列化，解决`DEBUG`时的`JSON`序列化异常
- 优化错误提示

## [v1.4.2] 2021.09.06
- 修复`db`模块的`withBlank`在`update`时失效的问题
- 修复部分情况编译出现的空指针异常
- 修复字符串转义符未生效的问题
- 修复上下文错乱的问题 [I48F0L](https://gitee.com/ssssssss-team/magic-api/issues/I48F0L)
- 优化代码格式化，修复部分情况格式化不正确的问题
- 移除非`DEBUG`期间的日志


## [v1.4.1] 2021.09.01
- 新增调用函数的方法。
- 修复`DEBUG`期间部分`JSON`结果无法序列化的问题。
- 修复无法调用动态方法的`BUG`
- 修复脚本中包含文本块格式化代码时结果不正确的问题
- 修复刚新建的分组不能修改的问题
- 优化历史记录显示顺序
- 优化`DEBUG`时`null`值的显示
- 优化在未开启`UI`的情况下，还会推送日志消息的问题
- 优化逻辑删除，支持`int`类型的逻辑删除值。 
- 优化`DEBUG`时的变量显示顺序
- 优化日志显示，多行日志收缩显示
- fix [I47QH4](https://gitee.com/ssssssss-team/magic-api/issues/I47QH4) [I47VNI](https://gitee.com/ssssssss-team/magic-api/issues/I47VNI)

## [v1.4.0] 2021.08.30
- **优化脚本执行性能(使用`asm`编译字节码后执行)**
- 新增`LINQ`语法：`limit` `offset`
- 新增支持`throw`语法
- 新增支持定义数值时使用`_`分隔
- 新增支持定义二进制、十六进制定义数值`0b111000`、`0xff`
- 新增支持`let`、`const`，以及指定类型的方式定义变量
- 新增支持模板字符串语法 ``` `hello:${name}` ```
- 新增支持数组、集合访问超出范围时直接返回`null`，不在抛出异常。
- 新增集合扩展方法`first`、`last`方法，数组增加`size`方法
- 新增`db`模块方法：`count`、`exists`、`exclude`、`excludes`
- 新增非`DEBUG`期间日志显示
- 新增支持点击鼠标滚轮关闭`tab`页
- 修复在验证移动接口、函数时，获取的分组`ID`不是新值的问题
- 修复分组导出内容不正确的问题
- 修复测试带有`RequestBody`时无法上传文件的问题
- 修复脚本中包含文本块格式化代码时结果不正确的问题
- 修复`lambda`格式化不兼容`->`的问题
- 修复`iframe`跨域情况下页面不显示的问题
- 优化`DEBUG`时变量信息的结构查看
- 优化页面字体，字间距，更换`LOGO`、暗色皮肤下异常日志颜色
- 优化代码提示，修复部分场景语法解析错误造成的错误提示
- 优化`Swagger`文档顺序，将`magic-api`生成的接口调至第一位
- 优化文档结构

## [v1.3.9] 2021.08.16
- 新增支持在测试时上传文件
- 新增`db`模块更新空值的方法`withBlank`
- 修复`db`模块在切换数据后缓存设置失效的`BUG`
- 修复部分场景无法查看异常信息的问题：将异常信息改为`WebSocket`通讯
- 修复数据源必填验证不正确的问题
- 修复全量推送或上传后`id`发生变化导致后续不能增量推送或上传的问题
- 优化代码提示，修复部分场景无法提示的问题
- 优化滚动条样式（美化在火狐浏览器中的样式）
- 优化复选框样式（解决部分浏览器复选框错位的问题）
- 优化`UI`数据源编辑页面宽度
- 优化代码提示，支持`asm`分支的`throw`语句

### 其它更新
- 新增支持`throw`语法（`asm`分支）
- 修复`asm`分支部分场景变量作用域不正确的`BUG`
- 修复`asm`分支不能`DEBUG`的问题
- 修复`asm`分支获取异常位置不正确的问题
- 修复`asm`分支可能出现的`ClassNotFoundException`

::: tip 提示
  使用`magic-script` `asm`分支方法如下：
```xml
<dependency>
    <groupId>org.ssssssss</groupId>
    <artifactId>magic-api-spring-boot-starter</artifactId>
    <version>1.3.9</version>
    <exclusions>
        <exclusion>
            <groupId>org.ssssssss</groupId>
            <artifactId>magic-script</artifactId>
        </exclusion>
    </exclusions>
</dependency>
<dependency>
    <groupId>org.ssssssss</groupId>
    <artifactId>magic-script</artifactId>
    <version>1.5.0-beta4</version>
</dependency>
```
:::


## [v1.3.8] 2021.08.11
- 修复`asm`分支不支持`DEBUG`的`BUG`
- 修复`asm`分支异常打印可能出现空指针的问题
- 修复未配置数据源时无法启动的问题
- 优化代码提示，解决部分场景提示不正确的问题
- 优化`UI`布局，将接口选项中的+/-移动至左侧

::: tip 提示
使用`magic-script` `asm`分支方法如下：
```xml
<dependency>
    <groupId>org.ssssssss</groupId>
    <artifactId>magic-api-spring-boot-starter</artifactId>
    <version>1.3.8</version>
    <exclusions>
        <exclusion>
            <groupId>org.ssssssss</groupId>
            <artifactId>magic-script</artifactId>
        </exclusion>
    </exclusions>
</dependency>
<dependency>
    <groupId>org.ssssssss</groupId>
    <artifactId>magic-script</artifactId>
    <version>1.5.0-beta3</version>
</dependency>
```
:::

## [v1.3.7] 2021.08.09
- 新增事件日志`Tab`页
- 新增保存成功消息提示
- 修复集群环境下，修改接口名字可能未同步的`BUG`
- 修复无法测试`druid`数据源链接的问题
- 修复在调用Java原生方法只有一个参数且是可变参数时，传入数组参数未被正确处理的`BUG`
- 修复在结果预览中文件下载未显示文件名的问题
- 修复`responseBody`属性拷贝丢失，受执行时浅拷贝导致设置了`BaseDefinition`的`name`导致`Swagger`文档生成影响的`BUG`
- 修复`swagger`文档必填字段未显示的问题
- 升级`commons-compress`至1.21
- 优化`UI`底部布局，将右侧按钮挪至左侧，调整窗口最小高度，禁止拖动推送窗口。
- 优化代码提示、优化代码高亮，兼容`asm`分支
- 优化代码，兼容从低版本升级上来的参数验证、文档生成。兼容`magic-script`的`asm`分支

### 其它更新
- 新增支持定义数值时使用`_`分隔(`magic-script` `asm` 分支)
- 修复`magic-script` `asm`分支中未显示错误信息的问题

::: tip 提示
使用`magic-script` `asm`分支方法如下：
```xml
<dependency>
    <groupId>org.ssssssss</groupId>
    <artifactId>magic-api-spring-boot-starter</artifactId>
    <version>1.3.7</version>
    <exclusions>
        <exclusion>
            <groupId>org.ssssssss</groupId>
            <artifactId>magic-script</artifactId>
        </exclusion>
    </exclusions>
</dependency>
<dependency>
    <groupId>org.ssssssss</groupId>
    <artifactId>magic-script</artifactId>
    <version>1.5.0-beta2</version>
</dependency>
```
:::

## [v1.3.6] 2021.08.02
- 新增注释补全功能
- 增加`not_blank`、`not_null`、`is_null`、`is_blank`、`current_timestamp`、`print`等相关函数
- 修复未改动脚本时无法保存接口的`BUG`
- 修复注销不应该验证需要登录的问题
- 修复文件参数必填验证失效的`BUG`
- 修复在使用过程中`Token`失效后未显示登录框的问题
- 修复无法删除接口的`BUG`
- 修复`Body`参数在编辑后丢失配置信息的问题
- 修复`Redis`模块部分场景无法注册模块的问题
- 修正删除接口的权限配置错误
- 修复定义`async`、`select` 字符串时被解析成语句的`BUG`
- 修复`LINQ` `left join` 缓存不正确的问题 [I42W1F](https://gitee.com/ssssssss-team/magic-api/issues/I42W1F)
- 修复引用`actuator`组件可能造成的重复注册接口的问题 [I42UYG](https://gitee.com/ssssssss-team/magic-api/issues/I42UYG)
- 优化`http`模块注册，解决某些场景冲突导致无法启动的问题
- 优化状态条显示，解决一直显示`开始测试...`的问题

::: tip 提示
此版本兼容了`magic-script`的`asm`分支，`asm`分支为会将脚本部分编译为字节码运行。

此外还额外支持了`let`、`const`定义变量，以及模板字符串

使用方法如下：
```xml
<dependency>
    <groupId>org.ssssssss</groupId>
    <artifactId>magic-api-spring-boot-starter</artifactId>
    <version>1.3.6</version>
    <exclusions>
        <exclusion>
            <groupId>org.ssssssss</groupId>
            <artifactId>magic-script</artifactId>
        </exclusion>
    </exclusions>
</dependency>
<dependency>
    <groupId>org.ssssssss</groupId>
    <artifactId>magic-script</artifactId>
    <version>1.5.0-beta1</version>
</dependency>
```
:::

## [v1.3.5] 2021.07.26
- [增加Boolean类型的参数定义、`header`定义 PR27](https://gitee.com/ssssssss-team/magic-api/pulls/27)
- 新增备份最大保留天数配置
- 新增备份存储方式配置
- 修复在验证`Body`时，无法修改数组值类型的`BUG`
- 修复`JS`无法识别`JSON`数值具体类型的问题
- 修复修改分组时报空指针的`BUG`
- 修复在`import`接口、函数时，内部使用`exit`未正确返回的问题
- 修复上传时分组冲突检测不正确的BUG
- 修复语法高亮中注释未被正确高亮的问题
- 优化备份判断逻辑，修改为只有脚本部分有变动时才备份。
- 优化`UI`数据源`Dialog`
- [优化`header`的`get`方法，解决无法修改`header`参数值类型的问题 PR28](https://gitee.com/ssssssss-team/magic-api/pulls/28)

## [v1.3.4] 2021.07.19
- 弃用`SSE`改为`WebSocket`通讯，同时支持集群`DEBUG`能力 [#I3ZL4B](https://gitee.com/ssssssss-team/magic-api/issues/I3ZL4B)
- 新增`assert`语法，用于辅助校验参数。[#I3ZL4Q](https://gitee.com/ssssssss-team/magic-api/issues/I3ZL4Q)
- 新增支持`import "xxx.xxx.*"`的语法，导包更方便。[#I3ZL4O](https://gitee.com/ssssssss-team/magic-api/issues/I3ZL4O)
- 新增单表`API`逻辑删除功能 [#I40L8P](https://gitee.com/ssssssss-team/magic-api/issues/I40L8P)
- 新增提取代码中的`TODO`、`FIXME`的功能 [#I3ZL3W](https://gitee.com/ssssssss-team/magic-api/issues/I3ZL3W)
- 新增集合扩展去重函数`distinct`
- 修复在`knife4j`中参数默认值未显示的问题 [#I40BG2](https://gitee.com/ssssssss-team/magic-api/issues/I40BG2)
- 修复集合`push`函数未生效的`BUG` [#I40NP7](https://gitee.com/ssssssss-team/magic-api/issues/I40NP7)
- 修复`magic-script`中部分表达式优先级不正确造成的语法解析错误。
- 优化`magic-script`中的关键词检查，去除不必要的检查造成的语法解析错误。
- 优化在接口&函数未保存时，在上方tab页显示`*`号，保存后消失 [#I3ZL41](https://gitee.com/ssssssss-team/magic-api/issues/I3ZL41)
- 优化远程推送的密钥字段，采用`password`控件 [#I3ZL48](https://gitee.com/ssssssss-team/magic-api/issues/I3ZL48)
- 优化接口&函数&数据源加载，增加`Loading`、无数据提示 [#I3ZSTI](https://gitee.com/ssssssss-team/magic-api/issues/I3ZSTI) [#I3ZSTE](https://gitee.com/ssssssss-team/magic-api/issues/I3ZSTE)
- 优化顶部Tab页可拖动排序 [#I3ZL47](https://gitee.com/ssssssss-team/magic-api/issues/I3ZL47)
- 优化新增分组后自动定位到该位置 [#I3ZSTG](https://gitee.com/ssssssss-team/magic-api/issues/I3ZSTG)
- 优化结果预览功能，强化非`JSON`结果的预览 [#I3ZL4J](https://gitee.com/ssssssss-team/magic-api/issues/I3ZL4J)
- [PR !23 更加精准的端口读取和添加 magic-api showUrl 配置提示](https://gitee.com/ssssssss-team/magic-api/pulls/23)
- [PR !26 支持gp数据库方言 与PostgreSQL一致](https://gitee.com/ssssssss-team/magic-api/pulls/26)


## [v1.3.3] 2021.07.12
- 新增复制相对路径功能
- 新增注释中的`TODO`、`FIXME`高亮
- 修复推送重命名后的接口未被正确同步的`BUG`
- 修复`Swagger`文档不显示`ResponseBody`的问题
- 修复全局搜索中关键字高亮不正确的`BUG`
- 修复不回显`RequestBody`、`ResponseBody`的注释、验证信息的`BUG`
- 修复全局搜索中有时展示不出代码的`BUG`
- 修复左侧树复制接口时不能弹出编辑框的`BUG`
- 修复分组下没有接口时无法被搜索的`BUG`
- 修复拖拽左侧菜单后右侧编辑器大小未自适应的问题
- 优化`UI`权限配置，细化到分组&接口&函数&数据源上
- 优化全量推送&上传模式的逻辑，改为强一致实现。
- 优化顶部`tab`页，使其切换时始终展示在视野中
- 优化粘贴`RequestBody`时，自动对`key`添加双引号
- 优化代码提示新增方法参数、返回值说明
- 优化全局搜索对话框，隐藏滚动条、修正显示范围

## [v1.3.2] 2021.07.08
- 新增`PUSH`权限配置
- 修复推送需要验证登录的`BUG`
- 修复单表`API`中`in`方法拼接`SQL`不正确的`BUG`
- 修复修改分组名称可能出现的空指针异常
- 修复编辑器不显示`RequestBody`的问题
- 修复编辑器中请求方法全部显示为`GET`的`BUG`
- 优化部分`UI`中的英文，改为中文描述

## [v1.3.1] 2021.07.05
- 新增支持自定义选择接口推送和导出 [#I3TRT4](https://gitee.com/ssssssss-team/magic-api/issues/I3TRT4)
- 新增国产化数据库人大金仓kingbase方言适配 [#I3YCN2](https://gitee.com/ssssssss-team/magic-api/issues/I3YCN2)
- 新增主动刷新功能，用于在未开启集群配置且使用同一个存储不能同步的问题。
- 修复`DE`BUG``会造成多次验证的`BUG`
- 修复设置参数类型不生效的`BUG`
- 优化UI样式，将右上角不常用的图标移至右下角、以及左侧菜单优化

## [v1.3.0] 2021.06.28
- 新增`RequestBody`文档注释、属性校验，`ResponseBody` 文档注释
- 新增`response`模块的`getOutputStream`方法
- 新增`UI`配置项`defaultExpand`，用于配置是否默认展开
- 修复上传时由于读取顺序无序导致结果错乱的问题
- 修复`Swagger`文档注释被名称覆盖的问题
- 修复在调用`save`时，`Oracle`数据库可能出现空指针的`BUG`
- 优化`UI`上传接口对话框，全量上传时增加确认框
- 优化`UI`左侧树，新增`defaultExpand`默认是否展开配置
- 优化`UI`复制路径功能，不在弹出对话框提示。
- 优化`Swagger`文档生成，兼容`knife4j`处理
- 优化匹配数据库方言的方式，解决部分驱动不支持获取`URL`的问题

## [v1.2.2] 2021.06.15
- 新增自定义构建异常结果接口
- 新增启动后接口`URL`打印
- 修复在删除分组后，无法上传该分组的`BUG`
- 修复可能存在的循环引用的`BUG`
- 优化`UI`左侧树搜索，不在区分大小写
- 优化单表`API`，新增支持`delete`方法、`save`方法增加`beforeQuery`参数，用于判断数据是否存在的判断标准

## [v1.2.1] 2021.05.31
- 新增远程推送功能
- 新增注销登录功能
- 修复上传不支持数据源的问题
- 修复搜索未验证是否登录的问题
- 优化`UI`右键菜单，增加图标
- 优化上传逻辑，分为增量模式和全量模式

## [v1.2.0] 2021.05.24
- **新增支持集群部署**
- 新增数据源增删改查接口，可持久化保存数据源
- 修复在拦截器中抛出异常时，界面不显示结果的`BUG`
- 修复`Oracle`查询单行单列值时，返回值带有`ROW_ID`的问题
- [PR !13 解决swagger文档使用knife4j时不兼容，无法显示接口详情的问题](https://gitee.com/ssssssss-team/magic-api/pulls/13)
- [PR !14 [!]fix swagger文档使用knife4j时接口文档中query类型参数的数据类型显示不正确的问题（不影响swagger原生UI）](https://gitee.com/ssssssss-team/magic-api/pulls/14)
- 优化前端代码，在请求时剔除无用字段，避免一些可能存在的错误。
- 优化后端代码，删除`@Deprecated`方法
- 迁移`magic-api-spring-boot-starter`、`magic-editor`到`magic-api`仓库中

## [v1.1.3] 2021.05.18
- 新增获取函数、接口详情的接口
- 修复无法创建分组的`BUG`

## [v1.1.2] 2021.05.17
- 新增支持配置`json`结果`code`值
- 新增接口、函数、分组的增删改查接口。
- 修复在测试、删除数据源时未释放链接的问题
- 修复分组无法移动的问题
- 优化设置`RequestEntity`时机
- 优化构建分页结果接口，增加`RequestEntity`、`Page`参数
- 优化对`SpringBoot`的兼容性
- 优化UI样式，修复部分样式错位问题

## [v1.1.1] 2021.05.06
- 修复调用`context.get`时可能获取不到变量值的问题
- 修复`http`模块在某些情况下无法携带`hedaer`的`BUG`
- 修复无法创建`druid`数据源的`BUG`
- 修复在以组件方式引入时可能造成重复保存的`BUG`
- 优化`SQL`拦截器,增加参数`RequestEntity`
- 优化`Swagger`中的`RequestBody`改为非必填


## [v1.1.0] 2021.04.19
- 新增分组选项、分组路径变量配置
- 新增`json`、`stringify` 转换器，用于字符串转`JSON`和`JSON`转字符串
- 新增全局搜索功能
- 新增阻止页面关闭的配置
- 新增数据源参数`maxRows`
- 新增`http`模块(基于`RestTemplate`)
- 新增单表`API`方法`orderBy`、`groupBy`
- 新增单表`API`方法`notNull`、`notBlank` 用于过滤`where`中非空参数
- 修复断点会自动清除的`BUG`
- 修复使用`redis`存储时无法删除接口的`BUG`
- 修复脚本不支持`new`内部类的问题
- 优化测试逻辑，测试时将`serverURL`参数当为`baseURL`，不在拼接处理
- 优化`swagger`文档生成，支持`path`参数
- 优化`UI`样式，显示接口的请求方法

## [v1.0.2] 2021.04.12
- 新增示例项目 [magic-api-example](https://gitee.com/ssssssss-team/magic-api-example)
- 新增错误提示超时时间配置
- 新增单表API`delete`方法
- 修复`oracle`执行插入无法返回主键的问题
- 修复单表API中`save`方法返回的不是主键的问题
- 优化代码提高兼容性，不在强制要求配置数据源

## [v1.0.1] 2021.04.06
- 新增`uuid`函数
- 新增任意值到`Boolean`类型的隐式转换
- 修复无法访问静态内部类的问题
- 修复无法给没有初始值的变量进行赋值的`BUG`
- 修复无法将接口移动到接口分组上(没有分组路径)的`BUG`
- 修复移动接口可能造成接口重复的问题
- 修复编辑器可能无法显示内容的`BUG`
- 修复编辑器中`RequestBody`可能被覆盖的问题
- 修复在使用达梦数据库时，无法使用数据库存储的问题
- 修复在使用文件存储时无法创建数据源的`BUG`
- 优化方法调用的悬浮提示
- 优化带有可变参数的代码提示
- 优化单表API，列名现在可以从驼峰命名转为下划线
- 优化单表API的`save`方法，在执行插入时可设置主键值
- 优化单表API的主键非空判断逻辑，由`!=null`转为`notBlank`
- 优化集合函数`filter`，不在强制要求返回`Boolean`类型
- 优化部分代码，提取一些魔法字符串到常量类中

## [v1.0.0] 2021.03.29
- 新增自定义用户名密码登录验证
- 修复`函数列表`、`数据源管理` 拖动样式不正确的问题
- 修复解析文件内容时因意外的格式造成的解析错误
- 修复`readonly`在`db`、`redis`存储不生效的问题
- 修复数据源管理中异常信息显示不正常的`BUG`
- 修复无法为`JavaBean`属性赋值的`BUG`
- 修复在`RequestBody`填写错误时，无法执行测试的`BUG`
- 修复在配置`Long`转`String`时，历史记录时间显示不正确的问题
- 优化`UI`权限配置，使其更细致化
- 优化获取接口选项值的接口
- 优化前端读取配置的逻辑，使其更实用
- 优化前端验证逻辑，路径变量中的`value`为必填
- 优化脚本备份逻辑，减少备份次数
- 优化部分代码，兼容`Gson`，使其不在报错

## [v1.0.0-beta2] 2021.03.22
- **新增动态数据源管理(可在页面动态修改数据源)**
- **新增路径变量验证**
- 修复打成`jar`包后无法导出接口的`BUG`
- 修复复选框未回显的问题
- 修复在新增函数时，参数类型不回显的问题
- 修复不能关闭跨域配置的`BUG`
- 修复打包后无法读取`js`配置文件的问题
- 修复权限配置不正确的`BUG`
- 修复配置抛出异常无效的`BUG`
- 优化`JSON`构建接口，参数统一封装，减少方法
- 优化读取资源逻辑，增强数据库兼容性
- 优化日志打印，方便排除错误
- 优化模拟测试，增加支持路径变量配置

## [v1.0.0-beta1] 2021.03.18
### 新增功能
- 新增存储资源配置项（可在配置文件中配置存储方式）
- 新增强制只读模式
- 新增单表操作`API`
- 新增接口参数类型、默认值配置
- 新增接口参数验证、`header`验证功能(支持必填、表达式和正则验证)
- 新增自定义响应结构配置（可在配置文件中配置响应结构）
- 新增语法 **\`\`\`language \`\`\`** ，可执行对实现`JSR223`规范的脚本语言，也可自定义
- 新增接口导入、导出功能
- 新增跨域开关配置，现在可以关闭跨域功能
### `BUG`修复
- 修复历史记录排序不正确的问题
- 修复可能无法加载后台设置的编辑器配置的`BUG`
- 修复缓存在指定有效期时可能无效的`BUG`
- 修复驼峰命名转换在列名全大写时未转换的问题
- 修复三元表达式在赋值语句中表现不正确的`BUG`
### 优化
- 优化代码编辑器，增加是否要自动保存的配置
- 优化变量定义，现在可以省略赋值语句。
- 优化`Json`构建接口，增加`RequestEntity`参数可获取`request`、`response`、接口等相关参数及配置
- 优化数据库、`redis`资源读取逻辑，加快启动速度
- 优化`linq`语法，`linq`关键字不在区分大小写
- 优化`UI`界面，替换部分图标，增加`tab`页图标，方便区分`接口`、`函数`
- 优化方法调用，`lambda`表达式可隐式转换为`Java`的`FunctionalInterface`接口
- 优化方法调用，允许调用接口的`default`方法

## [v0.7.1] 2021.03.01
- 新增数据库存储、`Redis`存储方案
- 新增支持可自定义存储方式
- 新增屏蔽检测更新的选项
- 新增接口执行时间`executeTime`
- 修复无法自动注入`db`模块的`BUG` [I38LDB](https://gitee.com/ssssssss-team/magic-api-spring-boot-starter/issues/I38LDB)
- 修复`swagger`无法测试带有`RequestBody`的请求
- 修复类型转换时值为0的问题 [I398ND](https://gitee.com/ssssssss-team/magic-api/issues/I398ND)
- 修复在省略`as`的情况下，代码提示不正确的问题
- 修复切换脚本时，代码编辑器滚动条定位不正确的问题
- 优化生成`swagger`文档，显示接口描述
- 优化读取资源逻辑，兼容`Spring Boot` `2.1.x` `2.2.x` `2.3.x` `2.4.x`
- 优化代码，增加异常日志输出，方便定位问题

## [v0.7.0] 2021.02.22
- **弃用数据库存储方案,改为文件存储**
- 新增`===`、`!==` 比较运算符
- 新增`::int`、`::double`等类型转换语法
- 修复无法获取接口选项的问题
- 修复`#{}`结果为`null`时未拼接占位符的问题
- 优化脚本调用逻辑，可调用java方法非静态方法
- 优化`import`命令，在特定场景下可省略`as`
- 优化`swagger`支持参数默认值
- 优化`mongo`模块兼容`Spring Boot`
- 优化`==`、`!=` 逻辑，弱化类型
- 移除界面中顶部删除按钮
- [PR !1  浏览文件修复Java枚举代码提示获取不到成员的问题](https://gitee.com/ssssssss-team/magic-editor/pulls/1)

## [v0.6.1] 2021.02.01
- 新增编辑器配置，可在后端配置样式、皮肤、按钮显示控制等
- 修复`Swagger`文档接口路径未携带前缀的`BUG`
- 修复扩展运算符在多次运行时会导致参数错乱的问题
- 修复`RequestBody`不支持`List`的问题
- 修复断点调试时不走后置拦截器的问题
- [PR !7 优化遍历过程方法，修复分组路径修改不生效的问题](https://gitee.com/ssssssss-team/magic-api/pulls/7)
- [PR !8 修复接口里使用magic.execute调用其它接口导致上下文丢失的问题](https://gitee.com/ssssssss-team/magic-api/pulls/8)
- 优化调用`java`方法的优先级，以更合理的方式去调用
- 优化`mongodb`模块逻辑，增强兼容性
- 优化编辑器检测异常结果逻辑，不在弹框提醒

## [v0.6.0] 2021.01.04
- **新增在线自定义函数**
- 增强`import`语句，可引入其他接口或自定义的函数
- 修复函数`round`、`ceil`、`floor`、`precent`未注册的问题
- 修复`Vue`组件可能出现不刷新的问题
- 优化`ifnull` 函数，改为`ifnull(var,defaultValue)` 的形式
- 优化`magic.call/execute`方法，不在要求携带`prefix`
- 优化正则表达式语法高亮

## [v0.5.5] 2020.12.28
- **新增`Linq`式查询以及相关函数**
- 新增聚合函数`group_concat`、`count`、`sum`、`max`、`min`、`avg`
- 新增函数`round`、`ceil`、`floor`、`precent`、`date_format`、`ifnull`、`now`
- 新增自定义函数
- 优化`运行日志`输出
- 优化获取接口详情，兼容一些意外情况

## [v0.5.4] 2020.12.21
- 新增代码悬浮提示
- 修复编辑器的代码提示不完整的问题
- 修复`swagger`在带有`context-path`时`Execute`会`404`的问题
- 修复`assert`失败时，未被转换为`json`结果的`BUG`
- 修复接口信息中点击新增/删除`Header`或参数时，组件不刷新的问题
- 修复运行结果的组件可能不刷新的问题
- 修复复制接口时会产生覆盖的问题
- 修复脚本部分作用域未隔离的`BUG`
- 优化`Map`的`sort`扩展方法，增加`value`参数以支持根据`map`的`value`排序
- 优化代码提示
- 优化部分组件样式
- 示例网站新增一些`Demo`

## [v0.5.3] 2020.12.17
- 修复无法修改分组路径的`BUG`
- 修复sql中无法引入局部变量的`BUG` [#I29LQG](https://gitee.com/ssssssss-team/magic-api/issues/I29LQG)
- 修复未携带参数的`BUG`
- 修复引入组件浏览器会报错的问题
- 修复底部组件渲染不正确的问题

## [v0.5.2] 2020.12.16
- 修复注入不了`db`模块的`BUG`
- 修复`db.page`方法会报错的`BUG`
- 修复前端忽略版本更新时会再次提示的`BUG`
- 修复保存接口时可能会报空指针的`BUG`
- 修复`tab`页可能会重复的问题
- 修复编辑器未携带`RequestBody`的问题
- 优化`MagicDynamicDataSource`类的包路径
- 优化历史记录，当无记录时提示
- 优化编辑器样式，增强兼容性

## [v0.5.0] 2020.12.15
### 界面改动
- 界面改用`VUE`重写
- 新增支持多`tab`页、自动保存
- 新增对顶部`header`的自定义配置`API`
- 新增自定义皮肤配置的`API`
- 新增请求钩子设置，主要用于支持自身应用对`UI`操作的鉴权
- 新增支持接口搜素
- 新增全局配置（用于模拟测试，全局header、全局参数等）
- 新增语法错误提示
- 接口列表改为树形结构

### 功能改动
- 新增支持数据库自定义方言
- 新增自定义配置列名转换、以及默认列名转换配置项
- 新增数据库列名转换API(`camel`、`pascal`、`upper`、`lower`、`normal`)
- 新增单表操作`API`(`insert`、`update`)
- 新增`SQL`拦截器
- 新增拦截器`RequestInterceptor`参数`request`、`response`
- 新增内置跨域处理
- 废弃`DynamicDataSource` 改用`MagicDynamicDataSource`
- 优化代码，内部包结构调整

### 脚本改动
- 新增`?.`语法，`obj?.method` 当`obj`为空时直接返回`null`
- 新增`...`自动展开语法
- 新增支持`[].xxx()`的语法
- 新增支持`(expr).xxx()`的语法
- 新增正则类型 `//gimuy`
- 新增`Pattern`扩展`test`用于校验文本是否符合正则
- 新增`exit` 语句，`exit 400,'参数填写有误';` 直接退出执行脚本，返回结果

### `BUG`修复
- 修复未对脚本解除包装导致读取脚本错误的`BUG`
- 修复分页缓存计算`Key`的`BUG`
- 修复变量作用域污染的问题
- 修复在请求时`ContentType`为`application/json`等类型，`RequestBody` 为空时会报错的问题
- 修复`+=`、`-=`、`/=`、`%=` 对`int`值操作时未赋值的`BUG`

### 其它
- 新增达梦数据库方言及脚本 [!5 添加达梦数据库方言及sql文件](https://gitee.com/ssssssss-team/magic-api/pulls/5)
- 更新`SQL`脚本，去除自带例子
- 优化文档

## [v0.4.8] 2020.11.26
- 修复`monaco-editor`引起的浏览器崩溃问题
- 修复设置线程池大小无效的问题
- 增强`!`一元运算符，支持非布尔值运算
- 修复函数命名`atPercent`变更为`asPercent`

## [v0.4.7] 2020.11.23
- 新增`Map`类型到`JavaBean`的自动隐式转换 [#I251SS](https://gitee.com/ssssssss-team/magic-api/issues/I251SS)
- 新增`session.key = value`的写法，用于向`session`中写值
- 新增集合函数`every`、`some`、`reduce`、`skip`、`limit`、`findNotNull`
- 新增`Map`函数`sort`、`each`、`asString`、`merge`、`asList`
- 新增`Number`函数 `round`、`toFixed`、`floor`、`ceil`、`atPercent`
- 新增`Date`函数 `format`
- 修复调用`lambda`时变量获取不正确的`BUG` [#I2632N](https://gitee.com/ssssssss-team/magic-api/issues/I2632N)
- 优化`Map`类型定义、保持书写顺序
- 优化编辑器，可以折叠`import`、以及支持在单行太长时自动换行。
- 优化编辑器高亮，支持`SQL`高亮
- 优化`Loading`界面
- 优化部分逻辑，支持`JDK9+`
- 优化内部代码，`DatabaseQuery` 重命名为 `SQLExecutor`

## [v0.4.6] 2020.11.16
- 新增函数`asBean` 用于将`map`或`list`转为Java对象 [#I251SS](https://gitee.com/ssssssss-team/magic-api/issues/I251SS)
- 新增语法`++`、`--`、`+=`、`-=`、`*=`、`/=`、`%=`、`连=`
- 新增`env`模块，用于读取配置
- 新增`.class`属性访问
- 修复`async`嵌套会产生阻塞的问题
- 修复`return`语句在不返回任何值的空指针`BUG`
- 修复在`async`中变量读取不正确的问题
- 修复在切换变量作用域时二次赋值不正确的`BUG` [#I252VY](https://gitee.com/ssssssss-team/magic-api/issues/I252VY)
- 修复在`magic-api.auto-import-package`为空时 `JS`报错的问题
- 优化生成`SQL`时产生的空白
- 优化`&&`、`||` 运算，支持`data && data.xx`、`var a = b || 1` 的写法
- 优化`magic-script`脚本变量读写性能
- 优化代码提示、参数提示
- 优化脚本异常提示

## [v0.4.5] 2020.11.09
- 新增集合函数`group`、`join`
- 新增聚合函数`max`、`min`、`avg`、`sum`
- 新增参数提示、动态数据源提示
- 新增`magic-api.thread-pool-executor-size`参数配置，用来设置`async`语句线程池大小
- 修复恢复断点时丢失`header`的问题
- 修复进入断点时，获取变量信息不正确的`BUG` 
- 优化`magic-api.auto-import-package` 配置，内置自动导入`java.lang.*`、`java.util.*`
- 优化`async`语句执行机制，改为在线程池中执行
- 优化代码提示，增加中文提示
- 优化`查看历史记录详情` 的SQL兼容性


## [v0.4.4] 2020.11.04
- 新增`while`循环语句
- 修复异常结果未被正常处理的`BUG`
- 修复UI断点与折叠点击区域重叠的问题
- 优化在请求接口打印异常日志时附带URL
- 优化脚本错误信息增加行列号


## [v0.4.3] 2020.11.03
- 修复进入断点时无法操作的`BUG`
- 修复新建接口时默认请求参数缺失`}`的问题
- 优化`if`语句和`三元运算符` 支持`if(xxx)` 的写法

## [v0.4.2] 2020.11.02
- 新增脚本异步调用功能
- 新增集合函数`sort`、`reserve`、`join`、`shuffle`
- 新增代码折叠功能
- 优化模拟测试，改为实际请求
- 优化对`BigDecimal`类型的代码提示
- 优化对枚举类型的代码提示
- 优化对`Spring Security`框架的支持,自动适配解决`ThreadLocal`问题
- 去除`Cookie`、`Session`模拟

## [v0.4.1] 2020.10.26
- 新增支持ClickHouse数据库
- 修复定义空字符串`""`时代码高亮不正确的`BUG`
- 修复冲突问题，将`DynamicDataSource`更名为`MagicDynamicDataSource`
- 修复未正确调用带有可变参数的重载方法的`BUG`
- 修复向页面传递配置信息时传递用户名密码的安全问题
- 优化模拟测试，在测试时将header参数放在http header中 [#I1Z6RE](https://gitee.com/ssssssss-team/magic-api/issues/I1Z6RE)
- 优化登录，禁止使用ESC键或回车键关闭登录框


## [v0.4.0] 2020.09.14
- 新增用户名、密码配置（用于页面登录，增加安全性）[#I1UTXT](https://gitee.com/ssssssss-team/magic-api/issues/I1UTXT)
- 新增`response.end`方法 [#1S5UJ](https://gitee.com/ssssssss-team/magic-api/issues/I1S5UJ)
- 新增自动导包配置(默认导入`java.util.*、java.lang.*`)
- 新增允许覆盖应用接口配置
- 优化数据库兼容性 [#I1TCFU](https://gitee.com/ssssssss-team/magic-api/issues/I1TCFU)
- 优化代码提示

## [v0.3.4] 2020.08.09
- 新增支持将请求参数存入一个变量中
- 新增支持接口自动刷新
- 优化`Map`定义，可省略`value`
- 优化`import`提示
- 修复在测试时获取不到`HttpServletRequest`的问题

## [v0.3.3] 2020.08.02
- 新增插入并返回主键
- 新增15种类型判断方法
- 新增动态增删改查数据源（用于应用运行时动态修改数据源）
- response模块新增addHeader、setHeader、addCookie、addCookies等方法
- 修复分组不能删除的`BUG`
- 修复在保存时，注册接口与应用本身的接口冲突的问题
- 修复第一次调用父类方法时，会报找不到方法的`BUG`
- 优化UI编辑器保留当前编辑信息，当意外关闭时可恢复。
- 优化DE`BUG`功能，支持单步调试、运行时修改断点
- 优化代码提示
- 优化分组名、分组前缀添加校验
- 完善文档

## [v0.3.2] 2020.07.26
- 新增支持配置默认导入模块
- 新增支持`BigDecimal`类型
- 修复分组前缀在以非"/"开头时的错误
- 修复DE`BUG`时二进制结果输出不正确的问题
- 修复重启后台后前端自动重试的`BUG`
- 优化脚本报错时，自动跳转到错误行

## [v0.3.1] 2020.07.20
### 新增
- Oracle建表语句
### `BUG`修复
- 启动报`ClassNotFoundException : springfox.documentation.swagger.web.SwaggerResourcesProvider`的`BUG`
- Swagger配置类循环引用的`BUG`
- UI界面中编辑器里无法使用回车键的`BUG`


## [v0.3.0] 2020.07.19

### 新增
- 历史记录查看、比对、还原
- 支持Swagger2
- 允许日志输出到页面上
- 接口分组前缀
- Response模块(可输出图片、下载文件、自定义JSON、构建分页)
### `BUG`修复
- RequestBody参数测试时无效的问题
### 优化
- 滚动条、图标兼容Firefox
- 优化UI体验
- 取消兼容null.方法、null.属性、null[key]、null[index]

## [v0.2.1] 2020.07.12
- **更换UI**
- 新增事务相关函数
- 新增接口使用数据源配置
- 新增接口数据源接口（可自定义接口存储，可加密脚本信息）
- 新增页面按钮权限接口
- 新增each函数
- 优化代码提示
- 代码编辑器汉化
- 修复脚本中不能给map类型赋值的问题
- 修复finally块return null的`BUG`
- 修复return new XXX();语句的`BUG`
- 修复删除失败时，接口会被取消注册的`BUG`

## [v0.2.0] 2020.07.05
- **抛弃XML方式，改用脚本，通过Web页面编写脚本**
- 新增脚本De`BUG`能力
- 新增代码提示
- 新增错误提示
- 新增Redis、MongoDB的支持
- 新增API前缀以及WEB页面配置
- 新增日志、断言模块
- 新增自定义结果转换以及自定义类型扩展
- 重构自定义拦截器
- 重构SQL执行器
- 修复默认SQL缓存线程安全问题

## [v0.1.1] 2020.05.17
- 改名为magic-api,原名ssssssss
- 新增支持缓存(默认实现LRU+TTL),可自定义
- 修复多数据源时无法使用默认数据源的`BUG`
- 修复分页查询时未释放数据库连接的`BUG`
- 修复打成Jar后无法读取XML的问题
- 优化缓存获取数据库方言
- 取消验证dtd
- 完善文档

## [v0.1.0] 2020.05.11
- 修复post请求时报415错误的`BUG`
- 新增多数据源支持
- 新增插入返回主键
- 新增自定义主键生成策略
- 新增请求拦截器
- 新增是否抛出异常配置
- 优化dtd，改为xsd验证
- 完善文档


## [v0.0.1] 2020.05.06
- v0.0.1 正式发布
