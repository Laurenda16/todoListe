<template>
  <h1>Planification des taches</h1>
<form action="" @submit.prevent="ajouterTache">
  <fieldset role="group">
  <input type="text" placeholder="Tache a Effectuer" v-model="todo">
  <button>AjouterTache</button>

</fieldset>
</form>


  <div v-if="todos.length==0">Vous n'avez aucune tache a faire</div>
  

</template>

<script setup>
import { ref } from 'vue';

const variable = ref();
const todos=ref([])
const todo= ref('');
const ajouterTache=()=>
{
  //recupere la tache saisi
  todos.value.push(
    {
      title:todo.value,
      completed: false,
      date:Date.now()
    }
  )
}



</script>

<style>
</style>