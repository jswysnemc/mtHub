- ## 检测能否连接到aka.ms服务器

  - #### 键盘按win加R打开 运行

  - #### 输入cmd回车打开cmd

  ![1](https://gitee.com/snemc/images/raw/master/img/1.png)

  - #### 输入```ping aka.ms```回车

  - 如果ping失败或者显示来自127.0.01的回复,表示本机的回环地址,也就是没有连接到aka.ms这个域名的服务器,MySQL安装时需要连接这个服务器来下载某些组件,连接不到,自然无法安装成功

![输入aka.ms检测](https://gitee.com/snemc/images/raw/master/img/%E8%BE%93%E5%85%A5aka.ms%E6%A3%80%E6%B5%8B.png)

- ## 查询aka.ms的ip

  - #### 打开百度或者必应,搜索 ip域名查询,

  - #### 选择如图所示的或者类似的工具

  

  ![搜索ip域名查询](https://gitee.com/snemc/images/raw/master/img/%E6%90%9C%E7%B4%A2ip%E5%9F%9F%E5%90%8D%E6%9F%A5%E8%AF%A2.png)

  - #### 打开这个工具后点击DNS查询

  - #### 输入```aka.ms```

  - ![输入aka.ms查询,随便选择一个](https://gitee.com/snemc/images/raw/master/img/%E8%BE%93%E5%85%A5aka.ms%E6%9F%A5%E8%AF%A2,%E9%9A%8F%E4%BE%BF%E9%80%89%E6%8B%A9%E4%B8%80%E4%B8%AA.png)

  - #### 随便选择一个ip地址复制

  - #### 再次打开cmd 输入```ping 加你复制的ip```检测

  - ![再次ping](https://gitee.com/snemc/images/raw/master/img/再次 ping.png)

- ## 修改hosts

  - #### 打开``` C:\Windows\System32\drivers\etc```这个目录

    - 注意进入Winows这个文件夹的时候千万小心,不要删改其他的任何文件,这里是有关系统的

  - ![打开目录,复制hosts](https://gitee.com/snemc/images/raw/master/img/%E6%89%93%E5%BC%80%E7%9B%AE%E5%BD%95,%E5%A4%8D%E5%88%B6hosts.png)

  - #### 把hosts这个文件复制一份作副本(防止出现问题好恢复)

  - #### 图中方法用记事本打开无法,保存,用下面的的方法

  - #### 首先确保打开文件拓展名

    - ![打开文件拓展名](https://gitee.com/snemc/images/raw/master/img/%E6%89%93%E5%BC%80%E6%96%87%E4%BB%B6%E6%8B%93%E5%B1%95%E5%90%8D.png)

  - #### 在桌面右键新建文本文档![新建文本文档](https://gitee.com/snemc/images/raw/master/img/%E6%96%B0%E5%BB%BA%E6%96%87%E6%9C%AC%E6%96%87%E6%A1%A3.png)

  - #### 将文件名全称(包括.txt)改为hosts

  - ![修改为hosts打开](https://gitee.com/snemc/images/raw/master/img/%E4%BF%AE%E6%94%B9%E4%B8%BAhosts%E6%89%93%E5%BC%80.png)

  - #### 输入 ```你复制的IP地址 aka.ms然后保存退出 ```

  - ![输入ip地址空格加域名](https://gitee.com/snemc/images/raw/master/img/%E8%BE%93%E5%85%A5ip%E5%9C%B0%E5%9D%80%E7%A9%BA%E6%A0%BC%E5%8A%A0%E5%9F%9F%E5%90%8D.png)

  - #### 将这个文件放进``` C:\Windows\System32\drivers\etc```替换原来的hosts

  - ![拖拽进来替换](https://gitee.com/snemc/images/raw/master/img/%E6%8B%96%E6%8B%BD%E8%BF%9B%E6%9D%A5,%E6%9B%BF%E6%8D%A2.png)

  - #### 提示需要权限,点击继续

  - #### 再次ping ```aka.ms```

  - ![再次ping检测](https://gitee.com/snemc/images/raw/master/img/%E5%86%8D%E6%AC%A1ping%E6%A3%80%E6%B5%8B.png)

- ## 此时你再安装mysql试一试,记得在安装之,前将之前的安装的mydql卸载干净