<template>
  <section class="changeComponent">
    <the-button @click="setSelectedComponent('list-pet-house')">Domki</the-button>
  <the-button @click="setSelectedComponent('add-item')">Dodaj produkt</the-button>
  <the-button @click="setSelectedComponent('the-basket')">Koszyk</the-button>
  <the-button @click="sortByPriceDown">Cena malejąco</the-button>
  <the-button @click="sortByPriceUp" >Cena rosnąco</the-button>
  </section>
  <keep-alive>
  <component :is="selectedComponent"></component>
  </keep-alive>
</template>

<script>

import TheButton from "@/components/TheButton";
import ListPetHouse from "@/components/ListPetHouse";
import AddItem from "@/components/AddItem";
import TheBasket from "@/components/TheBasket";

const {v4: uuid} = require('uuid');

export default {
  components: {
    ListPetHouse,
    TheButton,
    AddItem,
    TheBasket,
  },
  data() {
    return {

      shopItems: [
        {
          id: uuid(),
          name: 'Dziupla',
          typeOfHouse: 'domek na drzewie',
          typeOfAnimal: 'sowa',
          price: 200,
          description: "Lorem Lorem Lorem Lorem Lorem  Lorem  Lorem Lorem Lorem Lorem Lorem Lorem Lorem Lorem Lorem Lorem Lorem Lorem ",
        },
        {
          id: uuid(),
          name: 'Jaskinia',
          typeOfHouse: 'domek na ziemi',
          typeOfAnimal: 'niedźwiedź',
          price: 300,
          description: "Lorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem Lo",
        },
      ],
      selectedComponent: 'list-pet-house',
      basket: [],
    }
  },
  provide() {
    return {
      shopItems: this.shopItems,
      addHouse: this.addHouse,
      addToBasket: this.addToBasket,
      basket: this.basket,
      removeItem: this.removeItem,
    }
  },
  computed: {

  },
  methods: {
    setSelectedComponent(active) {
        this.selectedComponent = active;
    },

    addHouse(name, typeOfHouse, typeOfAnimal, price, description ) {
      const item = {
        id: uuid(),
        name: name,
        typeOfHouse: typeOfHouse,
        typeOfAnimal: typeOfAnimal,
        price: price,
        description: description,
      };

      this.shopItems.unshift(item);
      this.selectedComponent = 'list-pet-house';
    },

    sortByPriceUp() {
      this.shopItems.sort((a, b) => a.price > b.price ? 1 : -1)
    },
    sortByPriceDown() {
      this.shopItems.sort((a, b) => a.price < b.price ? 1 : -1)
    },
    addToBasket(id, name, price) {
      const item = {
        id,
        name,
        price,
      };

      const result = this.basket.find(data => data.id === item.id );
      if (!result) this.basket.unshift(item);

    },
    removeItem(id) {
      const result = this.basket.findIndex(res => res.id === id);
      this.basket.splice(result, 1);
    }
  }

}
</script>


<style scoped>
.changeComponent {
  display: flex;
  justify-content: center;


}

</style>