
# 前端团队协作规范

## 前言
- 编写目的

  本文档的编写目的是为了规范前端团队的协作流程，统一代码风格和命名规范，提高代码质量和团队效率。同时，本文档也包括了Git团队协作规范，帮助团队成员更好地管理代码版本和协作开发。
  
- 文档范围

  本文档的范围是前端团队的协作流程，代码风格和命名规范，以及Git团队协作规范。本文档旨在规范团队成员的开发流程，提高代码质量和团队效率。
  

## 命名规范
- 文件命名
  - 文件名应该全部小写，单词之间用短横线（-）分隔，例如：index.html, main.css, app.js
- 变量命名
  - 变量名应该采用驼峰命名法，例如：firstName, lastName, age
- 函数命名
  - 函数名应该采用驼峰命名法，例如：getUserInfo, calculateTotal
- 类命名
  - 类名应该采用帕斯卡命名法，即首字母大写，例如：Person, Car, Animal
- 组件命名
  - 组件名应该采用帕斯卡命名法，例如：Header, Footer, Sidebar


## 代码风格
- 缩进：使用4个空格进行缩进。
- 空格：在运算符前后加上空格，例如：a + b, x = 1。
- 换行：每行不超过80个字符，超过时应该换行。
- 注释：注释应该解释代码的意图，避免描述代码的实现细节。
- 常量：常量名应该全部大写，单词之间用下划线（_）分隔，例如：MAX_LENGTH。
- 函数：函数名应该采用驼峰命名法，例如：getUserInfo, calculateTotal。函数应该具有描述性的名称，只做一件事情，尽可能短小，避免副作用。
- 类：类名应该采用帕斯卡命名法，即首字母大写，例如：Person, Car, Animal。类应该只做一件事情，尽可能短小，避免副作用。
- 组件：组件名应该采用帕斯卡命名法，例如：Header, Footer, Sidebar。


## HTML规范
- 语法规范
  - 使用HTML5语法
  - 使用UTF-8编码
  - 使用小写字母
  - 使用双引号
- 标签规范
  - 标签名应该全部小写
  - 标签应该正确嵌套
  - 标签应该具有描述性
  - 示例：
  ```
  <header>
    <nav>
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </nav>
  </header>
  ```
- 属性规范
  - 属性名应该全部小写
  - 属性值应该使用双引号
  - 属性应该具有描述性
  - 示例：
  ```
  <img src="example.jpg" alt="Example Image">
  ```
- 注释规范
  - 注释应该解释代码的意图
  - 注释应该避免描述代码的实现细节
  - 示例：
  ```
  <!-- This is a header section -->
  <header>
    <h1>Page Title</h1>
  </header>
  ```
  

## CSS规范
- 语法规范
  - 使用CSS3语法
  - 使用UTF-8编码
  - 使用小写字母
  - 使用双引号
- 选择器规范
  - 选择器名应该全部小写
  - 选择器应该具有描述性
  - 选择器应该避免嵌套过深
  - 示例：
  ```
  .header {
    background-color: #fff;
    color: #333;
    font-size: 16px;
  }
  ```
- 属性规范
  - 属性名应该全部小写
  - 属性值应该使用双引号
  - 属性应该具有描述性
  - 示例：
  ```
  .header {
    background-color: #fff;
    color: #333;
    font-size: 16px;
  }
  ```
- 注释规范
  - 注释应该解释代码的意图
  - 注释应该避免描述代码的实现细节
  - 示例：
  ```
  /* This is a header section */
  .header {
    background-color: #fff;
    color: #333;
    font-size: 16px;
  }
  ```


## JavaScript规范
- 语法规范
  - 使用严格模式
  - 使用let和const声明变量
  - 使用箭头函数
  - 使用模板字符串
  - 使用解构赋值
  - 避免使用eval和with
- 变量规范
  - 变量名应该具有描述性
  - 避免使用全局变量
  - 避免使用魔法数字
- 函数规范
  - 函数应该具有描述性的名称
  - 函数应该只做一件事情
  - 函数应该尽可能短小
  - 函数应该避免副作用
- 类规范
  - 类名应该具有描述性
  - 类应该只做一件事情
  - 类应该尽可能短小
  - 类应该避免副作用
- 注释规范
  - 注释应该解释代码的意图，而不是描述代码的实现细节
  - 注释应该避免过度注释，只在必要时添加注释
  - 注释应该使用简洁明了的语言，避免使用口胡词或术语
  - 注释应该遵循一定的格式，例如：在注释前加上一个空格，使用句号结尾等



