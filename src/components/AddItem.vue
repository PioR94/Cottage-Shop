<template>
  <section class="sectionAdd">
    <h2>Dodaj nowy domek</h2>
    <form @submit.prevent="submitData">
      <div class="form-style">
        <label for="name">Nazwa</label>
        <input name="name" id="name" type="text" ref="nameInput">
      </div>

      <div class="form-style">
        <label for="house">Rodzaj</label>
        <select name="house" id="house" ref="selectHouse">
          <option value="domek na drzewie">domek na drzewie</option>
          <option value="domek na ziemi">domek na ziemi</option>
        </select>
      </div>

      <div class="form-style">
        <select name="animal" id="animal" ref="selectAnimal">
          <option v-for="animal in animals" :value='animal' :key="animal">{{animal}}</option>
        </select>
          <form @submit.prevent="addAnimal">
            <div v-if="this.state">
            <label for="category"></label>
            <input id="category" type="text"  placeholder="nowa kategoria" ref="categoryInput">
            <the-button>Dodaj</the-button>
            </div>
          </form>

      </div>


      <div class="form-style">
      <label for="price">Cena w PLN</label>
      <input id="price" name="price" type="number" ref="inputPrice" min="0">
      </div>

      <div class="form-style">
        <label for="quantity">Ilość</label>
        <input id="quantity" name="quantity" type="number" min="1" ref="inputQuantity">
      </div>

      <div class="form-style">
        <label for="description">Opis</label>
        <textarea name="description" id="description" cols="30" rows="3" maxlength="200" ref="description"></textarea>
      </div>
      <the-button>Dodaj</the-button>
    </form>
    <div class="category-animal">
    <the-button @click="setState">Dodaj karegorię ziwerzęta</the-button>
    </div>
    <div  class="error-message">
    <the-error v-if="errorState"  message="Wypełnij wszystkie pola!">
      <template #ok>
        <the-button @click="closeMessage" mode="err-btn">X</the-button>
      </template>
    </the-error>
    </div>
  </section>
  
</template>

<script>
import TheButton from "@/components/TheButton";
import TheError from "@/components/TheError";

export default {
  inject: ['addHouse'],
  components: {
    TheButton,
    TheError,
  },
  data() {
    return {
      animals: ['niedźwiedź', 'sowa', 'lew'],
      errorState: false,
      errorMessage: '',
      state: false,
    }
  },
  methods: {
    submitData() {
      const enteredName = this.$refs.nameInput.value;
      const enteredHouse = this.$refs.selectHouse.value;
      const enteredAnimal = this.$refs.selectAnimal.value;
      const enteredPrice =  this.$refs.inputPrice.value;
      const enteredDescription = this.$refs.description.value;

      if (enteredName.trim() === ''
          || enteredPrice.trim() === ''
          || enteredDescription.trim() === '')
      {
        this.errorState = true;
        return;
      }

      console.log(enteredDescription);
     this.addHouse(enteredName, enteredHouse, enteredAnimal, enteredPrice, enteredDescription);
    },

    addAnimal() {
      const enteredCategory = this.$refs.categoryInput.value;

      if (enteredCategory.trim() === '') {
        this.errorState = true;
        return;
      }
      this.animals.push(enteredCategory);
    },

    setState() {
    this.state ? this.state = false : this.state = true;
    },

    closeMessage() {
      this.errorState = false;
    },
  }

}

</script>

<style scoped>

.sectionAdd {
  position: absolute;
  width: 50%;
  left: 25%;
  margin-top: 0.7rem;
  flex-direction: column;
}


input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
}

select {
  display: block;
  width: 40%;
  font: inherit;
}

.form-style {
  margin-top: 0.7rem;
}

.error-message {
  position: absolute;
  left: calc(50% - 150px);
  top: calc(50% - 50px);
}

.category-animal {
  position: absolute;
  right: 0%;
  top: 0%
}

#category {
  margin-top: 1rem;
}

</style>