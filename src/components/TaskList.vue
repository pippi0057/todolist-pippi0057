<script setup lang="ts">
    import { computed, ref } from 'vue';
    
    interface Task {
        name: string
        finished: boolean
    }

    const Tasks = ref<Task[]>([]);

    const FinisedTasks = computed(() => Tasks.value.filter((task) => task.finished));
    const NotFinishedTasks = computed(() => Tasks.value.filter((task) => !task.finished));

    const NewTaskName = ref('')

    const AddTask = () => {
        Tasks.value.push({ name: NewTaskName.value, finished: false });
        NewTaskName.value = '';
    }

    const ChangeStatus = (FinisedTaskName: string) => {
        Tasks.value.map((task) => {
            if(task.name === FinisedTaskName) task.finished = true;
        });
    }
</script>

<template>
    <h3>tasks</h3>
    <ul>
        <li v-for="task in NotFinishedTasks" :key="task.name">
            <div>name: {{ task.name }}</div>
            <button @click="ChangeStatus(task.name)">complete</button>
        </li>
    </ul>
    <h3>finised tasks</h3>
    <ul>
        <li v-for="task in FinisedTasks" :key="task.name">
            <div>name: {{ task.name }}</div>
        </li>
    </ul>
    <div>
        <label>
            task name
            <input v-model="NewTaskName" type="text"/>
        </label>
        <button @click="AddTask">add</button>
    </div>
</template>

<style>
    
</style>