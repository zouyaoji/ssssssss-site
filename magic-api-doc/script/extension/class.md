---
subSidebar: false
---
## Class

`java.lang.Class`的扩展方法

## newInstance
- 入参：`values`:`Object`  可变参数，构造函数的参数
- 返回值：`Date`
- 函数说明：将`Class`实例化
```js
import 'java.text.SimpleDateFormat' as SimpleDateFormat;
return SimpleDateFormat.newInstance('yyyy-MM-dd HH:mm:ss');
//其实可以简写成 new SimpleDateFormat('yyyy-MM-dd HH:mm:ss'); //这是一个语法糖 ^_^
```

## 获取类名称

支持以下方法

* getName
* getSimpleName
* getCanonicalName  

```js
import 'java.text.SimpleDateFormat' as SimpleDateFormat;
println(SimpleDateFormat.getName());
println(SimpleDateFormat.getSimpleName());
println(SimpleDateFormat.getCanonicalName());
return null;
```

可以在控制台看到如下输出

```java
java.text.SimpleDateFormat
SimpleDateFormat
java.text.SimpleDateFormat
```

具体以上方法有何不同可参考`Class.java`文件。

