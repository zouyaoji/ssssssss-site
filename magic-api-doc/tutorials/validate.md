# 参数校验


## 自动验证
![验证](../.vuepress/public/images/validate.png "参数验证")

如图所示，可验证必填，表达式验证和正则验证。

## 手动验证

对于表达式和正则无法实现的可以通过脚本来实现。
```groovy
var count = db.selectInt("""
    select count(*) from sys_user where phone = #{phone}
""")
// count 值应该为0，如果不为0则验证不予通过。
assert count == 0 : 400, '手机号已存在';
// 上述写法可以转换为
if(count != 0){
    exit 400, '手机号已存在'
}
```