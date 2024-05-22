<script setup lang="ts">
import {ref} from 'vue'

interface Item {
    name: string,
    price: number,
    description?: string
}

const items = ref<Item[]>([
    {name:"Egg", price:100},
    {name:"Apple", price:160},
]);

const newItemName = ref('');
const newItemPrice = ref(0);

function addItem() {
    items.value.push({
        name: newItemName.value,
        price: newItemPrice.value
    });
}

</script>

<template>
    <div>
        <div>ItemList</div>
        <ul>
            <li
            v-for="item in items"
            :key="item.name"
            :class="{
                over1000: item.price >= 1000,
                over500: item.price >= 500 && item.price < 1000
            }"
            >
                <div> Name: {{ item.name }} </div>
                <div> {{ item.price }} Yen. </div>
                <div v-if="item.price >= 1000">
                    Expensive
                </div>
            </li>  
        </ul>
        <div>
            <label>
                Name:
                <input v-model="newItemName" type="text" />
            </label>
            <label>
                Price:
                <input v-model="newItemPrice" type="number" />
            </label>
            <button @click="addItem"> Add </button>
        </div>
    </div>
</template>

<style>
.over500 {
    color: red;
}
.over1000 {
    color: blue;
}
</style>