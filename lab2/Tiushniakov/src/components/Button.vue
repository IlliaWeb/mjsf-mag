<template>
  <button
    :class="`font-semibold rounded-lg shadow-lg transition duration-300 ease-in-out transform ${sizeClass} ${colorClass} flex items-center justify-center`" 
    @click="handleClick"
  >
    <span v-if="props.icon" class="mr-2">
      <img :src="props.icon" alt="icon" class="w-5 h-5" />
    </span>
    {{ label }}
  </button>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
  label: String,
  color: {
    type: String,
    default: 'blue'
  },
  size: {
    type: String,
    default: 'medium'
  },
  icon: {
    type: String,
    default: ''
  }
});

// Compute the size class for the button
const sizeClass = computed(() => {
  return {
    small: 'px-3 py-1 text-sm w-24',
    medium: 'px-5 py-2 text-base w-32',
    large: 'px-7 py-3 text-lg w-40'
  }[props.size] || 'px-5 py-2 text-base w-32';
});

// Compute the button color class based on the color prop
const colorClass = computed(() => {
  const colorMap = {
    pink: 'bg-pink-600 text-white hover:bg-pink-700 focus:outline-none focus:ring-2 focus:ring-pink-400',
    orange: 'bg-orange-600 text-white hover:bg-orange-700 focus:outline-none focus:ring-2 focus:ring-orange-400',
    teal: 'bg-teal-600 text-white hover:bg-teal-700 focus:outline-none focus:ring-2 focus:ring-teal-400',
    gray: 'bg-gray-600 text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-400',
    indigo: 'bg-indigo-600 text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-400',
   
    // Add more colors as needed
  };
  return colorMap[props.color] || 'bg-blue-600 text-white hover:bg-blue-700'; // Default color
});

const handleClick = (event) => {
  console.log("Button clicked!", event);
};
</script>

<style scoped>
/* Optional: You can add some additional styles if necessary */
button:focus {
  outline: none; /* Remove default focus outline */
}
</style>
