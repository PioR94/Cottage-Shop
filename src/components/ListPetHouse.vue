<template>
  <input type="text" placeholder="Szukaj..." v-model="search" class="searchInput">

  <section class="sectionList">

    <ul>
      <pet-house
        v-for="item in filterItems"
        :key="item.id"
        :id="item.id"
        :name="item.name"
        :typeOfHouse="item.typeOfHouse"
        :typeOfAnimal="item.typeOfAnimal"
        :price="item.price"
        :description="item.description"
     >
      </pet-house>
   </ul>
  </section>
</template>


<script>
import PetHouse from "@/components/PetHouse";

export default {
  inject: ['shopItems'],
  components: {
    PetHouse,
  },
  provide() {
    return {

    }
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
          || item.description.includes(this.search)
      )
    },


  },

}
</script>

<style scoped>
li {
  list-style: none;
  margin-top: 1rem;
}

.sectionList {
  margin-left: calc(50% - 300px);

}

.searchInput {
  position: absolute;
  width: 15%;
  padding: 0.5rem 0;
  border: 2px solid #3a0061;
  text-align: center;
  right:5px;
  top: 1.5rem;
}
</style>