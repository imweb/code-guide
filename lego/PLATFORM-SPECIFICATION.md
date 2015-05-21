#lego组件平台规范
@(基础能力)

-----------------------

[lego](http://lego.imweb.io)基于[spm](http://spmjs.io/)基础之上，完善组件分类体系，组件认证体系，组件反馈体系的完整的组件使用生态系统。协助组件使用者在组件选择、信任组件、组件使用中更好的参与到组件生态系统中。

+	**GitHub开源**
	+	[lego](https://github.com/imweb/lego)与[lego.imweb.io](https://github.com/webryan/lego.imweb.io)（`需要权限才能访问`）
	+	如需要，访问[spm](https://github.com/spmjs/spm)与[spm.io](https://github.com/spmjs/spmjs.io)
+	组件平台

	组件平台分类[客户端](https://github.com/imweb/lego)以及[服务平台](http://lego.imweb.io)

+	客户端安装&使用（`文档还在完善中`）

	**npm install -g lego** `安装lego客户端`

	**lego login** `登录lego系统，lego帐号和github帐号关联`

	**lego info** `lego信息查看`

	**lego init**	`初始化组件目录，组件开发初始化`

	**lego doc** `文档生成`，如：[jquery](http://lego.imweb.io/docs/jquery/latest/)

	**lego doc publish** `组件开发者将文档发布至平台`

	**lego publish/unpublish**	`组件发布`

	**lego config** `管理lego配置`

	**lego install** `安装组件`

	组件使用的时候安装一个组件，使用类似于npm，如果没有制定安装具体的组件，可以通过pakage.json中的lego字段申明依赖。
	
	lego install jquery 或者 lego install jquery@2.1.3

	组件install之后，会安装到本地的lego_modules中，所有依赖组件都会平级放到该目录下。
	
	**package.json**
	
	```html
{
  "name": "zepto",
  "version": "1.1.4",
  "description": "zepto",
  "keywords": [],
  "homepage": "",
  "author": "herbertliu <herbertliuhb@gmail.com>",
  "repository": {
    "type": "git",
    "url": ""
  },
  "bugs": {
    "url": ""
  },
  "licenses": "MIT",
  "lego": {
    "main": "index.js",
    "dependencies": {
    },
    "devDependencies": {
      "expect.js": "0.3.1"
    }
  }
}			
```

	**lego test** `单元测试，完善中`

	**lego search**`组件查找，完善中`

	**lego update**`组件更新，完善中`

	**lego server update** `第三方组件更新检查(jquery)，通过配置组件来源，通过命令检查更新，进行同步，完善中`

	在组件的package中lego字段新增`source`字段，在组件开发中如果是第三方组件需要指定该字段，通过命令进行更新检查并做一些初始化组件的工作。


+	**组件分类**

	组件分类，帮助组件使用者更快、直接的招到自己所需要的组件，通过组件本身属性（兼容性、平台性、功能性）来进行分类和标记。同时，可以通过查找来直接定位组件。详细的分类如下（*`后续维护修改`*）：

	+	基础组件
		诸如[jquery](http://lego.imweb.io/package/jquery)等基础框架组件
	+	工具组件
		依托于基础组件的插件、工具等组件。诸如local、query、cookie
	+	通用组件
		所有通用业务都需要，但与具体业务无关的t组件，包含逻辑以UI，诸如：badjs、report.js、editor
		+	逻辑组件
			纯逻辑组件，详细分类还在完善中
			+	日志
			+	校验
			+	...
		+	UI组件	
			涉及UI交互视觉的组件，详细分类还在完善中
			+	导航
			+	弹出框
			+	面板
			+	日历
			+	...
	+	业务组件
		+	在线教育
			+	逻辑组件
			+	UI组件
		+	吃喝玩乐
			+	逻辑组件
			+	UI组件
		+	...
+	组件认证
	+	认证提交

	组件开发者通过平台，[提交](http://lego.imweb.io/authen/apply/expect.js)组件认证。

	+	组件审核
	
	审核通过的组件可以通过平台查看认证信息，认证流程参见[组件规范](https://github.com/webryan/lego.imweb.io/blob/master/docs/STANDARD.md)。	
