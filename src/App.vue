<template>
  <div class="app">
    <HeaderComponent />
    <main class="main">
      <div class="container main__content">
        <button class="main__bulb" @click="isModal = true">
          <img src="./assets/img/bulb.png" alt="bulb">
        </button>
        <h3 class="main__subtitle">Choose the right answer</h3>
        <h1 class="main__title">Which shape shows thirds?</h1>
        <img src="./assets/img/task_img.png" alt="shape" class="main__images">
      </div>
    </main>
    <section class="buttons" v-if="!isHide">
      <ButtonRadio v-for="item in radioItems" :item="item" :key="item.id" :handleChange="handleChange"/>
      <div class="button">
        <label class="button__label button__label--check" @click="getResult">Check</label>
      </div>
    </section>
    <modal v-if="isModal" @hideModal="isModal = false"/>
  </div>
</template>

<script setup>
  import { ref } from 'vue';
  import HeaderComponent from './components/HeaderComponent.vue';
  import ButtonRadio from './components/ButtonRadio.vue';
  import Modal from './components/Modal.vue';

  const radioItems = ref([
    { id: 1, val: "A", checked: false, isTrue: true },
    { id: 2, val: "B", checked: false, isTrue: false },
    { id: 3, val: "C", checked: false, isTrue: false },
  ]);
  const checkValue = ref("");
  const isModal = ref(false);
  const isHide = ref(false)

  const handleChange = (e) => {
    checkValue.value = e.target.value;
  }
const getResult = () => {
  const answer = radioItems.value.find(item => (item.isTrue && (item.val == checkValue.value)));
    if (checkValue.value.length >= 1) { 
      if (!answer) {
        alert("You chose the wrong answer");
      } else {
        alert("You chose the correct answer A " + answer.val);
      }
      isHide.value = true;
    } else {
      alert("Please choose one answer!")
    }
    
  }
</script>

<style lang="scss" scoped>
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
.main {
  &__content {
    text-align: center;
    position: relative;
  }
  &__bulb {
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
    right: 32px;
    @media (max-width: 400px) {
      right: 10px;
    }


    img {
      width: 18px;
    }
  }
  
  &__images {
    margin-top: 160px;
    @media (max-width: 810px) {
      width: 500px;
    }
    @media (max-width: 550px) {
      width: 300px;
      margin-top: 120px;
    }
    @media (max-width: 350px) {
      width: 260px;
      margin-top: 70px;
    }
  }
}
.buttons {
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(#000, .1);
    gap: 18px;
    font-size: 22px;
    padding: 18px 22px;
    margin-top: auto;
    @media (max-width: 810px) {
      flex-wrap: wrap;
    }
  }
</style>
