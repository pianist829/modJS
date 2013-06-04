﻿#modJS


## 简介

modJS 是 [FIS](https://github.com/fouber/fis)(前端集成解决方案)的前端框架，主要用于模块管理和加载，适用于线上运行时，具有代码精简、使用简单、运行高性能的特点。

## 下载

[Latest release](https://raw.github.com/zjcqoo/mod/master/mod.js)

## 使用

**模块的定义**

* modJS完全遵循AMD规范。使用define来定义一个模块：

  **define** (id, factory)

  在平常开发中，我们只需写factory中的代码即可，无需手动定义模块。发布工具会自动将模块代码嵌入factory的闭包里。

 factory提供了3个参数：**require**, **exports**, **module**，用于模块的引用和导出。

* modJS的发布工具会保证你的程序在使用之前，所有依赖的模块都已加载。因此当我们需要一个模块时，只需提供一个模块名即可获取：

 **require** (id)

 和NodeJS里获取模块的方式一样，非常简单。

 因为所需的模块都已预先加载，因此require可以立即返回该模块。

* 考虑到有些模块无需在启动时载入，因此modJS提供了可以在运行时异步加载模块的接口：

 **require.async** (names, callback)

 names可以是一个模块名，或者是数组形式的模块名列表。

 当所有都加载都完成时，callback被调用，names对应的模块实例将依次传入。

  使用require.async获取的模块不会被发布工具安排在预加载中，因此在完成回调之前require将会抛出模块未定义错误。






## 相关项目

前端集成解决方案：[FIS](https://github.com/fouber/fis)

自动添加define插件：[fis-modular-reqlang](https://github.com/fouber/fis-modular-reqlang)
