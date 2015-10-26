#PC端技术数据上报规范
+   PC端来源区分
    +   根据场景需要，区分QQ 和 其他非QQ数据，齐齐，QT
        +   QQ
        +   齐齐(IE内核，需要客户端在user-agent中添加齐齐特有字段)
        +   QT(WebKit内核，需要客户端在user-agent中添加QT特有字段)
        + 其他场景自行选择浏览器的user-agent
+   页面测速(工具化)
    +   html 页面需要上报[Navigation Timing](http://www.w3.org/TR/navigation-timing/)
        +   `参见 performance.timing`(参考链接：[W3C: PerformanceTiming](http://www.w3.org/TR/2012/REC-navigation-timing-20121217/#processing-model)、[Performance API](http://javascript.ruanyifeng.com/bom/performance.html)、[Resource-Timing](http://www.w3.org/TR/resource-timing/#processing-model))
        +   使用华佗测速系统自动上报点
    +   页面测速需要区分离线包&非离线包（卓颖）
        +   pack 离线包
        +   unpack 非离线包
    +   CGI测速上报mm系统（xxx）
        +   url
    +   页面打点可以自行处理，需要包含以下测速点（自己手写）
        +   页面底部 dom-end
        +   js加载完成 js-end
        +   js执行完成 js-called-end
        +   数据加载完成 data-load-end
        +   数据渲染完成 data-render-end
        +   *首屏速度 first-screen*
            +   `首屏依赖数据的话，首屏速度参照data-render-end，反之，参照js-called-end`
    +   异步加载的文件测速（js/css/第三方资源）（xxx）
        +   速度上报测速系统
        +   带上离线包情况
        +   js-load-xxx/css-load-xxx/img-load-xxx/file-load-xxx
    + 客户端唤起web control测速
        +   用户点击客户端入口，到web control出现的时间(需推动客户端支持)
+   失败率
    +   文件加载失败率（css、js、图片[必要场景]）    （xxx）
    +   首屏关键图片监控(失败率/测速/区分首次与非首次)`[可选]`
+   日志信息（xxx）
    +   CGI拉取失败错误
        +   信息包含错误码、url地址
        +   格式：url(如果没有专门的错误码上报字段，错误码可添加在url中)
    +   必要的关键路径上报`[可选]`
    +   tryjs(即badjs 2.0)堆栈上报(如果有)
    +   local 异常上报
+   版本覆盖率（卓颖）
    +   QQ离线包版本更新率
    +   QQ离线包版本覆盖率

![PC上报规范](../imgs/PC上报规范.png)