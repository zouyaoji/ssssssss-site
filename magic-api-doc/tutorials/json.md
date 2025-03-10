# 统一请求响应


## 自定义状态码

目前内置了三种状态码，分别为 执行成功(`1`)，参数验证失败(`0`)，以及系统异常(`-1`)

个别情况可能需要针对三种状态码进行修改，可使用以下配置
```yml
magic-api:
  response-code-config:
    success: 200 #执行成功的code值
    invalid: 400 #参数验证未通过的code值
    exception: 500 #执行出现异常的code值
```


## 自定义响应Json结构

默认情况下，返回结果如下：

```json
{
  "code": 1,  // 状态码
  "message": "success", // 状态说明
  "data": ...,  // 返回的数据内容
  "timestamp": 1629610503506, // 服务器时间
  "executeTime": 1  // 执行时间
}
```
可以通过配置文件来修改此格式

```yml
magic-api:
  response: |- #配置JSON格式，格式为magic-script中的表达式
    {
      code: code,
      message: message,
      data,
      timestamp,
      requestTime,
      executeTime,
    }
```

## 自定义结构配置

编写Java代码如下，在使用此配置之后，配置文件中的`magic-api.response`将失效
```java
@Component
public class CustomJsonValueProvider implements ResultProvider {
    /**
    *   定义返回结果，默认返回JsonBean
    */
	@Override
	public Object buildResult(RequestEntity requestEntity, int code, String message, Object data) {
        // 如果对分页格式有要求的话，可以对data的类型进行判断，进而返回不同的格式
		return new HashMap<String,Object>(){
			{
				put("status", code);
				put("msg", message);
				put("body", data);
			}
		};
	}

	/**
	 *   定义分页返回结果，该项会被封装在Json结果内，
	 *   此方法可以不覆盖，默认返回PageResult
	 */
	@Override
	public Object buildPageResult(RequestEntity requestEntity, Page page, long total, List<Map<String, Object>> data) {
		return new HashMap<String,Object>(){
			{
				put("total", total);
				put("list", data);
			}
		};
	}
}
```