---
title: Hexo+GitHub搭建个人博客
tags: start
---

## 利用Hexo搭建个人博客（windows）

本教程采用Github + Hexo的方式搭建博客，优点是免费。大致流程如下

1. 安装[node.js](http://nodejs.cn/) 和 [Git](https://git-scm.com/download/win)
2. 申请Github账号，并开启github免费blog
3. 本地搭建Hexo 的blog站点，发布到Github上
4. 部分Hexo插件推荐

关于node.js和git的安装，直接下载安装即可。

本教程参考如下网站

http://www.jianshu.com/p/985d07d88ef4



### 申请Github账号，并开启Github Page

github账号申请：<https://github.com/>

#### 与Github账号建立连接([git-ssh配置](https://segmentfault.com/a/1190000002645623))

本教程采用git-ssh方式来建立连接，该方式配置完成后可免除输密码的麻烦。同样在Git命令行中配置

1. 设置Git的user name和email：(如果是第一次的话)

   ```markdown
   # 注意以下命令均为单条输入

   ### 双引号中输入Github的账户名
   git config --global user.name "zeyer"

   ### 双引号中输入注册的email地址
   git config --global user.email "zeyer3@outlook.com"
   ```

2. 生成密钥

   ```markdown
   ### 双引号中输入注册的email地址
   ssh-keygen -t rsa -C "zeyer3@outlook.com"
   ```

   连续3个回车，如果不需要密码的话。

   最后得到了两个文件：`id_rsa`和`id_rsa.pub`。

   如果不是第一次，就选择`overwrite`

3. 添加密钥到ssh-agent

   确保 ssh-agent 是可用的。ssh-agent是一种控制用来保存公钥身份验证所使用的私钥的程序，其实ssh-agent就是一个密钥管理器，运行ssh-agent以后，使用ssh-add将私钥交给ssh-agent保管，其他程序需要身份验证的时候可以将验证申请交给ssh-agent来完成整个认证过程。

   ```markdown
   ### 确保ssh-agent可用
   eval "$(ssh-agent -s)"

   ### 添加生成的SSH key 到 ssh-agent，完成后显示文件id_rsa地址
   ssh-add ~/.ssh/id_rsa

   ```

4. 登陆Github,添加ssh

   把`id_rsa.pub`文件里的内容添加到`New SSH key`的key中

5. 测试

   ```markdown
   ssh -T git@github.com
   ```

   将会看到

   ```markdown
   The authenticity of host 'github.com (207.97.227.239)' can't be established.
   RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
   Are you sure you want to continue connecting (yes/no)?
   ```

   选择`yes`

   如果看到`Hi`后面是你的用户名，就说明成功了。


* **扩展补充：**

  修改`.git`文件夹下`config`中的`url`。*（在Hexo中是在_confiy.yml中设置，具体见下文）：*

  修改前

  ```
  [remote "origin"]
      url = https://github.com/zeyer/zeyer.github.io.git
      fetch = +refs/heads/*:refs/remotes/origin/*
  ```

  修改后(将https换成git)

  ```
  [remote "origin"]
      url = git@github.com:zeyer/zeyer.github.io.git
      fetch = +refs/heads/*:refs/remotes/origin/*
  ```

#### 建立Github Page



### 本地搭建Hexo的博客

Node和Git都安装好之后，在本地电脑的某一位置新建文件夹，如在D盘创建blog文件夹，该文件夹主要用于存放Hexo的配置文件以及blog的内容。本教程假设文件夹名为"blog"，路径为`D:\blog`，若无特殊说明，操作均在根目录进行。

* 右键 `Git Bash Here`  （shift+右键 `在此处打开命令窗口`，使用哪种方式取决于安装Git时选择何种方式使用Git命令行），执行如下命令安装Hexo:

  ```markdown
  npm install hexo-cli -g
  ```


* 初始化Hexo

  ```
  hexo init
  ```

​	至此，Hexo安装工作就完成了，博客根目录就是blog。

* 可通过以下代码测试

  ```markdown
  ### 生成静态网页文件
  hexo generate （hexo g 也可以）

  ### 本地启动
  hexo server （hexo s）

  ### 可自定义端口,如5000
  hexo s -p 5000
  ```

### 本地文件发布到Github上

修改Hexo中的_config.yml文件

找到其中的deploy标签，改成如图所示，并保存

```
## 注意有一个空格
deploy:
  type: git
  repository: git@github.com:zeyer/zeyer.github.io.git
  branch: master
```

如果出现github not found错误 ，则在git 命令行中输入如下命令

```markdown
npm install hexo-deployer-git --save
```

再重新运行一遍

```markdown
hexo clean
hexo generate
hexo deploy
```

