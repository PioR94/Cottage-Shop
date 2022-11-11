<template>

  <the-header></the-header>
  <the-shop></the-shop>

</template>

<script>
import TheShop from "@/components/TheShop";
import TheHeader from "@/components/TheHeader";

export default {
  name: 'App',
  components: {
    TheShop,
    TheHeader,
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

</style>
