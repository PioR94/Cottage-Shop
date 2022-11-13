<template>
  <li>
    <section>
      <h2>{{name}}</h2>
      <h3>{{price}}PLN </h3>
      <the-button @click="removeItem(this.id)">Usuń</the-button>
    </section>
  </li>
</template>


<script>
import TheButton from "@/components/TheButton";

export default {
  inject: ['removeItem'],
  props: ['id', 'name', 'price'],
  components: {TheButton},
}

</script>


<style scoped>

section {
  width: 300px;

  border: 1px solid black;
  text-align: center;
  line-height: 50px;
  margin-left: 30px;
  margin-top: 20px;
}

</style>