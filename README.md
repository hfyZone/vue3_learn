# vue3_learn
## 1 vite启动项目
### 1.1 安装nvm
使用nvm安装nodejs防止出现mac的权限问题。  
> 参考：https://nvm.p6p.net/install/mac.html
```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
```
```sh
source ~/.zprofile
```
### 1.2 安装nodejs  
安装最新的nodejs
```sh
nvm install node
```
### 1.3 安装vite
```sh
`npm create vue@latest`
```
如果出现没有反应的情况，设置代理： 
```sh
npm config set proxy http://localhost:7897
```
vite会询问项目初始化信息并建立项目，然后安装依赖： 
```sh
npm install
```
### 1.4 运行项目
[package.json](vue-project%2Fpackage.json)里存储了启动方式，[index.html](vue-project%2Findex.html)为初始化页面

## 2 项目结构
App.vue文件是vue组件根文件，
main.ts是？？
自己构建组件后，在App.vue中引入，注册组件
vue2使用选项式API，vue3新增了组合式API，组合式API将同种类的各种选项集合在一个方法里，降低了代码耦合度；
## 3 APP.vue
### 3.1 `<setup>`标签
