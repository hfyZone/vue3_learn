<template>
  <!--  <div id="thisCar">-->
  <!--    <p>这是另一辆车。</p>-->
  <!--  </div>-->
  <div ref="thisCar">
    <p>这是另一辆车。</p>
  </div>
</template>

<script lang="ts" setup>
//使用thisCar做id会在Car中撞车
// console.log(document.getElementById("thisCar"));
import {ref} from 'vue';
let thisCarName = ref("Bench");
let thisCar = ref();
console.log('ref属性的标签：', thisCar);
defineExpose({thisCarName});
</script>

<style>

</style>