#[Lego](http://lego.imweb.io) 组件运营规范
@(系统建设)

+   **组件规范**

    在lego系统的组件需要遵循以下规范
    +   [Lego 组件规范](https://github.com/imweb/code-guide/blob/master/lego/SPECIFICATION.md)
    +   [Lego 平台规范](https://github.com/imweb/code-guide/blob/master/lego/PLATFORM-SPECIFICATION.md)
    +   [Lego 运营规范](https://github.com/imweb/code-guide/blob/master/lego/OPERATION.md)

----------------

+   **组件构建体系**

    团队后续构建工具统一迁徙至FIS3，lego会集成到fis3中，目前H5已接入Lego，基于fis2的插件[plugin](http://lego.imweb.io/package/fis-postprocessor-lego-require)。

    +   **构建规则**
    
        首先来看一下项目目录

        ——  edu-proj

            ---- dist 发布目录

            ---- dev 开发目录

            ---- src 源码目录

                ————   lego_modules lego依赖，基于同目录下的package.json维护

                    ———— zepto lego组件，规范为组件规范

                ————   modules 自身模块目录，下含多个模块，项目模块和全局模块可平行转移

                ————  pages 静态文件目录

                ————  images 图片目录

                ————  package.json 维护lego组件

        +   **构建规范**
            +   **优先级**
                
                优先级遵循项目modules > lego_modules，当使用着通过require('zepto')或者require.async('zepto')时，构建优先查找项目modules是否包含该模块，如包含，则使用该模块。反之，则查找lego_modules下是否包含该模块，并深度分析模块下的package.json中依赖，然后打包。
            +   **相对目录**
                
                当使用相对目录的时：require(./zepto)，只查找项目modules，并分析依赖构建打包。因此，为方便代码可读性和维护性，使用项目modules，优先采取相对目录使用。


+   **组件同步机制**

    内网源和外网源定期同步，开发网同学请优先使用内网源 ` lego config set registry http://lego.oa.com`
+   **组件提交规范**
    +   **文档 & 测试用例**
        +   需要给出完整的API文档、DEMO、测试用例，才能通过组件认证，被认证的组件，才会被大家优先使用。
    +   **组件文档规范**
    
        分为[内网源](http://lego.oa.com)，[外网源](http://lego.imweb.io)。
        +   内网源
            
            内网源，用户是基于github用户，在内网源的情况下，没有用户的概念，因此在内网源提交的组件需要在README.md中明确组件的author。
        +   外网源
            
            外网源，需要先login才能进行提交。详细使用见lego login命令
    +   **组件维护**
        +   认证
            
            组件开发者可以到平台申请组件认证，提交组件认证信息，有认证团队对组件进行认证。
        +   反馈
            
            组件维护者，需要关注自己提交的组件的反馈，及时关注组件issue，保证组件的活跃性(目前还没有打通通知机制)
+   **Lego组件团队(`征召中...`)**
    +   `优化团队`
        
        负责Lego系统功能优化，定期收集大家的反馈，优化系统体验。
    +   `认证团队`
        +   质量
            
            负责检测组件的质量，保证组件完善的api文档、demo、兼容性说明、author必要信息
        +   认证
            
            组件的认证，前期负责将平台现有的组件认证搭建起来，推动组件开发这完善组件的必要信息，收集大家的反馈。
    +   `推广团队`
    
        Lego推广，相关运营工作。lego站点、github上文档和指引的完善，各个第三方站点推广。