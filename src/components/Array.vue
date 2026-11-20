<script setup lang="ts">
import { ref } from 'vue'

const items = ref(['Item 1', 'Item 2', 'Item 3'])
const arrayObject = ref({
  title: 'Array Example',
  author: 'John Doe',
  published: '2024-06-01'
})
</script>

<template>
  <div>
    <h2>Array Example</h2>
    <div>
      <h3>Inline Array</h3>
      <ul>
        <li v-for="(item, index) in items" :key="index">
          <p>{{ item }}</p>
        </li>
      </ul>
    </div>
    <div>
      <h3>Inline Object</h3>
      <ul>
        <li v-for="(value, key) in arrayObject" :key="key">{{ key }}: {{ value }}</li>
      </ul>
    </div>
    <div>
      <h3>Repeat 10 Times</h3>
      <p v-for="n in 10" :key="n">10回繰り返す n:{{ n }}</p>
    </div>
  </div>
</template>

<style>
ul {
  margin-bottom: 1rem;
}
</style>