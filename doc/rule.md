
# 团队协作规范

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

## 代码操作规范

### 代码提交：

1. 代码提交前应该进行本地测试和代码审查：在提交代码前，你应该确保你的代码在本地已经通过了所有的测试，并且已经经过了代码审查，确保代码的质量。
2. 代码提交应该包含有意义的提交信息：提交信息应该清晰地描述出这次提交的内容和目的，使得其他团队成员能够理解这次提交的内容。

### 代码审查：

1. 代码审查应该在代码提交后尽快进行：尽快进行代码审查可以确保问题被及时发现并修复，避免问题在代码库中积累。
2. 代码审查应该由至少两名团队成员进行：这样可以确保不同的视角和经验被考虑到，提高代码质量。
3. 代码审查应该注重代码的可读性、可维护性和可扩展性：这些都是评估代码质量的重要因素。
4. 代码审查应该注重代码的安全性和性能：安全性和性能是代码质量的重要方面，需要在代码审查中特别关注。
5. 代码审查应该注重代码的一致性和规范性：这可以帮助团队保持一致的编码风格和规范。

### 代码修改：

1. 代码修改应该根据审查意见进行：代码审查的目的是找出代码中的问题并提出建议，代码修改应根据这些建议进行。
2. 代码修改应该包含有意义的提交信息：同样，修改后的提交信息也应该清晰地描述出修改的内容和目的。

### 代码合并：

1. 代码合并应该在代码审查通过后进行：只有通过了代码审查的代码才应该被合并到主分支，以确保主分支的代码质量。
2. 代码合并应该由团队成员进行：通常，团队成员会负责合并他们的代码，这样可以确保他们对合并的代码有深入的理解。
3. 代码合并应该保证代码的一致性和规范性：在合并代码时，需要确保代码的一致性和规范性，避免因为合并导致的问题。

## 代码审查规范


### 代码风格：

* 统一的代码风格和命名规范：这样可以使代码更易于理解和维护。比如，使用特定的缩进方式（如空格或制表符），统一的使用命名规则（如驼峰命名法）等。
* 可读性、可维护性和可扩展性：这是评估代码质量的重要标准。可读性高的代码容易理解，可维护性强的代码容易修改和调试，可扩展性的代码容易增加新功能。
* 安全性和性能：代码不应引入安全漏洞，如SQL注入、跨站脚本等，同时应优化性能，避免不必要的计算或网络请求。
* 一致性和规范性：团队或项目中应遵循一致的编码规范，以减少交流和理解的困难。

### 代码结构：

* 清晰的结构：好的代码结构应该清晰，使人能快速理解其组织方式。
* 避免过度嵌套：过度的嵌套会使代码难以理解。
* 避免重复代码：重复的代码会增加维护的难度和维护成本。
* 拆分长函数和组件：过长或复杂的函数或组件同样难以理解和维护。

### 注释：

* 解释代码意图：注释应该解释代码的目的和设计思想，而不是详细描述每一步的操作。
* 避免过度注释：过多的注释会使得代码难以阅读，而且当代码变化时，注释也需要更新，增加了维护成本。
* 使用简洁明了的语言：使用简洁明了的语言可以增加注释的可读性。避免使用难以理解的行话或术语。

### 测试：

* 良好的测试覆盖率：测试覆盖率是衡量测试完整性的一个重要指标，好的测试覆盖率可以确保代码质量。
* 各种情况覆盖：测试应该涵盖各种正常和异常的情况，包括边界条件和异常输入。
* 可重复性：好的测试应该是可以重复运行的，不受环境或其他因素影响。

### 性能：

* 良好的性能：好的代码应该尽可能的高效，不占用过多资源。
* 避免重复计算：重复计算会消耗不必要的计算资源。使用缓存或其他技术可以避免这种浪费。
* 避免过多网络请求：网络请求通常会带来延迟，使用缓存和其他技术可以减少网络请求的数量。

### 功能：

* 满足业务需求：代码或系统应该能够满足业务的需求，解决特定的问题或完成特定的任务。
* 流程完善，功能完备：这表示系统应该具有完整的业务流程，并且每个功能都应该完整且能够满足需求。
* 浏览器兼容性：对于Web应用，浏览器兼容性是很重要的，应用应该在各种主流浏览器上都能正常运行且表现良好。

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

