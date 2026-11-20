<script setup lang="ts">
import { ref, reactive } from 'vue';

const activeColor = ref('red');
const fontSize = ref(30);

// style オブジェクトを作成
const styleObject = reactive({ // ref() でも同様にリアクティブにできる
  color: 'green',
  fontSize: '20px'
});
</script>

<template>
  <div>
    <h2>Bind Style Example</h2>
    <p :style="{ 'font-size': fontSize + 'px' }">Styled Text fontSize</p>
    <p :style="styleObject">Styled Text styleObject
      <span :style="{ color: activeColor }"> {{ styleObject.color }}</span>
    </p>
    <h2 style="color: orange;" :style="'font-size: 1em'">with the standard writing style, and</h2>
  </div>

</template>
