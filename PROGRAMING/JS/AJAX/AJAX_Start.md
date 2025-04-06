## Day1：

### 1、 初始 AJAX

AJAX就是使得浏览器与数据库进行通讯的技术。

1. 学习axios库
2. 学习XMLHttpRequest对象的使用，了解AJAX的底层原理

### 2、 认识 URL

URL（Uniform resource locator）

统一资源定位符，用于索引网络中的资源。

### 3、 查询参数

浏览器给服务器提供额外的信息，让服务器返回浏览器想要的数据。

#### axios - 查询参数

使用 axios 提供的 params 选项，携带参数名和值

```javaScript
axios({
	ulr: '...'
	params: {
		参数名：值
}
})
```

类似于 json ，即 python 字典。

### 5、 常用请求方法和数据提交

| 请求方法 | 操作         |
| ---------- | -------------- |
| ***GET***         | 获取数据     |
| ***POST***         | 提交数据     |
| PUT      | 修改全部数据 |
| DELETE   | 删除数据     |
| PATCH    | 修改部分数据 |

#### 提交数据：

axios 请求配置

> url：请求的URL网址
>
> method：请求的方法，GET可以省略
>
> data：提交数据

```JavaScript
axiox({
	url:
	method:
	data: {
		username:
		password:
	}
})
```

#### 错误处理：

对错误进行处理

```JavaScript
axios({
}).then(result => {
	// 处理数据
}).catch(error => {
	// 处理错误
})
```

### 6、 HTTP协议 - 请求报文

HTTP协议：规定了浏览器发送以及服务器返回内容的格式

请求报文：浏览器按照HTTP格式的要求，发送给服务器的内容

#### 请求报文的格式

* 请求行：请求方法、URL、协议
* 请求头：以键值对的方式携带的附加信息
* 请求体：所携带的数据

#### 请求报文的错误排查

### 7、 HTTP协议 - 响应报文

从服务器返回浏览器的内容，叫做响应报文

#### HTTP响应状态码

| 状态码 | 说明       |
| -------- | ------------ |
| 1xx    | 信息       |
| 2xx    | 成功       |
| 3xx    | 重定向消息 |
| 4xx    | 客户端错误 |
| 5xx    | 服务端错误 |

### 8、 接口文档

接口文档：描述接口的文档，由后端提供

接口：使用 AJAX 和服务器通讯时，使用的 URL、请求方法和参数

## Day3：AJAX原理 - XMLHttpRequest

定义：XHR对象用于与服务器交互，通过XMLHttpRequest可以在不刷新页面的情况下，请求特定的URL，获取数据。

关系：axios内部包含着XMLHttpRequest

### 为什么学习XHR？

- 了解AJAX的底层原理
- 有更多与服务器数据进行通讯的方法
- 了解axios内部原理

### XHR使用步骤

1. 创建XHR对象
1. 调用open方法，设置url和请求方法
1. 监听loadend事件，接收结果
1. 调用send方法，发送请求

### XHR对象查询参数

浏览器给服务器提供额外的信息，让服务器返回浏览器想要的数据。

语法`http://www.example.com?参数名1=值1&参数名2=值2`

### XHR对象提交数据

使用XHR对象的send方法，提交数据

```JavaScript
xhr.send('参数名1=值1&参数名2=值2')

```

请求头设置 Content-Type：application/json

请求体携带 Json 字符串

#### XHR对象提交数据 - JSON格式

使用XHR对象的send方法，提交数据

```JavaScript
xhr.send(JSON.stringify({
	参数名1：值1，
	参数名2：值2
}))
```

#### XHR对象提交数据 - FormData格式

使用XHR对象的send方法，提交数据

```JavaScript
xhr.send(new FormData())
```

### promise

Promise：表示一个异步操作的最终完成（或失败）及其结果值的表示法。

Promise对象有三种状态：

- pending：初始状态，既不是成功，也不是失败
- fulfilled：操作成功完成
- rejected：操作失败

好处：

- 逻辑更清晰
- 了解了axios函数内部运行机制
- 能解决回调函数地狱的问题

