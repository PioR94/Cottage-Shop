<template>
  <section>
    <h2>Dodaj nowy domek</h2>
    <form @submit.prevent="submitData">
      <div>
        <label for="name"></label>
        <input name="name" id="name" type="text" ref="nameInput">
      </div>
      <select name="house" id="house" ref="selectHouse">
        <option value="treeHouse">Domek na drzewie</option>
        <option value="earthHouse">Domek na ziemi</option>
      </select>
      <br>
      <select name="animal" id="animal" ref="selectAnimal">
        <option value="bear">Niedźwiedź</option>
        <option value="owl">Sowa</option>
      </select>
      <br>
      <div>
      <label for="price">Cena</label>
      <input id="price" name="price" type="text" ref="inputPrice">
      </div>
      <div>
        <label for="quantity">Ilość</label>
        <input id="quantity" name="quantity" type="number" min="1" ref="inputQuantity">
      </div>
      <label for="description">Opis</label>
      <textarea name="description" id="description" cols="30" rows="3" ref="description"></textarea>
      <the-button>Dodaj</the-button>

    </form>
  </section>
  
</template>

<script>
import TheButton from "@/components/TheButton";

export default {
  inject: ['addHouse'],
  components: {
    TheButton,
  },
  methods: {
    submitData() {
      const enteredName = this.$refs.nameInput.value;
      const enteredHouse = this.$refs.selectHouse.value;
      const enteredAnimal = this.$refs.selectAnimal.value;
      const enteredPrice =  this.$refs.inputPrice.value;
      const enteredQuantity = this.$refs.inputQuantity.value;
      const enteredDescription = this.$refs.description.value;

     this.addHouse(enteredName, enteredHouse, enteredAnimal, enteredPrice, enteredQuantity, enteredDescription);


    }
  }

}

</script>
