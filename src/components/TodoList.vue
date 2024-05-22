<script setup lang="ts">

import { ref, computed } from 'vue'

interface Task {
    name: string
    state: number
};

const tasks = ref<Task[]>([
    {name: "Egg", state: 0},
]);

const not_completed_tasks = computed(() => tasks.value.filter(
    (task) => task.state === 0
));

const completed_tasks = computed(() => tasks.value.filter(
    (task) => task.state === 1
));
const inputTask = ref<string>("");

const addTask = () => {
    tasks.value.push({
        name: inputTask.value,
        state: 0
    });
    inputTask.value = "";
};

const changeState = (task: Task) => {
    task.state ^= 1;
    return;
};

</script>

<template>
<div>
    <div> Todo List </div>

    <h2> Not Completed </h2>
    <ul>
        <li
            v-for="task in not_completed_tasks"
            :key="task.name"
        >
            <div>
                Task: {{task.name}}
            </div>
            <button @click="changeState(task)"> COMPLETE! </button>
        </li>
    </ul>

    <label>
        Task: 
        <input v-model="inputTask" type="text" /> 
    </label>

    <button @click="addTask">Add</button>

    <h2> Completed </h2>
    <ul>
        <li
            v-for="task in completed_tasks"
            :key="task.name"
        >
            <div>
                Task: {{task.name}}
            </div>
            <button @click="changeState(task)"> return to list </button>
        </li>
    </ul>

</div>
</template>

<style>

</style>