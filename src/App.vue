<template>
  <div class="w-screen h-screen flex">
    <div class="flex-1">
      <div>
        <textarea v-model="leftText" placeholder="place input your text" name="" id="" cols="30" rows="10" ></textarea>
      </div>
      <button @click="onClickTrans">trans</button>
    </div>
    <div class="flex-1">
      <div>
        <textarea :value="rightText" placeholder="place input your text on left" name="" id="targetForCopy" cols="30" rows="10"></textarea>
      </div>
      <button @click="onClickCopy">copy</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const leftText = ref('');
const rightText = ref('');
function onClickTrans() {
  if (leftText.value === '') {
    alert('please input your text for trans');
    return;
  }
  console.log('trans');
  rightText.value = leftText.value.replace(/\n/g, ',');
}
function onClickCopy() {
  const textarea = document.querySelector('#targetForCopy');
  textarea.select();
  document.execCommand('copy');
  console.log('copied');
  alert('copied');
}
</script>

