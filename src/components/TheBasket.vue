<template>
  <ul>
    <house-in-basket
      v-for="item in basket"
      :key="item.id"
      :id="item.id"
      :name="item.name"
      :price="item.price"
    >
    </house-in-basket>
  </ul>
</template>

<script>
import HouseInBasket from "@/components/HouseInBasket";

export default {
  inject: ['basket', 'sum'],
  components: {HouseInBasket},
  data() {
    return {
      sum: 0,
    }
  },
  methods: {

  }
}

</script>