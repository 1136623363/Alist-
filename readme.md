# 使用Alist云盘挂载程序API接口上传文件到云盘(阿里云盘等)

```
import requests
from requests_toolbelt import MultipartEncoder
from urllib.parse import quote

url = "http://xxxxxx:5244/api/fs/form"

filename = 'xxxx'  #需要上传的文件

data = MultipartEncoder(
    fields={
        'file': (filename, open(filename, 'rb'))
    }
)

filename_new = quote(filename,'utf-8')  #对文件名进行URL编码

headers = {
   'Authorization':'xxxxxxxx',
   'Content-Type':data.content_type,
   'file-path':'/Alidrive/filename_new'    #上传到云盘的位置以及文件名（填写的文件名必须是URL编码后的）
}

res = requests.put(url=url,data=data,headers=headers)
print(res.text)
```

## 上传成功的反馈
![image](/upload/2023/03/image.png)

### 引用帖子
[https://zhuanlan.zhihu.com/p/587004798](https://zhuanlan.zhihu.com/p/587004798)
[https://github.com/alist-org/alist/discussions/1349](https://github.com/alist-org/alist/discussions/1349)
