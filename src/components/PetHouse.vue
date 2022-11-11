<template>
  <li>
    <section>
      <h2>{{name}}</h2>
      <h3>Rodzaj: {{typeOfHouse}}</h3>
      <h3>Przeznaczenie: {{typeOfAnimal}}</h3>
      <h3>Cena: {{price}}</h3>
      <p>{{description}}</p>
      <p>Ilość: {{quantity}}</p>

      <the-button>Kup</the-button>

    </section>
  </li>
</template>

<script>

import TheButton from "@/components/TheButton";

export default {
  components: {
    TheButton,
  },
  props: ['id', 'name', 'typeOfHouse', 'typeOfAnimal', 'price', 'quantity', 'description'],

}
</script>

<style scoped>

section {
  height: 300px;
  width: 800px;
  border: 1px solid black;
}

</style>