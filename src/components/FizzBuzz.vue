<template>
  <div class="w-full max-w-md mx-auto p-6 bg-white rounded-xl shadow-md text-gray-900">
    <h2 class="text-xl font-semibold mb-4">Generador de FizzBuzz</h2>

    <input
      v-model="limit"
      type="number"
      min="1"
      class="border border-gray-300 focus:border-blue-500 focus:ring focus:ring-blue-200 focus:outline-none p-2 rounded w-full mb-4 text-black transition-all duration-300"
      placeholder="Ingresa un número límite"
    />

    <button
      @click="generateFizzBuzz"
      class="w-full px-4 py-2 rounded mb-4 font-semibold
        bg-green-600 hover:bg-green-700 text-white
        transition-colors duration-300 shadow-md
        active:scale-95 cursor-pointer"
    >
      Generar
    </button>

    <ul class="list-disc list-inside text-left space-y-1">
      <li v-for="(item, index) in results" :key="index" class="transition-all duration-300 ease-in-out opacity-0 animate-fadeIn">{{ item }}</li>
    </ul>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

const limit = ref<number>(15);
const results = ref<string[]>([]);

function generateFizzBuzz(): void {
  results.value = [];

  for (let num = 1; num <= limit.value; num++) {
    if (num % 15 === 0) {
      results.value.push(`${num} fizz buzz`);
    } else if (num % 3 === 0) {
      results.value.push(`${num} fizz`);
    } else if (num % 5 === 0) {
      results.value.push(`${num} buzz`);
    } else {
      results.value.push(num.toString());
    }
  }
}
</script>
