<script setup lang="ts">
import { ref } from 'vue'

const awesome = ref(true)
const inner = ref(false)
</script>
<template>
  <div v-if="awesome">
    <h2>Conditional Example</h2>
    <template v-if="inner">
      <p>Inner content is visible</p>
    </template>
    <template v-else>
      <p>Inner content is hidden</p>
    </template>
  </div>
</template>