## React规范
- 语法规范
  - 使用ES6语法
  - 使用JSX语法
  - 使用PropTypes进行类型检查
- 组件规范
  - 组件名应该采用帕斯卡命名法，例如：Header, Footer, Sidebar。
  - 组件应该只做一件事情，尽可能短小，避免副作用。
  - 组件应该具有描述性的名称，例如：UserInfo, ProductList。
- 生命周期规范
  - 应该避免使用componentWillMount和componentWillReceiveProps生命周期方法。
  - 应该使用componentDidMount和componentDidUpdate生命周期方法。
  - 应该使用shouldComponentUpdate进行性能优化。
- 模板规范
  - 模板应该具有描述性，避免使用无意义的标签。
  - 模板应该避免嵌套过深，避免出现回调地狱。
  - 模板应该避免使用内联样式，应该使用外部样式表。
- 注释规范
  - 注释应该解释代码的意图，而不是描述代码的实现细节。
  - 注释应该避免过度注释，只在必要时添加注释。
  - 注释应该使用简洁明了的语言，避免使用口语词或术语。
  - 示例：
  ```
    import React from 'react';
    import PropTypes from 'prop-types';

    class UserInfo extends React.Component {
        static propTypes = {
        name: PropTypes.string.isRequired,
        age: PropTypes.number.isRequired,
        gender: PropTypes.oneOf(['male', 'female']).isRequired,
        };

        shouldComponentUpdate(nextProps, nextState) {
        return nextProps.name !== this.props.name || nextProps.age !== this.props.age || nextProps.gender !== this.props.gender;
        }

        render() {
        const { name, age, gender } = this.props;

        return (
            <div className="user-info">
            <h1>{name}</h1>
            </div>
            </div>
        </div>
        );
      }
    }
    ```



## Git团队协作规范

### 分支管理
- 主分支：master
- 开发分支：develop
- 功能分支：feature/xxx
- 修复分支：fix/xxx
- 发布分支：release/xxx

### 提交规范
- 每次提交前先拉取最新代码
- 提交信息格式：[type] description
- type包括：feat, fix, docs, style, refactor, test, chore
- description简明扼要，不超过50个字符

### 合并规范
- 功能分支合并到develop分支
- 修复分支合并到develop分支和master分支
- 发布分支合并到develop分支和master分支

### 版本管理
- 版本号格式：projectName.major.minor.patch.date
- projectName: 项目名
- major：大版本号，不兼容旧版本
- minor：小版本号，向下兼容
- patch：修复bug版本号
- date : 日期 YYMMDD

### 常用操作命令
- git clone：克隆远程仓库
- git branch：查看分支
- git checkout：切换分支
- git pull：拉取最新代码
- git add：添加修改文件
- git commit：提交修改
- git push：推送修改到远程仓库
- git merge：合并分支
- git tag：打标签
- git log：查看提交记录
- git status：查看工作区状态
- git remote：查看远程仓库
- git fetch：获取远程仓库最新代码
- git rebase：将本地修改合并到最新代码
- git reset：撤销提交
- git revert：撤销修改
- git stash：暂存当前修改
- git cherry-pick：选择某个提交应用到当前分支

## 代码审查流程
- 代码提交
  - 代码提交前应该进行本地测试和代码审查
  - 代码提交应该包含有意义的提交信息
- 代码审查
  - 代码审查应该在代码提交后尽快进行
  - 代码审查应该由至少两名团队成员进行
  - 代码审查应该注重代码的可读性、可维护性和可扩展性
  - 代码审查应该注重代码的安全性和性能
  - 代码审查应该注重代码的一致性和规范性
- 代码修改
  - 代码修改应该根据审查意见进行
  - 代码修改应该包含有意义的提交信息
- 代码合并
  - 代码合并应该在代码审查通过后进行
  - 代码合并应该由团队成员进行
  - 代码合并应该保证代码的一致性和规范性

