/**
 * MyTest2.vue
 * 「書き込み可能な」算出プロパティ
 */

<script setup lang="ts">
import { ref, computed } from "vue";

const firstName = ref<string>("John");
const lastName = ref<string>("Doe");

    // TODO: input で文字を入力するたびにスペースが挿入される問題を解決する必要がある
const fullName = computed({
  get() {
    return [firstName.value, lastName.value].filter(Boolean).join(" ");
  },
  set(newValue) {
    const separatorIndex = newValue.indexOf(" ");

    if (separatorIndex === -1) {
      firstName.value = newValue;
      lastName.value = "";
      return;
    }

    firstName.value = newValue.slice(0, separatorIndex);
    lastName.value = newValue.slice(separatorIndex + 1);
  },
});
</script>

<template>
  <div>
    <p>Full Name: {{ fullName }}</p>
    <input v-model="fullName" placeholder="Full Name" />
    <p>firstName: {{ firstName }}</p>
    <p>lastName: {{ lastName }}</p>
  </div>
</template>
