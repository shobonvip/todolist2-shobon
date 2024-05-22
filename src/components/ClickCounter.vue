<script setup lang="ts">
import { ref, computed } from 'vue'

const count = ref<number>(0);
/*
function countMessage(): string {
    return 'Count: ' + count.value;
}
*/
const countMessage = computed(
    () => {
        return 'Count: ' + count.value;
    }
);
//const countMessage = computed(() => 'Count: ' + count.value);
</script>

<template>
    <div>
        <div> {{countMessage}} </div>
        <button @click="count++;"> Click! </button>
        <button @click="count = 0"> Reset! </button>
    </div>
</template>

<style>
</style>