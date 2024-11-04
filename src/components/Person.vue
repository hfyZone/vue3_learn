<template>
  <div class="person">
    <p>我的名字是{{ name }}</p>
    <button @click="showInfo">点击显示信息</button>
    <p @click="changeCounter">点击计数器：{{counter}}</p>
  </div>
</template>

<!-- <script lang="ts">-->
<!--export default {-->
<!--  name: 'Person',-->
<!--  setup() {-->
<!--    let name = "韩飞洋";-->
<!--    let myInfo = "我在地球居住";-->
<!--    function showInfo() {-->
<!--      alert(myInfo);-->
<!--    }-->
<!--    return {name, showInfo}-->
<!--  }-->
<!--}-->
<!--</script>-->

<!--setup语法糖写法：-->
<!--<script lang="ts">-->
<!--export default {-->
<!--  name:"Person"-->
<!--}-->
<!--</script>-->
<!--上下两处必须保持语言类型一致，切内容不可合并-->
<script lang="ts" setup>
import {ref} from 'vue';

let name = "韩飞洋";
let myInfo = "我在地球居住";
let counter = ref(0);//ref包裹的数据为响应式
function showInfo() {
  alert(myInfo);
}
function changeCounter() {
  counter.value ++;// 通过.value访问ref包裹的响应式数据
}
</script>

<style>
.person {
  color: blue;
}
</style>