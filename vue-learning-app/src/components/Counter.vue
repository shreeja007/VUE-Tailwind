<template>
    <div class="counter">
        <h1>{{ target }}</h1>
        <h2>
            Count: {{ count }}
        </h2>
        <button @click="decrement"> - </button>
        <button @click="increment"> + </button>
        <button @click="reset"> Reset </button>

    </div>
</template>
<script setup>
import { ref, computed } from 'vue'

const count = ref(0)

function increment() {
    count.value++
}
function decrement() {
    if (count.value >= 1) {
        count.value--
    }
}
function reset() {
    count.value = 0
}

const target = computed(() => count.value === 10 ? "You've reached 10!" : '');
</script>

<style scoped>
.counter {
    text-align: center;
}

button {
    margin: 0 10px;
    padding: 5px 10px;
}
</style>