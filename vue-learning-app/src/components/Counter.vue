<template>
    <div class="counter">
        <div class="progress" :style="{ width: count * 10 + '%'}"></div>
        <h1  style="margin: 50px; border: 1px solid red;" v-if="target">{{ target }}</h1>
        <h2>
            Count: {{ count }}
        </h2>
        <button @click="decrement" :disabled="count === 0"> - </button>
        <button @click="increment" :disabled="count === 10"> + </button>
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

button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
}

.progress{
    border: 1px solid red;
}
</style>