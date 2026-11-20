/**
 * BindClass.vue
 * Example of binding classes dynamically in Vue 3
 * Class binding example
 */
<script setup lang="ts">
import { ref, reactive, computed } from 'vue';

const isActive = ref(true);
const hasError = ref(false);

const toggleClass = () => {
    isActive.value = !isActive.value;
    hasError.value = !hasError.value;
};

// class オブジェクト作成
const classObject = reactive({
    active: isActive,
    'has-error': hasError
});
// computed によるクラスオブジェクト作成
const error = ref<{ type: string } | null>({ type: 'fatal' });
const computedClassObject = computed(() => ({
    active: isActive.value && !error.value,
    'has-error': error.value && error.value.type === 'fatal'
}));
// class を配列でバインド
const activeClass = ref('active');
const errorClass = ref('text-danger');
</script>

<template>
  <div>
    <h2>Bind Class Examples</h2>
    <div class="toggle" :class="{ active: isActive, 'has-error': hasError }" @click="toggleClass">
        Bind Class Example
    </div>
    <div class="toggle" :class="classObject" @click="toggleClass">
        Bind Class Example with classObject
    </div>
    <div :class="computedClassObject">
        Bind Class Example with computedClassObject
    </div>
    <div :class="[activeClass, errorClass]">
        Bind Class Example with classArray
    </div>
    <div :class="[isActive ? activeClass : errorClass ]">
        Bind Class Example with conditional class array
    </div>
  </div>
</template>

<style>
.toggle {
    cursor: pointer;
}
.active {
    color: green;
}
.has-error {
    color: red;
}
.text-danger {
    color: orange;
}
</style>