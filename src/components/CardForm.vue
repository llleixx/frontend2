<script setup>
import { ref } from 'vue'
import MyButton from './MyButton.vue'
const props = defineProps({
  change: {
    required: true,
    type: Function
  }
});

const cardName = ref('')
const cardNumber = ref('')
const cardMonth = ref('')
const cardYear = ref('')
const cardCvc = ref('')

const errorCardName = ref('')
const errorCardNumber = ref('')
const errorCardDate = ref('')
const errorCardCvc = ref('')

function checkCardName(e) {
  if (cardName.value === '') {
    errorCardName.value = "Can't be blank"
    e.target.classList.add('error')
  } else {
    errorCardName.value = ""
    e.target.classList.remove('error')
  }
}

function checkCardNumber(e) {
  if (cardNumber.value === '') {
    errorCardNumber.value = "Can't be blank"
    e.target.classList.add('error')
  } else if (!/^\d+$/.test(cardNumber.value)) {
    errorCardNumber.value = "Wrong format, numbers only"
    e.target.classList.add('error')
  } else {
    errorCardNumber.value = ""
    e.target.classList.remove('error')
  }
}

function checkCardMonth(e) {
  if (cardMonth.value === '') {
    errorCardDate.value = "Can't be blank"
    e.target.classList.add('error')
  } else if (!/\d{2}/.test(cardMonth.value)) {
    errorCardDate.value = 'Wrong format, two numbers'
    e.target.classList.add('error')
  } else {
    errorCardDate.value = ""
    e.target.classList.remove('error')
  }
}

function checkCardYear(e) {
  if (cardYear.value === '') {
    errorCardDate.value = "Can't be blank"
    e.target.classList.add('error')
  } else if (!/\d{2}/.test(cardYear.value)) {
    errorCardDate.value = 'Wrong format, two numbers'
    e.target.classList.add('error')
  } else {
    errorCardDate.value = ""
    e.target.classList.remove('error')
  }
}

function checkCardCvc(e) {
  if (cardCvc.value === '') {
    errorCardCvc.value = "Can't be blank"
    e.target.classList.add('error')
  } else if (!/\d+/.test(cardCvc.value)) {
    errorCardCvc.value = 'Wrong format, numbers only'
    e.target.classList.add('error')
  } else {
    errorCardCvc.value = ""
    e.target.classList.remove('error')
  }
}

</script>

<template>
  <form class="input-form">
    <div class="input-wrapper">
      <label for="card-name">CARDHOLDER NAME</label>
      <input type="text" placeholder="e.g. Jane Appleseed" class="card-name" id="card-name" v-model="cardName"
        @input="checkCardName" required />
      <p class="error-info">{{ errorCardName }}</p>
    </div>
    <div class="input-wrapper">
      <label for="card-number">CARD NUMBER</label>
      <input type="text" placeholder="e.g. 1234 5678 9123 0000" class="card-number" id="card-number" v-model="cardNumber"
        @input="checkCardNumber" required />
      <p class="error-info">{{ errorCardNumber }}</p>
    </div>
    <div class="input-footer-wrapper">
      <div class="input-exp-date">
        <label for="card-month">EXP. DATE (MM/YY)</label>
        <div class="card-month-year">
          <input type="text" placeholder="MM" id="card-month" v-model="cardMonth" @input="checkCardMonth" required />
          <input type="text" placeholder="YY" id="card-year" v-model="cardYear" @input="checkCardYear" required />
        </div>
        <p class="error-info">{{ errorCardDate }}</p>
      </div>
      <div class="input-cvc">
        <label for="card-cvc">CVC</label>
        <input type="text" placeholder="e.g. 123" id="card-cvc" v-model="cardCvc" @input="checkCardCvc" required />
        <p class="error-info">{{ errorCardCvc }}</p>
      </div>
    </div>
    <MyButton :change="props.change">Confirm</MyButton>
  </form>
</template>

<style lang="scss" scoped>
$linear-s: hsl(249, 99%, 64%);
$linear-e: hsl(278, 94%, 30%);
$red: hsl(0, 100%, 66%);
$light-grayish-violet: hsl(270, 3%, 87%);
$very-dark-violet: hsl(278, 68%, 11%);

form {
  color: $very-dark-violet;
}

.input-footer-wrapper {
  display: flex;
  flex-direction: row;

  input {
    width: auto;
  }
}

.error-info {
  color: red;
  font-size: 0.7em;
  margin-bottom: 20px;
}

.card-month-year {
  display: flex;
  flex-direction: row;

  input {
    margin-right: 8px;
  }
}

.input-exp-date,
.input-cvc {
  flex: 1;
}

input[type='text'] {
  box-sizing: border-box;
  width: 100%;
  margin-top: 8px;
  height: 2.5em;
  border: 1px solid grey;
  border-radius: 10px;
  font-size: 18px;
  padding: 5px 12px;
}

input.error {
  border-color: red;
}

input:focus {
  outline: none;
  border-color: purple;
}
</style>