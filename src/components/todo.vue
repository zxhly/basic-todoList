<script setup>
import { ref } from 'vue'

const todoList = ref([])
const task = ref()

function addTodo() {
  if (task.value.trim()  != "")
  {
  todoList.value.push(task.value)
  task.value = ""
  }
}

function removeTodo(){
  todoList.value.pop()
}

function removeTodoALL(){
  todoList.value = []
}
</script>



<template>
  <div>
    <input type="text" v-model="task" />
    <button @click="addTodo">Add Todo</button>
    <ul id="check">
      <li v-for="(todo, index) in todoList" :key="index">
        <input type="checkbox">{{ todo }}</input>
      </li>
    </ul>
    <button @click="removeTodo" :hidden="todoList.length === 0">remove last</button>
    <button @click="removeTodoALL" :hidden="todoList.length === 0">remove all</button>
  </div>
</template>

<style scoped>
/* Remove the default bullet points */
#check {
  list-style-type: none;
  padding: 0;
}

#check li {
  margin: 8px 0;
}

</style>