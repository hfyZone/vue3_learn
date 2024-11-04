<template>
  <div class="sandwich">
    <p>一个三明治夹着{{sandwich.bread}},{{sandwich.meat}},{{vegetables}}!</p>
    <button @click="changeSandwich">修改样式！</button>
    <p>三明治的价格为{{price}}</p>
    <button @click="discount">为三明治打折！</button>
  </div>
</template>

<script lang="ts" setup>
import {reactive, toRef, toRefs} from "vue";

let sandwich = reactive({bread:"全麦面包", meat:"鸡肉片", vegetables:"生菜片",price:12});
let {bread, meat, vegetables} = toRefs(sandwich);
function changeSandwich() {
  bread.value="巧克力面包";
  meat.value = "猪肉片";
}
let price = toRef(sandwich, "price");
function discount(){
  price.value=10;
}
</script>

<style>
.sandwich{
  color: blueviolet;
}
</style>