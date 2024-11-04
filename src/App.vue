<template>
  <div class="app">
    <h1>CONTENT</h1>
    <Person/>
    <Car/>
    <Sandwich/>
    <Name/>
  </div>
</template>

<script lang="ts">
import Person from "@/components/Person.vue";
import Car from "@/components/Car.vue";
import Sandwich from "@/components/Sandwich.vue";
import Name from "@/components/Name.vue";

export default {
  name: 'App',// 组件的名字
  components:{// 注册vue组件
    Person,
    Car,
    Sandwich,
    Name
  }
}
</script>

<style>
.app {
  color: pink;
}
</style>