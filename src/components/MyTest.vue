<script setup lang="ts">
import { ref, reactive, computed } from "vue";

const author = reactive({
  name: "John",
  books: ["Book 1", "Book 2"],
});

const bookCount = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No';
});

const currentTime = ref<Date>(new Date());

const now = computed(() => {
  setTimeout(() => {
    currentTime.value = new Date();
  }, 1000);

  return new Intl.DateTimeFormat('ja-JP', {
    timeZone: 'Asia/Tokyo',
    hour: '2-digit',
    minute: '2-digit',
    second: '2-digit'
  }) .format(currentTime.value);
});
console.log(now.value);
</script>

<template>
    <p>Has published books?</p>
    <span>{{ bookCount }}</span>
    <p>Current time:</p>
    <span class="now-time">{{ now }}</span>
</template>

<style scoped>
p {
  font-weight: bold;
}
.now-time {
  font-weight: bold;
  font-size: 3.2em;
  color: #fff30a;
}
</style>
