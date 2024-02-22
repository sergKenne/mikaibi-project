<template>
  <header class="header">
    <div class="container">
      <div class="header__inner">
        <div class="header__item">
          <p>Anton</p>
          <div class="header__counter">
            <span>1000</span>
            <img src="../assets/img/coin.png" alt="coin">
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>

</script>

<style lang="scss" scoped>
  .header {
    &__inner {
      display: flex;
      justify-content: flex-end;
    }
    &__item {
      font-weight: 900;
      font-size: 18px;
    }
    &__counter {
      display: flex;
      align-items: center;
      gap: 5px;
    }

    img {
      width: 20px;
    }
  }
</style>