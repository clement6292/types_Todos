<template>
  <div>
    <ul>
      <li v-for="(todo, index) in getAllToDo" :key="index">
        <input type="checkbox" />
        <span>{{ todo.text }}</span>
        <!-- <span>{{todo.isDone?"Traitée":"Non traitée"}}</span> -->
        <span class="sup" @click="remove(index)"> X </span>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { Todo } from '../types'

const props = defineProps<{
  getAllToDo: Todo[]
}>()
console.log(props.getAllToDo)

const todoList = ref<Array<Todo>>([...props.getAllToDo])
function remove(index:number):void{
    
   props.getAllToDo.splice(index, 1)
       

    
}
</script>

<style scoped>
.sup {
  padding: 5px;
  border: 2px solid;
  cursor: pointer;
  color: white;
  background-color: rgb(21, 19, 19);
  border-radius: 50%;
  margin-inline: 20px;
}
li{
    list-style: none;
    margin-block: 10px;
    display: flex;
    justify-content: center;
    align-content: center;
    
}
</style>