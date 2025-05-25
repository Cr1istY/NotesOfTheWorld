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
