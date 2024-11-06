<template>
  <div class="app">
    <h1>CONTENT</h1>
    <Person/>
    <Car/>
    <Sandwich/>
    <Name/>
    <ClassRoom></ClassRoom>
    <AnotherCar ref="anotherCar"></AnotherCar>
    <button @click="testCar">测试车</button>
  </div>
</template>

<script lang="ts" setup>
import Person from "@/components/Person.vue";
import Car from "@/components/Car.vue";
import Sandwich from "@/components/Sandwich.vue";
import Name from "@/components/Name.vue";
import ClassRoom from "@/components/ClassRoom.vue";
import AnotherCar from "@/components/AnotherCar.vue"

import {ref} from "vue";

let anotherCar = ref();//这个首先执行与点击事件执行的一样
// testCar();直接运行会崩溃掉，因为此时thisCarName是不存在的，实际上整个anotherCar的对象都与下边的不同
function testCar() {
  console.log('这个是父组件Vue读取子组件AnotherCar', anotherCar.value.thisCarName);
}

</script>
<!--以下是vue2的写法-->
<!--<script lang="ts">-->
<!--import Person from "@/components/Person.vue";-->
<!--import Car from "@/components/Car.vue";-->
<!--import Sandwich from "@/components/Sandwich.vue";-->
<!--import Name from "@/components/Name.vue";-->
<!--import ClassRoom from "@/components/ClassRoom.vue";-->

<!--export default {-->
<!--  name: 'App',// 组件的名字-->
<!--  components:{-->
<!--    ClassRoom,-->
<!--// 注册vue组件-->
<!--    Person,-->
<!--    Car,-->
<!--    Sandwich,-->
<!--    Name-->
<!--  }-->
<!--}-->
<!--</script>-->

<style>
body {
  background: lightslategray;
}

.app {
  color: pink;
}

.app div {
  background: white;
  margin: 10px 0;
  box-shadow: 10px 5px 5px black;
  padding: 10px 10px;
}
</style>