/**
 * MyTest2.vue
 * 「書き込み可能な」算出プロパティ
 */

<script setup lang="ts">
import { ref, computed } from "vue";

const firstName = ref<string>("John");
const lastName = ref<string>("Doe");

const fullName = computed({
    // getter関数ではリアクティブなプロパティを更新せず、値を返すだけにする
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
