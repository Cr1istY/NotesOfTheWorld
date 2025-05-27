# JavaWeb

[ke](https://www.bilibili.com/video/BV1UN411x7xe?spm_id_from=333.788.videopod.episodes&vd_source=1925e38de9174c77ef2d3cfdc2dea75d)

课程框架：

1. 前端：HTML、CSS、JS
2. 后端：TomCat、JavaEE、MVC
3. 完整工程化：ES6、Node.js、npm、Vite、Vue3、Router4、axios、Pinia、ElementPlus

本次课程

1. 为后端同学设计，快速掌握前端工程化
2. 遵循教学一般规律
3. 贯穿练习
4. 知识完整

学习路线：

1. Java基础
2. 微头条系统（前后端分离开发）
3. 数据结构与算法
4. 后端工程化
5. 全栈商用级项目
6. 架构师核心
7. 大型企业分布式项目
8. 大数据模块
9. AI模块

## 前端部分

### HTML部分

### CSS部分

### JavaScript部分

## 案例开发

### 日程管理第一期

#### 1. 登录页及校验

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>登录页面</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background-color: #f5f5f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .login-container {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
            width: 350px;
        }

        .login-header {
            text-align: center;
            margin-bottom: 25px;
        }

        .login-header h1 {
            color: #333;
            font-size: 24px;
            margin-bottom: 10px;
        }

        .login-header p {
            color: #777;
            font-size: 14px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #555;
            font-size: 14px;
        }

        .form-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 14px;
        }

        .form-group input:focus {
            outline: none;
            border-color: #4a90e2;
        }

        .login-button {
            width: 100%;
            padding: 12px;
            background-color: #4a90e2;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
        }

        .login-button:hover {
            background-color: #3a7bc8;
        }

        .forgot-password {
            text-align: right;
            margin-top: 10px;
        }

        .forgot-password a {
            color: #4a90e2;
            text-decoration: none;
            font-size: 14px;
        }

        .forgot-password a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
<div class="login-container">
    <div class="login-header">
        <h1>用户登录</h1>
        <p>请使用您的账号和密码登录</p>
    </div>

    <form method="post" action="/user/login" onsubmit="return checkForm();">
        <div class="form-group">
            <label for="username">用户名</label>
            <input type="text" id="username" placeholder="请输入账号" onblur="checkUsername();">
        </div>

        <div class="form-group">
            <label for="password">密码</label>
            <input type="password" id="password" placeholder="请输入密码" onblur="checkPassword();">
        </div>
        <div>
            <span id="inputMsg"></span>
        </div>


        <button type="submit" class="login-button">登录</button>

        <div class="forgot-password">
            <a href="#">注册</a>
            <a href="#">忘记密码？</a>
        </div>
    </form>
</div>

<script>
    function checkUsername() {
        // 定义正则表达式
        let usernameReg = /^[a-zA-Z0-9]{5,10}$/
        // 获得用户在页面输入的信息
        let username = document.getElementById('username').value;

        let usernameMsg = document.getElementById('inputMsg');

        if (!usernameReg.test(username)) {
            usernameMsg.innerText = '用户名格式必须是5-10位'
            return false
        } else {
            return true;
        }
    }

    function checkPassword() {
        let passwordReg = /^[a-zA-Z0-9]{5,10}$/
        let password = document.getElementById('password').value;
        let passwordMsg = document.getElementById('inputMsg');

        if (!passwordReg.test(password)) {
            passwordMsg.innerText = '密码格式必须是5-10位'
            return false
        } else {
            return true;
        }

    }

    function checkForm() {
        let flag1 = checkUsername();
        let flag2 = checkPassword();
        return flag1 && flag2
    }

