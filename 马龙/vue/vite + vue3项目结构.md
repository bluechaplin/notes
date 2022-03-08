# vite + vue3项目结构

- ## public

  不需要进行编译的静态资源文件

- ## assets

  需要进行编译的静态资源文件

- ## components

  组件，用于将一些公用的组件进行抽离

- ## app.vue

  全局组件，单页应用入口，里面写的样式会影响全局，需要注意

- ## main.ts

  入口文件

- ## index.html

  vite的入口页面，一般由此引入main.ts

- ## package.json

  配置项（脚本命令等），依赖设置

- ## tsconfig.json

  ts配置文件

- ## vite.config.ts

  vite配置文件

  