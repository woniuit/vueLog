# Nuxt

## css

**配置全局的css**

在nuxt.config.js中配置

```
  css: [
    'element-ui/lib/theme-chalk/index.css',
    // 项目里要用的 CSS 文件
    '@/assets/css/init.css'
  ],
```

使用less

首先安装

```
npm install less less-loader --save-dev
```

设置全局的变量

```
less less-loader sass-resources-loader
```

在nuxt.config.js中配置

```
  styleResources: {
    less: [
      './assets/css/common.less'
    ]
  },
  
    modules: [
    
    '@nuxtjs/style-resources'
  ],
```

## 加载外部资源

例如加载阿里字体图标

在nuxt.config.js中配置

```
head: {
    script: [
      { src: 'http://at.alicdn.com/t/font_1776033_hpzkf49oa07.js' }
    ]
  }


  <svg class="icon" aria-hidden="true">
       <use xlink:href="#iconzhanghaoshensu" />
   </svg>
```

