

<template>
  <header>
    <img src="./assets/logo.svg" />
    
    <!--new task form-->
    
    <TaskForm />
    <!-- filter -->
    
    <nav>
      <button class="s-Button" @click="filter = 'all' ">All</button>
      <button class="s-Button" @click="filter = 'favs' ">Favs</button>
    </nav>

    <!--task lsits-->

    <div v-if="filter === 'all'">
      <p>You have {{ taskStore.totalCount }} tasks left to do</p>
      <p class="s-Tasks">All tasks</p>
      <div v-for="task in taskStore.tasks">
      <TaskDetails :task="task" />
      </div>
    </div>
    <div v-if="filter === 'favs'">
      <p>You have {{ taskStore.favCount }} favs left to do</p>
      <p class="s-Tasks">Favs tasks</p>
      <div v-for="task in taskStore.favs">
        <TaskDetails :task="task" />
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import { useTaskStore } from './stores/TaskStore'
import  TaskDetails  from './components/TaskDetails.vue'
import  TaskForm from './components/TaskForm.vue'
const taskStore = useTaskStore()

const filter = ref('all');

</script>

<style scoped>
.s-Button{
  width:60px;
  height: 30px;
  margin:10px;
  background-color:rebeccapurple;
  border:none;
  color:white;
  font-size: 14px;
  font-weight: bold;
}
.s-Tasks{
  color:green;
  font-size: 25px;
  border-bottom: 5px solid black;
  padding:10px;
}
</style>
