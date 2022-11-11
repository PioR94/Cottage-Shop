<template>
    <button @click="sortByPriceDown">down</button>
  <button @click="sortByPriceUp">up</button>
    <input type="text" placeholder="fraza" v-model="search">
  <ul>
    <pet-house
        v-for="item in filterItems"
        :key="item.id"
        :id="item.id"
        :name="item.name"
        :typeOfHouse="item.typeOfHouse"
        :typeOfAnimal="item.typeOfAnimal"
        :price="item.price"
        :quantity="item.quantity"
        :description="item.description"
    >
    </pet-house>
  </ul>

</template>


<script>
import PetHouse from "@/components/PetHouse";


export default {
  inject: ['shopItems'],
  components: {
    PetHouse,

  },
  data() {
    return {
      search: '',
      sortedItem: '',
    }
  },
  computed: {
    filterItems() {
      return this.shopItems.filter(item =>
          item.name.includes(this.search)
          || item.typeOfAnimal.includes(this.search)
          || item.typeOfHouse.includes(this.search)
          || item.price.includes(this.search))
  },



  },
  methods: {
    sortByPriceUp() {
      this.shopItems.sort((a, b) => a.price > b.price ? 1 : -1)
    },
    sortByPriceDown() {
      this.shopItems.sort((a, b) => a.price < b.price ? 1 : -1)
    }
  }
}
</script>

<style scoped>
li {
  list-style: none;
}

ul {
  
}
</style>