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
npm create vue@latest
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
> [Person.vue](src%2Fcomponents%2FPerson.vue)，
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

#### 3.1.4 `watch` 
> 项目：[ClassRoom.vue](src%2Fcomponents%2FClassRoom.vue)

`watch`可监视的数据：
- ref定义的数据
- reactive定义的数据
- 函数返回值getter
- 包含上述内容的数组

> Regarding 1) You can't replace reference to reactive state like that, it's explained here https://vuejs.org/guide/essentials/reactivity-fundamentals.html#limitations-of-reactive If you want to update reactive state with a new object, use Object.assign(student, newState). Other solution is using ref. The choice is yours which one you want to use  
> Regarding 2) it works as expected. The  changeToBrain() function will always trigger the callback because you're assigning a new object. In changeSalary(), you only update the salary property, but the tracked object itself hasn't changed. That's why the watcher callback is not triggered unless you explicitly enable deep property tracking.  
> _FROM https://github.com/vuejs/core/issues/12333_

**watchEffect**
不用传入监控值，自动监控方法里涉及到的所有参数

#### 3.1.5 模板中的`ref`
> 项目：[AnotherCar.vue](src%2Fcomponents%2FAnotherCar.vue)

在`<template>`中的标签中使用ref，可以避免不同vue文件中的id冲突。
```html
<h2 ref="title">HELLO</h2>
```
如果开启了局部样式即`<style scoped>`，并且模板中带有ref属性的标签，
会在渲染标签中加上data-v-XXXXXX.
#### 3.1.6 `defineExpose`
> 项目：[AnotherCar.vue](src%2Fcomponents%2FAnotherCar.vue)、
> [App.vue](src%2FApp.vue)

子组件可以将要暴露的属性传入`defineExpose`来暴露给父组件使用。

