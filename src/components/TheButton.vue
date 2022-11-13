<template>
  <button :class='mode'>
    <slot></slot>
  </button>

</template>

<script>
export default {
  props: ['mode']
}
</script>


<style scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #3a0061;
  border: 1px solid #3a0061;
  color: white;
  cursor: pointer;
}

button:hover {
  background-color: #270041;
  border-color: #270041;
}

.err-btn {
  position: absolute;
  border: none;
  padding: 0.25rem 0.5rem;
  background-color: transparent;
  right: 0;
  top: 0;
  color: black;
  font-size: 15px;
;
}
.err-btn:hover {
  background-color: transparent;
  color: wheat;
}

.buy {
  width: 100px;
}

.change-currency {

  background-color: transparent;
  color: black;
  font-size: 15px;
  border: none;
}

.change-currency:hover {
  background-color: transparent;
  color: blueviolet;
}


</style>