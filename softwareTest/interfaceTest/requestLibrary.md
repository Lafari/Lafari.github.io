# 发送请求

`requests.get(url,params=None,**kwargs)`  
`requests.post(url,data=None,json=None,**kwargs)`  
`requests.put(url,data=None,**kwargs)`  
`requests.delete(url,**kwargs)`  

-前面的四个方法底层其实都是调用下面这个方法  
`requests.request(method,url,**kwargs)`  

-上面这个方法调用的是下面这个方法(区别在于，这个方法能够自动化的关联有cookie关联的接口)  
`session.request(method=method,url=url,**kwargs)`  
method=method, 请求方式

