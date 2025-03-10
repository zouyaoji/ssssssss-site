---
subSidebar: false
---
## 常见问题

[[toc]]

## 如何配置JSON日期的格式
使用`Jackson`的配置如下(`Spring Boot`默认使用`Jackson`)：
```yml
spring:
  jackson:
    time-zone: GMT+8
    date-format: yyyy-MM-dd HH:mm:ss
```
对于`LocalDateTime`配置
```java
@Bean 
public Jackson2ObjectMapperBuilderCustomizer jackson2ObjectMapperBuilderCustomizer() {
    LocalDateTimeSerializer localDateTimeSerializer = new LocalDateTimeSerializer(DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss"));
    return builder -> builder.serializerByType(LocalDateTime.class, localDateTimeSerializer); 
}
```
其它的自行参考`json`框架配置

## 出现找不到db模块的错误
目前已知两种情况：
- 未配置数据源
- 未引用`spring-boot-starter-jdbc`

## 如何获取RequestBody中的参数
脚本中使用`body.xxx`获取`RequestBody`中的参数
`SQL`中使用`#{body.xxx}`或`${body.xxx}`获取`RequestBody`中的参数

## 如何获取Header中的参数
脚本中使用`header.xxx`获取`Header`中的参数
`SQL`中使用`#{header.xxx}`或`${header.xxx}`获取`Header`中的参数

## 如何获取Cookie中的参数
脚本使用`cookie.xxx`获取`Cookie`中的参数
`SQL`中使用`#{cookie.xxx}`或`${cookie.xxx}`获取`Cookie`中的参数

## 如何获取Session中的参数
脚本中使用`session.xxx`获取`Session`中的参数
`SQL`中使用`#{session.xxx}`或`{session.xxx}`获取`Session`中的参数

## 如何获取PathVariable中的参数
脚本中使用`PathVariableName`或`path.xxxx`获取`PathVariable`中的参数
`SQL`中使用`#{PathVariableName}`或`#{path.xxx}`获取`PathVariable`中的参数

## 如何获取上传的文件

利用Request模块
```js
import request;
request.getFile('name');
```

## 如何获取提交的数组参数

利用Request模块
```js
import request;
return request.getValues('name');
```

## 如何给接口添加权限

一般情况采用`拦截器`实现
在`接口选项`中配置`permisson`或`role`或自定义选项
随后在拦截器实现：
```java
@Component
@Order(1)   //拦截器顺序
public class PermissionInterceptor implements RequestInterceptor {

    @Override
    public Object preHandle(ApiInfo info, MagicScriptContext context, HttpServletRequest request, HttpServletResponse response) {
        // 获取配置的接口选项属性
        String permissionCode = info.getOptionValue(Options.PERMISSION);
        // 执行自己的代码逻辑进行判断是否有权限
        // ....
        if(无权限){
        	// 需要注意的是，拦截器返回的不会走ResultProvider。
            return new JsonBean<>(403,"无权访问");
        }
        // 放行
        return null;
    }
}
```

## 如何给UI添加权限

请参考[自定义UI鉴权](../authorization/operation)


## ${}和#{}的区别
主要区别在于`${}`用于拼接SQL(会产生SQL注入问题)，`#{}`会替换成占位符（不会产生SQL注入问题），这里的区别与`Mybatis`一致

## 如何循环拼接参数
两种办法：
- `in (#{ids})`的语法会自动对集合参数展开
```js
var ids = [1,2,3,4,5,6];
//会自动变成select * from sys_user where id in(?,?,?,?,?,?)
return db.select('select * from sys_user where id in(#{ids})'); 
```
- 循环拼接SQL
```js
var list = [1,2,3,4,5];
var sql = "select * from sys_user where ";
for(index,item in list){
    sql = sql + 'id = #{list['+index+']}';
    if(index + 1 < list.size()){
        sql = sql + ' or ';
    }   
}
return db.select(sql);
```

## 多数据源如何配置
编写java代码如下：
```java
@Bean
public MagicDynamicDataSource magicDynamicDataSource(){
    MagicDynamicDataSource dynamicDataSource = new MagicDynamicDataSource();
    // 设置默认数据源（默认数据源一定要设置）
    dynamicDataSource.setDefault(ds1);
    dynamicDataSource.add("slave",ds2);
    return dynamicDataSource;
}
```
脚本中使用：
```js
db.select('select * from sys_user');  //使用默认数据源
db.slave.select('select * from sys_user');  //使用slave数据源
```

## SQL执行报错java.sql.SQLFeatureNotSupportedException: null
原因：druid版本过低，升级至最新版后即可

## 如何自定义返回结果
- 通过配置文件进行配置，具体参考[spring-boot配置](../config)
- 通过`自定义JSON结果`，具体定义方法查看[自定义JSON结果](../tutorials/json.html)
- 通过`自定义拦截器`拦截返回自己想要的格式，具体定义方法查看[自定义拦截器](./custom/interceptor.html)
- 通过`spring`的拦截器返回想要的格式，如`ResponseBodyAdvice`，`HandlerMethodReturnValueHandler`（这种方式目前会影响到UI,故不推荐使用）


## 页面加载缓慢

由于`monaco-editor`编辑器比较大，建议开启压缩静态资源

```properties
server.compression.enabled=true #启用压缩
server.compression.min-response-size=256 #大于256kb时压缩
```

## 脚本内容被转义

出现这种情况，请检查自身项目是否有`XSS`一类的过滤器，需要把`UI`界面对应的后台接口排除掉即可

## 执行测试无响应

目前已知有两种情况

- 使用了Spring Boot 2.3.5版本，升级至2.3.6解决
- 使用了`nginx`代理，加一条配置`proxy_buffering off;`解决

## 访问UI404

- 请检查访问路径是否正确
- 请检查`magic-editor`包是否被引入
- 如果是拉源码运行，则需要编译一下前端。
- 如果以上确定没问题，请检查应用中是否有关于`mvc`的配置，如果有请检查是否是`extends WebMvcConfigurationSupport`的形式，是的话，改成`implements WebMvcConfigurer`的形式。
- 如以上问题均不存在，请提[ISSUE](https://gitee.com/ssssssss-team/magic-api/issues) 或加群[739235910](https://qm.qq.com/cgi-bin/qm/qr?k=Q6dLmVS8cHwoaaP18A3tteK_o0244e6B&jump_from=webapi)反馈

## 无法DEBUG或无法查看日志

- 由于`DEBUG`和日志是依赖于`WebSocket`实现的，所以需要`WebSocket`支持
- 请检查`Web`容器是否支持`WebSocket`，如果不支持，需要引入对应依赖或更换支持`WebSocket`的`Web`容器
- 请检查是否使用了`nginx`之类的代理，如果使用了，需要对配置其支持`WebSocket`，样例如下：
```nginx
location /magic/web/console {
    proxy_pass http://localhost:9999;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
    proxy_read_timeout 900s;
}
```

## 保存图片(Blob)数据到数据库

​	假设将图片的二进制数据传输到body.img中, sql可以这么写

```js
var sql = """
	insert into img_table(
    	img 
    )
	values(
    	#{img::sql('blob')}
    )
""";
```

​	`::sql`用法参考 [类型转换](../tutorials/grammar.html#类型转换-2)