</script>
</body>
</html>
```

#### 2. 注册页及校验

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>登录页面</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Arial', sans-serif;
    }

    body {
      background-color: #f5f5f5;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .login-container {
      background-color: white;
      padding: 30px;
      border-radius: 8px;
      box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
      width: 350px;
    }

    .login-header {
      text-align: center;
      margin-bottom: 25px;
    }

    .login-header h1 {
      color: #333;
      font-size: 24px;
      margin-bottom: 10px;
    }

    .login-header p {
      color: #777;
      font-size: 14px;
    }

    .form-group {
      margin-bottom: 20px;
    }

    .form-group label {
      display: block;
      margin-bottom: 8px;
      color: #555;
      font-size: 14px;
    }

    .form-group input {
      width: 100%;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 4px;
      font-size: 14px;
    }

    .form-group input:focus {
      outline: none;
      border-color: #4a90e2;
    }

    .login-button {
      width: 100%;
      padding: 12px;
      background-color: #4a90e2;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 16px;
      transition: background-color 0.3s;
    }

    .login-button:hover {
      background-color: #3a7bc8;
    }

    .forgot-password {
      text-align: right;
      margin-top: 10px;
    }

    .forgot-password a {
      color: #4a90e2;
      text-decoration: none;
      font-size: 14px;
    }

    .forgot-password a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>
<div class="login-container">
  <div class="login-header">
    <h1>用户注册</h1>
    <p>请使用您的账号和密码登录</p>
  </div>

  <form method="post" action="/user/login" onsubmit="return checkForm();">
    <div class="form-group">
      <label for="username">用户名</label>
      <input type="text" id="username" placeholder="请输入账号" onblur="checkUsername();">
    </div>

    <div class="form-group">
      <label for="password">密码</label>
      <input type="password" id="password" placeholder="请输入密码" onblur="checkPassword();">
    </div>
    <div>
      <span id="inputMsg"></span>
    </div>


    <button type="submit" class="login-button">注册</button>

    <div class="forgot-password">
      <a href="#">忘记密码？</a>
    </div>
  </form>
</div>

<script>
  function checkUsername() {
    // 定义正则表达式
    let usernameReg = /^[a-zA-Z0-9]{5,10}$/
    // 获得用户在页面输入的信息
    let username = document.getElementById('username').value;

    let usernameMsg = document.getElementById('inputMsg');

    if (!usernameReg.test(username)) {
      usernameMsg.innerText = '用户名格式必须是5-10位'
      return false
    } else {
      return true;
    }
  }

  function checkPassword() {
    let passwordReg = /^[a-zA-Z0-9]{5,10}$/
    let password = document.getElementById('password').value;
    let passwordMsg = document.getElementById('inputMsg');

    if (!passwordReg.test(password)) {
      passwordMsg.innerText = '密码格式必须是5-10位'
      return false
    } else {
      return true;
    }

  }

  function checkForm() {
    let flag1 = checkUsername();
    let flag2 = checkPassword();
    return flag1 && flag2
  }

</script>
</body>
</html>
```

### XML TomCat HTTP

#### XML

Extensible Markup Language 可扩展的标记语言

用于配置文件

- 可拓展：XML允许自定义标签，但不代表你可以随便写

```xml

```

1. 只有一个根标签
2. 第一行写法固定
3. xml有约束，用于限定xml内部能编写的内容

##### DOM4J进行XML解析

### Tomcat

TomCat是一个开源的Java Web服务器

#### TomCat目录

1. bin - tomcat相关命令
2. conf - tomcat配置文件
3. lib - tomcat依赖包
4. logs - tomcat日志文件
5. temp - tomcat临时文件
6. work - tomcat工作目录，jsp技术有关
7. webapps - tomcat部署的web项目

#### Web项目结构

- app
   - index.html
   - static
     - css
     - js
     - img

#### Tomcat部署项目的方式

1. 直接扔到webapps目录中
2. 添加配置文件

#### IDE 关联 Tomcat

Tomcat挂载的是用java写好的app

我们需要使用idea来实现工程的建设和打包

1. 建立tomcat和idea的联系
2. 创建使用idea，javaWeb项目
3. 在Web工程中开发代码
4. 使用idea将工程构建成app
5. 使用idea将app部署到tomcat中

##### IDEA 与 tomcat 底层原理

IDEA在底层，创建了一个tomcat的虚拟副本

存放的仅仅是和app相关的配置文件

### HTTP

Tomcat默认使用HTTP协议1.1

1. 交互的模式：请求（客户端向服务端）-响应（服务端向客户端）模式
2. 数据的格式：请求时发送的数据，被称为请求报文，响应则称为响应报文

#### HTTP请求和响应报文格式

##### 报文的格式

报文 = 报文行 + 报文头 + 报文体

#### 常见响应状态码

- 200 - 请求成功
- 302 - 重定向
- 304 - 使用本地缓存
- 404 - 资源不存在
- 405 - 资源被拒绝访问
- 500 - 服务器异常

### Servlet

#### 动态资源与静态资源

- 静态资源：图片，css，js，html，txt，ico
- 动态资源：需要在程序运行时通过代码运行生成的资源

#### 什么是Servlet

Servlet是运行在服务端上的java小程序，是sum公司提供的一套定义动态资源规范，从代码层面上来讲Servlet就是一个接口

tomcat接收到请求后，会将请求的报文信息转换为一个HttpServletRequest对象

该对象中包含了请求中的所有信息，及请求行、请求头、请求体

同时，tomcat会创建一个HttpServletResponse对象，用于装载要响应给客户端的信息

该对象中包含了响应报文信息，及响应行、响应头、响应体

我们需要自定义一个class 实现 Servlet 接口

tomcat根据请求中的资源路径，找到对应的servlet，将servlet实例化，调用servlet方法，同时将HttpServletRequest和HttpServletResponse作为参数传递给servlet方法

我们就可以在servlet方法中：

1. 从request对象中获取所有信息，一般为参数
2. 根据参数，生成获取要响应给客户端的数据
3. 将响应的数据放入response对象中，并设置响应头，告诉客户端本次请求的响应类型和编码格式

#### Servlet开发流程

1. 创建Servlet类，继承HttpServlet抽象类
2. 重写service(HttpServletRequest request, HttpServletResponse response)方法
3. 在service方法中，定义业务处理代码
4. 在web.xml中配置Servlet对应的请求映射路径
   1. 配置Servlet类，并起一个别名

#### Servlet开发中的常见问题

1. Servlet-api.jar 导入问题
2. Content-Type响应头问题

#### Servlet_url-pattern的一些特殊写法
