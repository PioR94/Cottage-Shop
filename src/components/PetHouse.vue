<template>
  <li>
    <section>
      <h2>{{name}}</h2>
      <h3>Rodzaj: {{typeOfHouse}}</h3>
      <h3>Przeznaczenie: {{typeOfAnimal}}</h3>
      <h3>Cena:
        <div v-if="dollar" class="div-price">${{dollar}}</div>
        <div v-else class="div-price">{{price}}PLN</div>
        <the-button @click="changeCurrency" mode="change-currency">PLN/$</the-button>
      </h3>
      <div class="description">
         <p>{{description}}</p>
      </div>

      <the-button @click="buyItem" mode="buy">Kup</the-button>

    </section>
  </li>
</template>

<script>

import TheButton from "@/components/TheButton";


export default {
  inject: ['addToBasket'],
  components: {
    TheButton,
  },
  props: ['id', 'name', 'typeOfHouse', 'typeOfAnimal', 'price', 'description'],

  data() {
    return {
      dollar: '',

    }
  },

  methods: {
   changeCurrency() {
      fetch('http://api.nbp.pl/api/exchangerates/tables/A')
      .then(r => r.json())
      .then(data => {
        const res = (data[0]['rates'][1]['mid']);

        if (this.dollar) {
          this.dollar = '';
        } else
        this.dollar = (this.price / res).toFixed(2);
        console.log(this.dollar);
      });
   },
    buyItem() {
     this.addToBasket(this.id, this.name, this.price)

    }
  }
}
</script>

<style scoped>

section {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  height: 300px;
  width: 600px;
  border: 1px solid black;
}

.description {
  width: 500px;
  overflow: hidden;
  text-align: center;


}

.div-price {
  display: inline-block;
}




</style>