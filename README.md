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
#### 3.1.1 响应式`ref()`和`reactive()`
> 项目：  
> [Person.vue](src%2Fcomponents%2FPerson.vue)  
> [Car.vue](src%2Fcomponents%2FCar.vue)

响应式基础数据与对象数组使用ref()定义，使用变量.value修改属性值；  
响应式对象或数组使用reactive()定义，直接访问属性修改，且深度（属性的属性）响应；
#### 3.1.2 解构响应式 `toRefs()`  `toRef()`
> 项目：[Sandwich.vue](src%2Fcomponents%2FSandwich.vue)

`toRefs()`将响应式对象的属性值以结构为响应式变量，访问解构的响应式变量用value修改之；
`toRef()`接受一个对象和对象的值，单独取出此对象的某个属性；

#### 3.1.3 `computed()`计算属性
> 项目：[Name.vue](src%2Fcomponents%2FName.vue)

计算属性所依赖的字段发生变化则自动更新；
与方法的区别：方法会在每次调用都运行，computed会有缓存优化；
计算属性默认为只读，如果需要可修改需要加入 `get()set()`函数，并且set接收一个参数为最新修改值。