## 代码审查规范
  - 代码风格
    - 代码应该遵循统一的代码风格和命名规范
    - 代码应该具有良好的可读性、可维护性和可扩展性
    - 代码应该注重安全性和性能
    - 代码应该注重一致性和规范性
  - 代码结构
    - 代码应该具有清晰的结构，避免出现过于复杂的嵌套
    - 代码应该避免出现重复的代码块，应该封装成函数或组件
    - 代码应该避免出现过长的函数或组件，应该拆分成多个小的函数或组件
  - 注释
    - 注释应该解释代码的意图，而不是描述代码的实现细节
    - 注释应该避免过度注释，只在必要时添加注释
    - 注释应该使用简洁明了的语言，避免使用口胡词或术语
  - 测试
    - 代码应该具有良好的测试覆盖率，避免出现未覆盖的代码块
    - 测试应该覆盖代码的各种情况，包括正常情况和异常情况
    - 测试应该具有可重复性，避免出现随机性的测试结果
  - 性能
    - 代码应该具有良好的性能，避免出现性能瓶颈
    - 代码应该避免出现过多的重复计算，应该使用缓存等技术进行优化
    - 代码应该避免出现过多的网络请求，应该使用缓存等技术进行优化
  - 功能
    - 功能应该满足业务需求，流程完善，功能完备
    - 浏览器兼容应该满足业务场景所需，无错乱显示，交互体验好

## 附录
- 参考文献
 1.   Airbnb JavaScript Style Guide. (n.d.). Retrieved October 12, 2021, from https://github.com/airbnb/javascript1. Airbnb JavaScript Style Guide. (n.d.). Retrieved October 12, 2021, from https://github.com/airbnb/javascript

2. Google HTML/CSS Style Guide. (n.d.). Retrieved October 12, 2021, from https://google.github.io/styleguide/htmlcssguide.html

3. React Official Documentation. (n.d.). Retrieved October 12, 2021, from https://reactjs.org/docs/getting-started.html

4. Git Official Documentation. (n.d.). Retrieved October 12, 2021, from https://git-scm.com/doc

- 术语表
1. 驼峰命名法：一种命名规范，单词首字母小写，后面单词首字母大写，例如：firstName, lastName。1. 驼峰命名法：一种命名规范，单词首字母小写，后面单词首字母大写，例如：firstName, lastName。
2. 帕斯卡命名法：一种命名规范，单词首字母大写，例如：Person, Car, Animal。
3. UTF-8编码：一种字符编码方式，支持所有Unicode字符。
4. HTML5：一种标记语言，用于创建网页。
5. CSS3：一种样式表语言，用于控制网页的样式和布局。
6. ES6：ECMAScript 6的简称，是JavaScript的一种标准，引入了许多新的语法和特性。
7. JSX：一种JavaScript语法扩展，用于创建React组件。
8. PropTypes：一种React库，用于进行类型检查。
9. Git：一种分布式版本控制系统，用于管理代码版本和协作开发。

- 缩略语表
1. HTML：Hypertext Markup Language，超文本标记语言
2. CSS：Cascading Style Sheets，层叠样式表
3. JS：JavaScript
4. JSX：JavaScript XML
5. DOM：Document Object Model，文档对象模型
6. API：Application Programming Interface，应用程序编程接口
7. UI：User Interface，用户界面
8. UX：User Experience，用户体验
9. HTTP：Hypertext Transfer Protocol，超文本传输协议
10. HTTPS：Hypertext Transfer Protocol Secure，安全超文本传输协议
11. URL：Uniform Resource Locator，统一资源定位符
12. URI：Uniform Resource Identifier，统一资源标识符
13. AJAX：Asynchronous JavaScript and XML，异步JavaScript和XML
14. JSON：JavaScript Object Notation，JavaScript对象表示法
15. XML：Extensible Markup Language，可扩展标记语言
16. SQL：Structured Query Language，结构化查询语言
17. NoSQL：Not Only SQL，非关系型数据库
18. ORM：Object-Relational Mapping，对象关系映射
19. MVC：Model-View-Controller，模型-视图-控制器
20. MVVM：Model-View-ViewModel，模型-视图-视图模型
21. SPA：Single Page Application，单页应用程序
22. SSR：Server-Side Rendering，服务器端渲染
23. CSR：Client-Side Rendering，客户端渲染
24. CDN：Content Delivery Network，内容分发网络
25. SEO：Search Engine Optimization，搜索引擎优化
26. CMS：Content Management System，内容管理系统
27. WYSIWYG：What You See Is What You Get，所见即所得
28. IDE：Integrated Development Environment，集成开发环境
29. CLI：Command Line Interface，命令行界面
30. API：Application Programming Interface，应用程序编程接口
31. SDK：Software Development Kit，软件开发工具包
32. VCS：Version Control System，版本控制系统
33. CI/CD：Continuous Integration/Continuous Deployment，持续集成/持续部署

## 版本记录

### 1.0.0.211012
- 初版发布
- 包含HTML、CSS、JavaScript、React和Git团队协作规范
- 包含代码审查流程和规范

