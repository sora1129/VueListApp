<script setup lang="ts">
  import { ref, reactive, computed, watch, toRefs } from 'vue'

  // const itemName1 = ref<string>('Desk')
  const itemName2 = 'Bike'

  const item1 = reactive({
    name: 'Desk',
    price: 40000
  })

  const price1 = 40000
  const price2 = 20000

  const url1 = 'https://www.amazon.co.jp/%E3%82%B5%E3%83%B3%E3%83%AF%E3%83%80%E3%82%A4%E3%83%AC%E3%82%AF%E3%83%88-%E3%83%91%E3%82%BD%E3%82%B3%E3%83%B3%E3%83%87%E3%82%B9%E3%82%AF-%E5%BC%95%E3%81%8D%E5%87%BA%E3%81%97%E4%BB%98%E3%81%8D-%E3%83%80%E3%83%BC%E3%82%AF%E3%83%96%E3%83%A9%E3%82%A6%E3%83%B3-100-DESKH010BR/dp/B015YUDEGW/ref=sr_1_1_sspa?__mk_ja_JP=%E3%82%AB%E3%82%BF%E3%82%AB%E3%83%8A&crid=32P28104W851Q&keywords=%E6%9C%BA&qid=1659772478&sprefix=%E6%9C%BA%2Caps%2C221&sr=8-1-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUEyQldRNTdRQURUN1dZJmVuY3J5cHRlZElkPUEwMDM3NTUzM1JBVVFHRVNBR0FYVCZlbmNyeXB0ZWRBZElkPUFQN1EyMURCU1NGWUomd2lkZ2V0TmFtZT1zcF9hdGYmYWN0aW9uPWNsaWNrUmVkaXJlY3QmZG9Ob3RMb2dDbGljaz10cnVl'

  const buy = (itemName: string) => {
    alert('Are you sure tu buy ' + itemName + '?')
  }

  const clear = () => {
    item1.name = ''
    item1.price = 0
  }

  const budget = 50000
  const priceLabel = computed(() => {
    if(item1.price > budget * 2) {
      return 'too expensive...'
    } else if(item1.price > budget) {
      return 'expensive...'
    } else {
      return item1.price + 'yen'
    }
  })

</script>

<template>
  <div class="container">
    <h1>Payment</h1>
    <input v-model="item1.name"/>
    <input v-model="item1.price"/>
    <button v-on:click="clear">Clear</button>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ priceLabel}}</label>
      <!-- <label>{{ item1.price }} yen</label> -->
      <a v-bind:href="url1">bought at...</a>
      <button @click="buy(item1.name)">BUY</button>
    </div>
    <div class="payment">
      <label>{{ itemName2 }}</label>
      <label>{{ price2 }} yen</label>
      <button @click="buy(itemName2)">BUY</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

input {
  margin-bottom: 8px;
}

.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  width: 400px;
  background-color: aliceblue;
  margin: 10px 0;
}

label {
  font-size: 20px;
  font-weight: bold;
}
</style>