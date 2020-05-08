### python爬虫项目

该项目整合了有道、百度、谷歌以及金山词霸的翻译接口，可以实现四个翻译接口的同步翻译，可以通过比较不同翻译结果选择合适的翻译结果，感觉还是比较方便，平时翻译都是用的我自己写的这个翻译软件。



#### 爬取有道翻译

1. 解决反爬虫机制

~~~python
 	u = 'fanyideskweb'
    d = content  # content 为翻译的内容
    f = str(int(time.time()*1000) + random.randint(1,10))  # 时间戳
    c= 'rY0D^0\'nM0}g5Mm1z%1G4'
    sign = hashlib.md5((u + d + f + c).encode('utf-8')).hexdigest()   # md5加密，生成一个随机数
~~~

2. 获取有道翻译数据表单

~~~python
 data = {}
    # data 有道翻译数据表单
    data['i'] = content  # content 为需要翻译的内容
    data['from'] = 'AUTO'
    data['to'] = 'AUTO'
    data['smartresult'] = 'dict'
    data['client'] = 'fanyideskweb'
    data['salt'] = f  # salt 与 sign 反爬机制 ，每次都会变化 salt就是时间戳
    data['sign'] = sign # 使用的是u + d + f + c的md5的值。
    data['ts'] = '1551506287219'
    data['bv'] = '97ba7c7fb78632ae9b11dcf6be726aee'
    data['doctype'] = 'json'
    data['version'] = '2.1'
    data['keyfrom'] = 'fanyi.web'
    data['action'] = 'FY_BY_REALTIME'
    data['typoResult'] = 'False'
~~~

3. 发起request请求

~~~python
	url = "http://fanyi.youdao.com/"
    head={}
    head['User-Agent'] = 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/65.0.3325.181 Safari/537.36'  # 模拟浏览器
    data = urllib.parse.urlencode(data).encode('utf-8')
    request = urllib.request.Request(url=url,data=data,headers=head, method='POST')

~~~

4. 获取response并转换成json格式

~~~python
 	response  = urllib.request.urlopen(request)
    line = json.load(response)  # 将得到的字符串转换成json格式
~~~

5. 爬取json文本中翻译结果

```python
text = line['translateResult'][0][0]['tgt']
```

#### 爬取百度翻译

1. 

#### 爬取谷歌翻译



#### 爬取金山翻译



