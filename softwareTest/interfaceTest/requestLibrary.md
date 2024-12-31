# 发送请求

`requests.get(url,params=None,**kwargs)`  
`requests.post(url,data=None,json=None,**kwargs)`  
**data和json的区别：取决于你需要传递参数类型**    
  file：文件上传  
  form-data：表单和文件上传  
  x-www-form-urlencode：纯表单  
  raw：json(参数为json)  
  binary：把文件转化为二进制文件传输  
`requests.put(url,data=None,**kwargs)`  
`requests.delete(url,**kwargs)`  

**前面的四个方法底层其实都是调用下面这个方法**  
`requests.request(method,url,**kwargs)`  

**上面这个方法调用的是下面这个方法(区别在于，这个方法能够自动化的关联有cookie关联的接口)**  
`session.request(method=method,url=url,**kwargs)`  
`method=method` 请求方式  
`url=url` 请求路径  
`params=None` get请求传参  
`data=None`  post或者put请求传参  
`json=None` post请求传参  
`headers=None` 请求头  
`cookies=None` Cookie  
`files=None` 文件上传  
`auth=None` 鉴权  
`timeout=None` 超时处理  
`allow redirects=True` 是否允许重定向  
`proxies=None` 设置代理  
`hooks=None` 钩子  
`stream=None` 文件下载  
`verify=None` 证书验证  
`cert=None` CA证书
