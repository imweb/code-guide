#Lego 组件运营规范
@(系统建设)

+   **组件规范**

    在lego系统的组件需要遵循以下规范
    +   [Lego 组件规范](https://github.com/imweb/code-guide/blob/master/lego/SPECIFICATION.md)
    +   [Lego 平台规范](https://github.com/imweb/code-guide/blob/master/lego/PLATFORM-SPECIFICATION.md)
    +   [Lego 运营规范](https://github.com/imweb/code-guide/blob/master/lego/PLATFORM-SPECIFICATION.md)

----------------

+   **组件构建体系**
    +   团队后续构建工具统一迁徙至FIS3，lego会集成到fis3中，目前H5已接入Lego。
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
+   **组件运营计划(`征召中...`)**
    +   `优化团队`
        
        负责Lego系统功能优化，定期收集大家的反馈，优化系统体验。
    +   `认证团队`
        +   质量
            
            负责检测组件的质量，保证组件完善的api文档、demo、兼容性说明、author必要信息
        +   认证
            
            组件的认证，前期负责讲平台现有的组件认证搭建起来，推动组件开发这完善组件的必要信息，收集大家的反馈。
    +   `推广团队`
    
        Lego推广，相关运营工作。lego站点、github上文档和指引的完善，各个第三方站点推广。