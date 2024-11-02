# vue3_learn
## 1 vite启动项目
### 1.1 安装nvm
使用nvm安装npm防止出现mac的权限问题。  
> 参考：https://nvm.p6p.net/install/mac.html

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash`
`source ~/.zprofile`
### 1.2 安装npm  
安装最新的nodejs
`nvm install node`
### 1.3 安装vite
`npm create vue@latest`  
如果出现没有反应的情况，设置代理：  
`npm config set proxy http://localhost:7897`  
vite会询问项目初始化信息并建立项目，然后安装依赖：  
`npm install`
### 1.4 运行项目
[package.json](vue-project%2Fpackage.json)里存储了启动方式，[index.html](vue-project%2Findex.html)为初始化页面