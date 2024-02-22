<template>
  <div class="modal">
    <div class="container">
      <div class="modal__inner">
        <button class="modal__close" @click="emit('hideModal')">
          <img src="../assets/img/close_btn.png" alt="bulb">
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
  const emit = defineEmits(['hideModal']);
</script>

<style lang="scss" scoped>
  .modal {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.24);
    &__inner {
      position: relative;
      height: 100%;
    }
    &__close {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 32px;
      height: 32px;
      background: rgba(#ead592, .5);
      border: none;
      border-radius: 4px;
      cursor: pointer;
      box-shadow: 0 2px 2px 0 rgba(0,0,0,0.14), 0 3px 1px -2px rgba(0,0,0,0.12), 0 1px 5px 0 rgba(0,0,0,0.2);
      position: absolute;
      left: 0px;
      top: 120px;
      @media (max-width: 400px) {
      left: -25px;
    }

      img {
        width: 18px;
      }
    }
  }
</style>