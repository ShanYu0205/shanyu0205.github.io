# Hugo个人博客搭建(极简版)

<!--more-->

**Hugo个人博客搭建**

---
## 1 快速开始
- 基于Mac系统
- 主要流程
  - 1. 安装相关环境
    - 安装`git`
    - 安装`Homebrew`
    - 安装`hugo`
  - 2. 博客相关操作
    - 新建自己的博客站点
    - 设置主题
    - 本地启动博客
    - 构建网站
  - 3. 服务器部署(github)
    - 将博客部署到github远端

---
## 2 相关环境安装
### 2.1 安装`git`
**打开终端,即terminal**, 输入以下命令，回车执行
```
git --version
```
如果已经安装，则会显示安装的版本信息；若没有安装，则会提示安装，按照提示安装即可。


---
### 2.2 安装`Homebrew`
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
同样可以通过，`brew -v`来检查是否已经安装或者是否安装成功


---
### 2.3 安装`hugo`
```
brew install hugo 

# 检查安装成功
hugo version
```

---
## 3 博客相关操作
### 3.1 新建自己的博客站点
首先新建一个网站，名字随便起，这里以 `myblog` 为例，[PATH] 为自己想要存放的路径，`myblog` 为网站名。

```
hugo new site [PATH]/myblog
```

---
### 3.2 设置主题
这里以**LoveIt**为例, 该主题仓库是：https://github.com/dillonzq/LoveIt

通常来说，我们将这个主题直接克隆`clone`到`theme`目录即可
```
# 先进入myblog目录下
cd [PATH]/myblog

# 克隆操作
git clone https://github.com/dillonzq/LoveIt.git themes/LoveIt
```

---
### 3.3 创建第一篇文章
```
hugo new posts/first_post.md
```


---
### 3.4 本地启动博客
```
hugo serve
```

去查看 http://localhost:1313.

<center><img src="/content/posts/serverfile/1.png"></center>

---
### 3.4 构建网站
当你准备好部署你的网站时, 运行以下命令:

```
hugo
```


会生成一个 `public` 目录, 其中包含你网站的所有静态内容和资源. 现在可以将其部署在任何 Web 服务器上

---
### 3.5 将博客部署到github远端
1. 首先在自己的GitHub赏创建一个新的仓库，名称必须为`Github用户名.github.io`，例如我的就是`shanyu0205.github.io`,用户名必须全小写.

{{< image src="/posts/serverfile/2.png" >}}

2. 创建成功后，将自己的博客文件夹下的`public`文件夹下的所有文件复制到`Github用户名.github.io`仓库下，然后提交到远端即可。

> 所有git命令都应在`public`文件夹下执行，应为`public`文件夹下才是真正的博客文件，其他的都是配置文件

```python
cd public  # 进入public文件夹
git init   
git add .  # 注意后面有个点
git commit -m "我的第一个hugo博客" 
git remote add origin "https://github.com/"你的库的地址"" # 与远端的git仓库进行关联
git push   # 如果是第一次提交，需要加上-u参数: git push -u origin master
```
> 注意：由于Github修改了关于公钥的条例，所以在`push`的时候,可能会出现`Permission denied`的错误
> 所以需要在`push`之前,先在Github的`Settings`的`Developer settings`里,找到`Personal access token`,并选择`token(classic)`，然后点击`Generate new token`，然后在弹出的页面中，勾选`repo`，然后点击`Generate token`，然后将生成的token复制下来输入终端.
> 
> 详情请见：<https://blog.csdn.net/qq_43382853/article/details/119221234>

3. 接下来就可以通过`[].github.io`直接访问自己的博客了。`[]`中填写自己的github用户名

> 此时，如果你的博客还没有显示出来，那么就需要等待一段时间，因为github需要一段时间来构建你的博客，一般来说，等待时间不会超过10分钟。
---

{{< image src="/posts/serverfile/dashang.jpeg" height="30%" width="30%" caption="感谢你的支持"  >}}








