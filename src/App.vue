<template>
  <div>
    <div> {{first}} 곱하기 {{second}} 는?</div>
    <input type="number" ref="answer" v-model="enter">
    <button type="submit" @click="onSubmitForm">입력</button>
    <div> {{result}} </div>
  </div>
</template>

<script>
import { ref } from 'vue';
 
export default {
  name: 'App',
  setup() {
    const first = ref(Math.ceil(Math.random() * 9));
    const second = ref(Math.ceil(Math.random() * 9));
    const answer = ref(null)
    let enter = ref('');
    let result = ref('');
  
    const onSubmitForm = (e) => {
      e.preventDefault();
      if(first.value * second.value === enter.value) {
        result.value = '정답';
        first.value = Math.ceil(Math.random() * 9);
        second.value = Math.ceil(Math.random() * 9);
        enter.value = '';
        answer.value.focus();
      } else {
        result.value = '땡';
        enter.value = '';
        answer.value.focus();
      }
      
    }


    return {
      first,
      second,
      enter,
      result,
      answer,
      onSubmitForm,
    }
  }
 
}
</script>

<style>

</style>
