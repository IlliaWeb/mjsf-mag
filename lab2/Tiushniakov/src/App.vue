<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Button from './components/Button.vue';
import SearchableDropdown from './components/SearchableDropdown.vue';
import { ref } from 'vue';

const dropdownItems1 = ref([
  { id: 1, label: 'thing 1', icon: 'https://cdn-icons-png.flaticon.com/128/17128/17128864.png' },
  { id: 2, label: 'thing 2', icon: 'https://cdn-icons-png.flaticon.com/128/17128/17128864.png' },
  { id: 3, label: 'thing 3', icon: 'https://cdn-icons-png.flaticon.com/128/17128/17128864.png' },
]);

const dropdownItems2 = ref([
  { id: 4, label: 'Choice A'},
  { id: 5, label: 'Choice B'},
  { id: 6, label: 'Choice C'},
]);

const selectedItems1 = ref([]);
const selectedItems2 = ref([]);
</script>

<template>
<div class="flex flex-col items-center space-y-4 p-4">

  <!-- Buttons Section -->
  <div class="flex space-x-4">
    <Button label="Hello" size="small" color="pink"></Button>
    <Button label="Hello2" size="large" color="teal" icon="https://cdn-icons-png.flaticon.com/128/17128/17128883.png"></Button>
    <Button label="hello3" size="large" color="gray" icon="https://cdn-icons-png.flaticon.com/128/17128/17128876.png"></Button>
    <Button label="Hello4" size="medium" color="indigo" icon="https://cdn-icons-png.flaticon.com/128/17128/17128895.png"></Button>
  </div>

  <!-- Dropdowns Section -->
  <div class="w-full max-w-md">
    <h2 class="text-lg font-semibold mb-2">Dropdown 1</h2>
    <SearchableDropdown
      :items="dropdownItems1"
      :multiple="true"
      v-model="selectedItems1"
      placeholder="Оберіть варіанти"
    />

    <div class="mt-4">
      <h3 class="text-lg font-semibold">Вибрані елементи 1:</h3>
      <ul class="mt-2 border border-gray-300 rounded-md overflow-hidden">
        <li v-if="selectedItems1.length" v-for="item in selectedItems1" :key="item.id" class="flex items-center p-2 hover:bg-gray-200">
          <img v-if="item.icon" :src="item.icon" alt="" class="w-5 h-5 mr-2" />
          {{ item.label }}
        </li>
        <li v-else class="text-gray-500 p-2">Нічого не вибрано</li>
      </ul>
    </div>

    <h2 class="text-lg font-semibold mt-6 mb-2">Dropdown 2</h2>
    <SearchableDropdown
      :items="dropdownItems2"
      :multiple="false"
      v-model="selectedItems2"
      placeholder="Оберіть інші варіанти"
    />

    <div class="mt-4">
      <h3 class="text-lg font-semibold">Вибрані елементи 2:</h3>
      <ul class="mt-2 border border-gray-300 rounded-md overflow-hidden">
        <li v-if="selectedItems2.length" v-for="item in selectedItems2" :key="item.id" class="flex items-center p-2 hover:bg-gray-200">
          <img v-if="item.icon" :src="item.icon" alt="" class="w-5 h-5 mr-2" />
          {{ item.label }}
        </li>
        <li v-else class="text-gray-500 p-2">Нічого не вибрано</li>
      </ul>
    </div>
  </div>
</div>
</template>

<style scoped>
/* Additional styles if necessary */
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
