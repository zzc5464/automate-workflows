# 构建前端自动化工作流环境
- 前端工作有太多重复的动作,通过nodeJS以及它带来的一些工具进行简化操作
- 搭建一个自己的自动化工作流环境；
  + 自动编译  比如less/sass
  + 自动合并  比如js
  + 自动刷新  比如测试不同浏览器中项目的效果
  + 自动部署  
  ## 为什么要有自动化的流程

- 在我们的开发过程中有大量的重复操作
- DRY  Don't repeat yourself
- 开发人员的精力应放在哪？创造，新的一切
- 前端开发的编译操作
## 1.Node环境

### 1.1.什么是Node

- 不是JS文件，也不是一个JS框架（）
- 而是Server side Javascript runtime, 服务端的一个JS运行时
- 我们可以在NODE运行JS代码
- 但一些浏览器个api就无法使用如:alert();
- node中只能运行ECMAScript，无法使用 BOM 和 DOM
- 目前我们的JS是运行在浏览器内核中
- 就像php要运行在php环境,java要运行在jdk;
### 1.2.Node环境搭建
#### 1.2.1.Mac

- 安装包的方式
  + [pkg](https://nodejs.org/dist/v5.5.0/node-v5.5.0.pkg)
- NVM（Node Version Manager）

  ```bash
  $ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.30.2/install.sh | bash
  $ echo '. ~/.nvm/nvm.sh' >> .bash_profile
  $ nvm install stable
  $ nvm alias default stable
  ```

#### 1.2.2.Windows

- 官方下载
 + https://nodejs.org/en/download/
- 因为NODE版本比较多，开发人员可能依赖很多版本
 + nvm(node version manager)
- 通过NVM，可以轻松切换于不同的版本之间

  ```command
  
  ```
  
#### 配置nvm
- 下载nvm
 + https://www.npmjs.com/package/nvm
 + 安装包放到纯英文路径
 + 把你所需要用到的node版本下载安装到nvm同级文件夹(v4.x v5.x v6.x)
 + 我的路径 C:\Develop
 + 打开setting.txt(如果没有就新建)

        root: C:\Develop\nvm     你nvm安装的路径
        path: C:\Develop\nodejs  node的快捷方式路径
        arch: 64                 你的操作系统
        proxy: none              先不管就none吧
         

- 如果你的路径和我一样,复制黏贴.
- 在nvm目录下打开命令行(shift+右键),输入nvm查看版本信息
 + nvm use 6.x 可以切换node版本  如果你是32位要在版本后面加上(空格)32
- 如果以上可以一步到位,那恭喜你很幸运接下来一小段可以略过了.
#### 配置失败
> 首先,setting没有咋办?
- 双击install.cmd文件,在代码最后复制nvm的安装路径.
- 会跳出setting.txt. 同上,把root和path写上保存
- 保存不见了咋办?直接新建吧骚年..
- 到这里基本能看版本信息了,这时候回上一层目录看一下nodejs快捷方式有没有出来.

> 没有nodejs快捷方式,那就要配置环境变量了
- 打开环境变量,找到系统变量把之前配置的NVM开通的HOME和SYMLINK删掉
- 到用户变量新建两个变量NVM_HOME对应的路径是nvm安装路径和NVM_SYMLINK对应的是nodejs路径
- 然后打开path变量(没有就新建),把变量名加进去.完成
>> NVM_HOME=C:\Develop\nvm

>> NVM_SYMLINK=C:\Develop\nodejs

>> PATH=%NVM_HOME%;%NVM_SYMLINK%;%NPM_HOME%

#### 1.2.3.环境变量说明
- 环境变量就是操作系统提供的系统级别用于存储变量的地方
- 系统变量和用户变量
- 系统变量指的是所用当前系统用户共享的变量
- 自己的电脑一般只有一个用户
- 建议将自己配置的环境变量放在用户变量中，用户变量比较干净
- 环境变量的变量名是不区分大小写的
- 变量间运行相互引用
- 特殊值：
- PATH变量（不区分大小写）
- PATH 相当于一个路径的引用
- 只要添加到PATH变量中的路径，都可以在任何目录下搜索
- 命令行
- 可以用来执行当前目录下的文件
- 命令
 + cd :change directory
 + 具体可以百度cmd命令..
- Node.js是一个轻内核（本身没有什么功能）的东东，所有的功能都要功能包提供
- node官方提供了一些最基础的包
- 至此完成nvm安装
### 1.3.Node用途

#### REPL环境（控制台环境）

#### 1.3.1.开发Web应用程序

- 做动态网站
- 开发提供数据的服务端API

#### 1.3.2.前端开发工具基础
- Node.js给前端乃至整个开发行业带来一场工业革命
### 1.4.Node开发Web应用Demo
详见nodeJSdemo.js
#### ps
客户端发送到服务端的东西称之为请求报文
服务端返回给客户端的东西称之为响应报文
