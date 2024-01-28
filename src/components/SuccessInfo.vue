<script setup>
import mybutton from './Button.vue'
const props = defineProps({
  change: {
    required: true,
    type: Function
  }
});
</script>

<template>
  <div class="success-info">
    <div class="image-wrapper">
      <img src="../assets/icon-complete.svg" width="60px" height="60px" alt="success" />
    </div>
    <p class="info-1">THANK YOU!</p>
    <p class="info-2">We've added your card details</p>
    <mybutton :change="change">Continue</mybutton>
  </div>
</template>

<style lang="scss" scoped>
$dark-grayish-violet: hsl(279, 6%, 55%);

img {
  display: block;
  margin: 0 auto;
}

.info-1 {
  text-align: center;
  font-size: 1.5em;
  margin-top: 20px;
  letter-spacing: 3px;
}

.info-2 {
  text-align: center;
  color: $dark-grayish-violet;
  margin-top: 15px;
  margin-bottom: 30px;
}
</style>
