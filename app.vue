<script setup lang="ts">
const id = ref<number>(0)

const increment = () => id.value++
const decrement = () => id.value--
</script>

<template>
    <button @click="increment">+</button>
    id: {{  id  }}
    <button @click="decrement">-</button>
    <Profile :id="id" />
</template>