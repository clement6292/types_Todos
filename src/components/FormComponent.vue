<template>
  <input type="text" v-model="newtask" 
  placeholder=" Ajouter une nouvelle tâche"
  @keydown.enter="submitTask"
   />
</template>

<script setup lang="ts">
import { ref } from 'vue'
const newtask = ref<string>('')
// const emit = defineEmits(['sendTask'])
const emit = defineEmits<{
    (e:"sendTaskName" , value:string):void
}>()

function submitTask (e:Event):void{
    if (newtask.value.trim()!=="") {
        emit('sendTaskName',newtask.value)       
    }
    newtask.value = "" ;
    console.log("donnée envoyer")
}

</script>

<style scoped>
input {
  padding: 10px;
  font-size: 1.5rem;
}
</style>