<template>
  <div class="car" id="thisCar">
    <p>一辆{{car.brand}}牌子的车，价值{{car.price}}万元</p>
    <button @click="bargain">砍价！</button>
  </div>
</template>

<script lang="ts" setup>
import {reactive} from "vue";

let car = reactive({brand: 'TSL', price: 20});// 响应式对象（数组）
function bargain() {
  car.price = 18;// 响应式对象访问属性直接访问
}
</script>

<style>
.car {
  color: green;
}
</style>