<template>
  <h1>Planification des taches</h1>
<form action="" @submit.prevent="ajouterTache">
  <fieldset role="group">
  <input type="text" placeholder="Tache a Effectuer" v-model="newTodo">
  <button :disabled="newTodo.length==0">Ajouter</button>

</fieldset>
</form>


  <div v-if="todos.length==0">Vous n'avez aucune tache a faire</div>
<div v-else>
  <ul>
    <li v-for="todo of sortedTodo()" :key="todo.date" :class ="{completed: todo.completed}">
      <label>
        <input type="checkbox" v-model="todo.completed">   {{ todo.title }}
      </label>
     
    </li>
    
    
  </ul>
  <div>
    <label for="">
      <input type="checkbox" name="" id="" v-model="hideCompleted">masquer les taches completes
    </label>
  </div>

</div>

</template>

<script setup>
import { ref } from 'vue';

const variable = ref();
const todos=ref([
 {
  title:'Faux ajouter les taches a faire',
      completed: true,
      date:1

 }
])
const newTodo= ref('');
const hideCompleted=ref(false)
const ajouterTache=()=>
{
  //recupere la tache saisi
  todos.value.push(
    {
      title:newTodo.value,
      completed: false,
      date:Date.now()
    }
  )
  newTodo.value='';
}

const sortedTodo=()=>
{
const sortedTodos= todos.value.toSorted((a,b)=> a.completed>b.completed?1:-1)

if(hideCompleted.value === true)
{
return sortedTodos.filter(t=> t.completed === false)
}
return sortedTodos;
}



</script>

<style>
.completed
{
  opacity: .5;
  text-decoration: line-through;
}
</style>
