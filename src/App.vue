<template>
  <div class="app">
    <h1>CONTENT</h1>
    <Person/>
  </div>
</template>

<script lang="ts">
import Person from "@/components/Person.vue";

export default {
  name: 'App',// 组件的名字
  components:{// 注册vue组件
    Person
  }
}
</script>

<style>
.app {
  color: pink;
}
</style>