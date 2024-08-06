<template>
  <div class="flex border boxizing">
    <h1 class="">My Todos   !!</h1>
    <FormComponent @sendTaskName="getTaskName" />
    <TodoList :getAllToDo="toDos" />
  </div>
</template>

<script setup lang="ts">
// import { type } from 'os';
import FormComponent from './FormComponent.vue'
import TodoList from './TodoListComponent.vue'
import { nanoid } from 'nanoid'
import { ref } from 'vue'
import { Todo } from '../types'

const toDos = ref<Todo[]>([
  { id: nanoid(), text: 'courir', isDone: true },
  { id: nanoid(), text: 'Danser', isDone: true },
  { id: nanoid(), text: 'Nager', isDone: true }
])

function getTaskName(taskName: string): void {
  console.log(taskName)
  const newTodo: Todo = {
    id: nanoid(),
    text: taskName,
    isDone: false
  }
  toDos.value.push(newTodo)
  
  console.log('receive')
}

// const toDos =ref<Array<Todo>>([])
</script>

<style scoped>
.flex {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 15px;
  padding-inline: 5rem;
}
/* h1{
  font-size: 45px;
} */
.border {
  border: 2px solid red;
  border-radius: 20px;
}

.boxizing {
  padding-block: 20px;
  width: 15rem;
  margin: 0 auto;
}
</style>