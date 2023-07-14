<script setup lang="ts">
    import { transferableAbortSignal } from 'util';
import { ref } from 'vue'

    const Task = ref<Task[]>([
        { name: "hoge", finished: false }
    ])

    const FinisedTasks = ref<Task[]>([])

    const NewTaskName = ref('')

    const AddTask = () => {
        Task.value.push({ name: NewTaskName.value, finished: false })
        NewTaskName.value = ''
    }

    const ChangeStatus = (FinisedTaskName: string) => {
        Tasks.value.map = ((task) => {
            if(task.name === FinisedTaskName) task.finised = true
        })
    }
</script>

<template>
    <div>tasks</div>
    <ul>
        <li v-for="task in Task" :key="task.name">
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
    <div>finised tasks</div>
</template>

<style>
    
</style>