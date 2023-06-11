<script setup lang="ts">
    import { ref } from 'vue'

    interface Item {
        name: string
        price: number
    }

    const items = ref<Item[]>([
        { name: 'egg', price: 100},
        { name: 'apple', price: 160}
    ])

    const newItemName = ref('')
    const newItemPrice = ref(0)

    const addItem = () => {
        items.value.push({ name: newItemName.value, price: newItemPrice.value})
        newItemName.value = ''
        newItemPrice.value = 0
    }
</script>


<template>
    <div>ItemList</div>
    <ul>
        <li v-for="item in items" :key="item.name">
            <div>name: {{ item.name }}</div>
            <div>{{ item.price }} yen</div>
        </li>
    </ul>
    <div>
        <label>
            name
            <input v-model="newItemName" type="text" />
        </label>
        <label>
            price
            <input v-model="newItemPrice" type="number" />
        </label>
        <button @click="addItem">add</button>
    </div>
</template>

<style></style>