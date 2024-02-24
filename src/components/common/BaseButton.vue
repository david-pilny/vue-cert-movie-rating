<template>
  <button class="button"><slot /></button>
</template>

<style scoped>
@tailwind base;
@tailwind components;
@tailwind utilities;

.button {
  @apply font-bold py-2 px-4 rounded;
}
</style>
