<template xmlns="http://www.w3.org/1999/html">
  <div>
    <!--    watch监视基础数据-->
    <button @click="test">考试</button>
    <p>小明的分数为{{ score }}!</p>
    <!--    watch监视对象数据-->
    <hr>
    <button @click="testStudent">给此同学考试！</button>
    <button @click="testZhanghua">换Zhanghua同学考试！</button>
    <p>一个学生的名字为{{ student.name }},他的考试分数为{{ student.score }}.</p>

  </div>
</template>
<!--ClassRoom 里学生的行为被老师监视（watch），当学生行为发生变化时，老师会随之发生变化-->
<script lang="ts" setup>
import {reactive, ref, watch, watchEffect} from 'vue';

// watch监视基础数据
let score = ref(0);

function test() {
  score.value = Math.floor(Math.random() * 100) + 1;
}

// 此处score不需要.ref,watch接收的是一个代理对象
const stopWatch = watch(score, (newV, oldV) => {
  console.log(newV, oldV);
  if (score.value === 100) {
    stopWatch();//watch返回自己的停止方法，在内部使用来停止监视
  }
})

// watch监视对象数据（属性值、引用）
let student = ref({name: "liming", score: 70, family: {daddy: "Joe", mommy: "Jane"}});

function testStudent() {
  student.value.score = Math.floor(Math.random() * 100) + 1;
}

function testZhanghua() {
  //注意此地：如果student使用reactive，此处可以要使用Object.assign({}),这是reactive的局限性;
  //使用ref响应式student，可以正常修改；
  student.value = {name: 'zhanghua', score: 22, family: {daddy: "Smith", mommy: "Lois"}};
}

// reactive默认开启深度监视
watch(student, (newV, oldV) => {
  // 对象监视的新旧值为Proxy(Object)
  console.log(newV, oldV);
}, {deep: true, immediate: true})//watch还有第三个选项，进入官网查看
// 监视的选项deep为true的时候，会在修改属性值的时候也触发newV和oldV都是新的值；
// 默认为false，此时只有引用地址变更的时候会触发。

// 4、监视响应式对象中的某个基本类型属性，使用getter
watch(() => student.value, (newValue, oldValue) => {
  console.log("student已修改", newValue, oldValue);
})
// 如果是监视student.value.family，如果family对象被整体替换，则无法监视
// watch(student.value.family,(newValue,oldValue)=>{
//   console.log("student.family已修改", newValue, oldValue);
// })
// 如果使用函数，推荐，则会监视地址的变化
watch(() => student.value.family, (newValue, oldValue) => {
  console.log("student.family已修改", newValue, oldValue);
})

// 监视多个数据,此时newValue和oldValue为数组。
watch([() => student.value.name, () => student.value.score], (newValue, oldValue) => {
  console.log('监视name和score', newValue, oldValue);
});
let weather = "cloudy";
// watchEffect无需传入监控值，会检测在方法内的所有值的变化而触发watch
watchEffect(()=>{
  if(student.value.name === 'zhanghua'){
    console.log("zhanghua来了");
  }else{
    console.log("不是zhanghua");
  }
  if(weather === "cloudy"){
    console.log('今天是雨天');
  }else{
    console.log('今天不是雨天');
  }
})

</script>

<style>

</style>