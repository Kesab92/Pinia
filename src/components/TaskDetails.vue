<template>
    <div class="s-Task__header" >
        <h3 >{{ task.title }}</h3>
        <div>
            <i class="fa-solid fa-trash" @click="taskStore.deleteTask(task.id)"></i>
            <i class="fa-solid fa-heart" @click="taskStore.toggleFav(task.id)"></i>
        </div>
    </div>
</template>

<script setup>
import { useTaskStore } from '../stores/TaskStore';
    const props = defineProps({
        task: Object
    })
    const taskStore = useTaskStore()


</script>
<style scoped>
    .s-Task__header{
        display:flex;
        justify-content: space-between;
        gap:10px;
        height:40px;
        width:100%;
        margin-top:10px;
        padding:5px;
        border:2px solid #888888;
        box-shadow: 1px 2px #888888;
    }
</style>