<script setup lang="ts">
import { ref, computed } from "vue";


const firstName = ref<string>("John");
const lastName = ref<string>("Doe");

const fullName = computed({
  get() {
    return firstName.value + " " + lastName.value;
  },
  set(newValue) {
    const [first = "", last = ""] = newValue.split(" ");
    firstName.value = first;
    lastName.value = last;
  },
});
</script>

<template>
  <div>
    <p>Full Name: {{ fullName }}</p>
    <input v-model="fullName" placeholder="Full Name" />
  </div>
</template>