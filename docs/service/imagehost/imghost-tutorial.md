# 絢咲萌图床使用教程

## 新版图床获取 Token 方法

企业版用户可通过 GUI 方式获取 Token 。

打开 [Token](https://img.ASMS.cn/user/tokens) 页面，点击 `创建 Token` 以创建 Token。

输入 Token 的名称，例如该 Token 的用途，或使用的网站等，勾选该 Token 对应的权限，点击 `保存` ，复制出现的Token即可。

一定要保管好该 Token ，一旦丢失只能撤销重铸。

## 图片压缩

絢咲萌图床所有用户(包括游客)都支持图片压缩。

### WebP 压缩

在图片链接后加上 `/wp{level}` 即可。

例如，这是一张约10M的测试图片：
```
https://img-cdn-cos.lolicon.team/IMAGES/1/2023/02/20/1x63f254e2e530f.jpg
``` 

WebP压缩后仅剩921多KB。

```
https://img-cdn-cos.lolicon.team/IMAGES/1/2023/02/20/1x63f254e2e530f.jpg/wp60
```

#### 所有WebP压缩等级

- `wp60` : 60% 质量
- `wp70` : 70% 质量
- `wp80` : 80% 质量
- `wp90` : 90% 质量
- `wp` : 100% 质量



## 对接PicGO

### 方法一： `自定义Web图床` 插件

按如下方式填写即可：

- API地址：https://your.domain/api/v1/upload
- POST 参数名：file
- JSON路径：data.links.url
- 自定义请求头：{"Authorization": "Bearer your_token"}
- 其他选填

### 方法二：`lankong` 插件

按如下方式填写：

- 打开 `Lsky Pro Version`
- Server： 填写你的图床地址即可，不需要 `/api/v1/upload` ，**不要以 `/` 结尾**
- Auth Token： `Bearer Your_token`
- Sync Delete： 打开即可通过PicGo删除图片
- 其他选填


## 获取Token

### CURL

- 简洁一点：

    ```
    curl -X POST -F "email=your_email@address" -F "password=your_passwd" https://your.domain/api/v1/tokens
    ```
- 展开：
    ```
    curl --location --request POST 'https://your.domain/api/v1/tokens' \
    --form 'email="your_email@address"' \
    --form 'password="your_passwd"'
    ```

### Shell wget
```
wget --no-check-certificate --quiet \
  --method POST \
  --timeout=0 \
  --header '' \
  --body-data 'email=your email address&password=password' \
   'https://pic.iqy.ink/api/v1/tokens'
```

都差不多。