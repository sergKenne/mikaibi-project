<template>
  <div class="button">
    <input class="button__input"  :value="item.val" type="radio" name="radio" :id="item.id" @change="handleChange">
    <label class="button__label" :for="item.id">{{ item.val }}</label>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
  const props = defineProps({
    item: Object,
    handleChange: Function
  })
</script>

<style lang="scss" scoped>

</style>