# vue

## vue项目的环境变量

### 背景

项目开发一般分为开发环境，测试环境，正式环境。

### 模式

*development*     模式用于 vue-cli-service serve

*production*        模式用于 vue-cli-service build 和 vue-cli-service test:e2e

*test*                     模式用于 vue-cli-service test:unit

npm run serve时，对应的环境就是开发环境；

npm run build时，对应的环境就是生产环境。

### 给.env文件添加内容

#### 基本格式

NODE_ENV=环境名称
VUE_APP_URL=对应的环境地址

#### 例子

```
.env.production文件
ENV = 'production'
VUE_APP_BASE_API = '/prod-api'
```

#### 在package.json中添加不同环境对应的执行语句

可以通过传递--mode选项参数为命令行覆写默认的模式。例如想在构建命令中使用开发环境变量，就在package.json中加入

```
"dev-build": "vue-cli-service build --mode development",
```

![735803-20191121140048590-279787724](C:\Users\Administrator\Desktop\vueLog\735803-20191121140048590-279787724.png)

## 使用

如现在需要local环境，就执行 npm run local-serve

然后通过 process.env.NODE_ENV 获取环境名；通过 process.env.VUE_APP_URL 获取环境对应的url。

比如我们在axios请求中，就可以把它的baseURL设置为  process.env.VUE_APP_URL ，如下图所示：

![23](C:\Users\Administrator\Desktop\vueLog\23.png)

后面的"/web"是根据我自己接口来的，你别也写个"/web"。

如果你不确定你自己现在是在哪个环境变量下，可以   console.log("当前环境变量："+process.env.NODE_ENV) 和   console.log("当前环境路径："+process.env.VUE_APP_URL)  看下。

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 配置路径别名

1.先在项目根目录下创建vue.config.js文件

2.然后在文件里输入下面代码

```
const path = require('path');

function resolve(dir) {
  return path.join(__dirname, dir);
}
module.exports = {
  lintOnSave: true,
  chainWebpack: (config) => {
    config.resolve.alias
      .set('@', resolve('src'))
      .set('@assets',resolve('src/assets'))
      // 这里只写了两个个，你可以自己再加，按这种格式.set('', resolve(''))
  }
}
```



