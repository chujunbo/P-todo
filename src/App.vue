<script setup>
import TodoHeader from './components/TodoHeader.vue'
import TodoMain from './components/TodoMain.vue'
import TodoFooter from './components/TodoFooter.vue'
import { ref } from 'vue'
// 提供数据
// 根据 开发团队 统一风格 ref
// reactive 与 ref 区别
// 作用：都可以作为响应式
// 区别：
  // reactive 仅为 复杂数据类型
  // ref 简单数据类型、复杂数据类型
// 原理：
  // reactive 是对象进行代理
  // ref 是在数据外层包了一次对象，其中 .value 属性就是原本的数据类型，最后再对外进行代理。

const list = ref([
  {
    id: 1,
    name: '吃饭',
    done: true,
  },
  {
    id: 2,
    name: '睡觉',
    done: false,
  },
  {
    id: 3,
    name: '打豆豆',
    done: false,
  },
])
// 勾选
const hChange = (id)=>{
  console.log(id);
 const todo = list.value.find((item) => item.id === id)
 todo.done = !todo.done
}
// 删
const del = (id)=>{
  list.value= list.value.filter((item)=>{item.id !== id})
}
// 增
const addClick = (id)=>{
  list.value.push({
    id:Date.now(),
    name:taskName,
    done:false
  })
}
</script>

<template>
  <section class="todoapp">
    <TodoHeader @add="addClick"></TodoHeader>
    <TodoMain :list="list" @changeSelect="hChange" @unClick="del"></TodoMain>
    <TodoFooter :list="list"></TodoFooter>
  </section>
</template>

<style></style>
