根据ng-packagr文档得知，我们需要在我们的项目中添加两个文件，ng-package.json 和 public_api.ts。



在 ng-package.json 文件中添加如下内容：

{
  "$schema": "./node_modules/ng-packagr/ng-package.schema.json",
  "lib": {
    "entryFile": "public_api.ts"
  }
}
在 public_api.ts 文件中导出 header.module.ts

内容如下：

export * from './src/app/modules/header/header.module'
在 package.json 文件中的 scripts添加 "packagr": "ng-packagr -p ng-package.json" ，告诉 ng-packagr 根据 ng-package.json 来打包我们的组件库。同时，设置 "private": false 。



运行 npm run packagr 创建组件包，创建完成后会在项目的根目录中生成 dist 文件夹，里面的内容就是我们生成的标准的 Angular 组件库的结构。

进入 dist 目录执行 npm pack打包组件库，打包完成后，会在项目的根目录生成 my-component-library-0.0.0.tgz，0.0.0来至于 package.json 文件中一部分。

我们可以在应用中使用 npm install 安装本地的开发包
