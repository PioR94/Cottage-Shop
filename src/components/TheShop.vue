<template>
  <section>
  <the-button @click="setSelectedComponent('list-pet-house')">Domki</the-button>
  <the-button @click="setSelectedComponent('add-item')">Dodaj produkt</the-button>
  <the-button @click="setSelectedComponent('the-basket')">Koszyk</the-button>
  </section>
  <component :is="selectedComponent"></component>
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
          price: '200',
          quantity: 1,
          description: "Lorem LoremLoremLoremLoremLoremLoremLoremLoremLoremLoremLoremLoremLoremLoremLor emLoremLoremLoremLoremLoremLoremLoremLoremLoremLoremLoremLorem",
        },
        {
          id: uuid(),
          name: 'Jaskinia',
          typeOfHouse: 'domek na ziemi',
          typeOfAnimal: 'niedźwiedź',
          price: '300',
          quantity: 4,
          description: "Lorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem LoLorem Lo",
        },
      ],
      selectedComponent: 'list-pet-house',
    }
  },
  provide() {
    return {
      shopItems: this.shopItems,
      addHouse: this.addHouse,
    }
  },
  computed: {

  },
  methods: {
    setSelectedComponent(active) {
        this.selectedComponent = active;
    },

    addHouse(name, typeOfHouse, typeOfAnimal, price, quantity, description ) {
      const item = {
        id: uuid(),
        name: name,
        typeOfHouse: typeOfHouse,
        typeOfAnimal: typeOfAnimal,
        price: price,
        quantity: quantity,
        description: description,
      };

      this.shopItems.unshift(item);
      this.selectedComponent = 'list-pet-house';
    },

  }

}
</script>


<style scoped>


</style>