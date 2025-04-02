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