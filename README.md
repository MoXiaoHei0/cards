# 自介卡工厂（GitHub 版）

一个不需要服务器、不需要域名备案的自介卡生成器。
整个平台就是一个网页，卡片数据存在你自己浏览器里，发布时直接把网页文件推到 GitHub Pages 上。

---

## 一、第一次部署（只做一次，10 分钟）

### 1. 建一个仓库

1. 打开 https://github.com/new
2. Repository name 填 `cards`（想叫别的也行，后面设置里对应改）
3. 选 **Public**
4. 点 **Create repository**

### 2. 把文件传上去

1. 在新仓库页面点 **uploading an existing file**（或者 Add file → Upload files）
2. 把本文件夹里的东西**整个拖进去**：
   - `index.html`
   - `_tpl/`
   - `_assets/`
3. 下面 Commit changes 那里点 **Commit changes**

> 如果浏览器不认拖文件夹：先建好 `_tpl`、`_assets` 两个文件夹（Add file → Create new file，文件名写 `_tpl/redblack.html` 就会自动建目录），再分别上传对应的文件。

### 3. 打开 Pages

1. 仓库页面 → **Settings** → 左边 **Pages**
2. Source 选 **Deploy from a branch**
3. Branch 选 **main**，目录选 **/ (root)**
4. 点 **Save**

等 1～2 分钟，你的平台地址就有了：

```
https://你的用户名.github.io/cards/
```

打开就是密码框。

### 4. 拿一个授权码（token），让平台能往仓库里写卡片

1. 打开 https://github.com/settings/tokens?type=beta
2. 点 **Generate new token**
3. Token name 随便写，比如 `cards`
4. Expiration 选 **No expiration**（不然到期要重弄）
5. **Repository access** 选 **Only select repositories** → 选刚建的 `cards`
6. **Permissions** → 展开 **Repository permissions** → 找到 **Contents**，改成 **Read and write**
7. 底部 **Generate token**，复制那串 `github_pat_...`

### 5. 在平台里填设置

1. 打开平台，输管理密码 `1234`
2. 右上角 **发布设置**
3. 仓库填 `你的用户名/cards`
4. 授权码粘贴进去
5. 链接前缀填 `https://你的用户名.github.io/cards/`
6. 点 **测试连接**，显示「连接正常」就点 **保存**

---

## 二、日常怎么用

1. 输密码进入（管理密码 `1234`，进门密码 `8888`，右上角可以改）
2. **＋ 新建卡片**
3. 选模板（红黑信纸 / 蓝色沉潜），右边实时预览
4. 填内容；标题写**你自己或对方的名字**，方便认
5. 链接后缀填拼音，比如 `shurong` → 链接就是 `.../cards/p/shurong.html`
   - 不填会用随机字母
   - 重名会自动加 2、3
6. 点 **保存**（这时只存在你浏览器里）
7. 回列表，点卡片上的 **发布**，等十几秒
8. 弹出链接，复制发给对方

改内容：点 **编辑**，改完 **保存**，再点一次 **重新发布**（GitHub 要重新生成一遍，等十几秒）。

---

## 三、要清楚的几件事

- **数据存在你这台电脑的浏览器里。** 换电脑、换浏览器、清缓存，列表就空了（已经发布出去的网页不受影响，链接照样能打开）。
- **卡片密码是假的。** 网页是纯静态的，懂技术的人能从网页里翻出内容。纯链接不公开就够用了。
- **改完必须重新发布。** 保存只改本地，不点发布，网上还是旧的。
- **国内偶尔打不开 github.io。** 平时没问题，抽风时等一会儿再开。
- **图片会内嵌在网页里。** 上传时会自动压到 900px 以内，一张卡大概几百 KB。
- **默认进门口令 `8888`、管理口令 `1234`**，只在你自己这台浏览器生效（因为存在本地）。

---

## 四、文件说明

```
index.html          平台本体（就是你打开的那个网页）
_tpl/redblack.html  红黑信纸模板（已内联样式，不能直接当卡片打开）
_tpl/sink.html      蓝色沉潜模板
_assets/            公共素材：默认封面、默认头像、两首背景音乐
p/                  发布后自动生成的卡片网页（一开始没有这个目录，第一次发布会自动建）
```
