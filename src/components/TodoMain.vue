<script setup>
  // 接收数据
  defineProps({
    list:{
      type:Array,
      required:true
    }
  })
  // 子传父
  const emit = defineEmits(['changeSelect','unClick'])
  const changeSelect = (id)=>{
    // 传勾
    console.log("changeSelect",id);
    emit('changeSelect',id)
  }
</script>

<template>
  <section class="main">
    <input id="toggle-all" class="toggle-all" type="checkbox" />
    <label for="toggle-all">Mark all as complete</label>
    <ul class="todo-list">
      <li class="completed" v-for="item in list" :key="item.id">
        <div class="view">
          <input class="toggle" type="checkbox" :checked="item.done" @change="changeSelect(item.id)"/>
          <label>{{item.name}}</label>
          <button class="destroy" @click="emit('unClick',item.id)"></button>
        </div>
        <input class="edit" value="Create a TodoMVC template" />
      </li>
    </ul>
  </section>
</template>

<style lang="less" scoped></style>
