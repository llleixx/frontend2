<script setup>
const props = defineProps({
  change: {
    required: true,
    type: Function
  }
});
</script>

<template>
  <button type="button" @click="props.change()">
    <slot></slot>
  </button>
</template>

<style lang="scss" scoped>
$very-dark-violet: hsl(278, 68%, 11%);

button {
  box-sizing: border-box;
  display: inline-block;
  width: 100%;
  font-size: 18px;
  border-radius: 10px;
  height: 3em;
  color: white;
  background-color: $very-dark-violet;
}
</style>