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