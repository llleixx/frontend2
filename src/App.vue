<script setup>
import { ref } from 'vue'
import cardform from '@/components/CardForm.vue'
import successinfo from '@/components/SuccessInfo.vue'

const submitted = ref(false)

function changeSubmitted() {
  submitted.value = !submitted.value;
}


</script>

<template>
  <main>
    <div class="banner">
      <div class="card-back card">
        <p>000</p>
      </div>
      <div class="card-front card">
        <div class="circles">
          <div class="circle-1"></div>
          <div class="circle-2"></div>
        </div>
        <p class="card-number">0000 0000 0000 0000</p>
        <div class="card-footer">
          <p>JANE APPLESEED</p>
          <p>00/00</p>
        </div>
      </div>
    </div>
    <div class="main-content">
      <cardform v-if="!submitted" :change="changeSubmitted"></cardform>
      <successinfo v-else :change="changeSubmitted"></successinfo>
    </div>
  </main>
</template>

<style lang="scss" scoped>
$font-stack: 'Space Grotesk', sans-serif;

main {
  font-family: $font-stack;
  font-size: 18px;
}

.banner {
  background: url(./assets/bg-main-mobile.png) top left / cover no-repeat;
  width: 100%;
  height: 250px;
  position: relative;
}

.card {
  position: absolute;
  width: 80%;
  height: 80%;
  border-radius: 8px;
}

.card-back {
  background: url(./assets/bg-card-back.png) top left / cover no-repeat;
  right: 8px;
  top: 10px;

  p {
    color: white;
    position: absolute;
    top: 44%;
    right: 12%;
  }
}

.card-front {
  background: url(./assets/bg-card-front.png) top left / cover no-repeat;
  bottom: -70px;
  left: 20px;
  color: white;

  .circles {
    display: flex;
    flex-direction: row;
    align-items: center;
  }

  .circle-1 {
    margin: 20px 25px;
    margin-right: 10px;
    width: 30px;
    height: 30px;
    border-radius: 100%;
    background-color: white;
  }

  .circle-2 {
    margin: auto 0;

    width: 10px;
    height: 10px;
    border-radius: 100%;
    border: 1px solid white;
  }

  .card-number {
    text-align: center;
    letter-spacing: .15rem;
    margin-top: 40px;
  }

  .card-footer {
    padding: 30px;
    font-size: 0.8rem;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
}

.main-content {
  margin: 110px 20px;
}

@media (min-width: 600px) {
  main {
    display: flex;
    flex-direction: row;
    min-height: 100vh;
    align-items: center;
  }

  .banner {
    flex: 1;
    background: url(./assets/bg-main-desktop.png) top left / contain no-repeat;
    background-size: auto 100%;
    min-height: 100vh;
  }

  .main-content {
    flex: 1;
    padding-left: 200px;
    padding-right: 100px;
  }

  .card {
    width: 400px;
    height: 224px;
  }

  .card-front {
    top: 120px;
    left: 120px;
  }

  .card-back {
    top: 400px;
    left: 200px;
  }
}
</style>