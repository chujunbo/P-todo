<script setup>
  import {ref} from 'vue'
  const taskName = ref('')
  const emit =defineEmits(['add'])
  const keyDown = ()=>{
    console.log(123);
    if(taskName.value.length===0)return
    emit('add',taskName.value)
    taskName.value = ''
  }

</script>
<template>
  <header class="header">
    <h1>todos</h1>
    <input
    class="new-todo"
    placeholder="What needs to be done?"
    autofocus
    @keydown.enter="keyDown"
    v-model.trim ="taskName"/>
  </header>
</template>

<style lang="less" scoped></style>
