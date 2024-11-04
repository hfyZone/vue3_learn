<template>
  <div>
    <label>
      FirstName: <input v-model="firstName">
      LastName: <input v-model="lastName">
    </label>
    <p>Your name is {{ fullName }};</p>
    <p>Your nick name is {{ nickName }}</p>
    <button @click="changeNickName">修改别名</button>
  </div>
</template>

<script lang="ts" setup>
import {computed, ref} from "vue";

let firstName = ref('Default');
let lastName = ref('Default');
// 计算属性（只读）
let fullName = computed(() => {
  return firstName.value + " " + lastName.value;
});
//计算属性（可修改）

let nickName = computed({
  get() {
    return lastName.value + firstName.value;
  },
  set(val) {
    firstName.value = "212";
    lastName.value = "3223"
  }
});

function changeNickName() {
  nickName.value = "2";
}
</script>

<style>

</style>