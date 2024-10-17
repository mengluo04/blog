---
layout: blog
title: 使用python打包文件夹上传到七牛云
date: 2024-10-17 11:02:06
categories: 
- 技巧
tags:
- python
- 七牛
---
> 使用七牛云备份数据

```python
import os
import datetime
import zipfile
from qiniu import Auth, put_file, etag, urlsafe_base64_encode

def create_zip_archive(source_dir, output_filename):
    with zipfile.ZipFile(output_filename, 'w', zipfile.ZIP_DEFLATED) as zipf:
        for root, dirs, files in os.walk(source_dir):
            for file in files:
                zipf.write(os.path.join(root, file))

def upload_to_qiniu(localfile, bucket_name, key):
    # 替换为你的七牛云Access Key和Secret Key
    access_key = 'your_access_key'
    secret_key = 'your_secret_key'

    q = Auth(access_key, secret_key)
    token = q.upload_token(bucket_name, key, 3600)
    ret, info = put_file(token, key, localfile)
    print(info)

# 获取昨天的日期
yesterday = datetime.datetime.now() - datetime.timedelta(days=1)
date_str = yesterday.strftime('%Y/%m/%d')

# 指定目录
source_dir = '/path/to/your/directory'

# 输出文件名
output_filename = f'data_{yesterday.strftime("%Y%m%d")}.zip'

# 创建ZIP存档
create_zip_archive(source_dir, output_filename)

# 构建目标路径
remote_path = f'yunzai/data/backup/{date_str}/data.zip'

# 上传到七牛云
upload_to_qiniu(output_filename, 'your_bucket_name', remote_path)

# 清理本地临时文件
os.remove(output_filename)
```