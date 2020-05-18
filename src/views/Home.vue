<template>
  <div class="home">
    <h1>Adopt a new best friend.</h1>
    <p>There are {{ animalsCount }} animals.</p>
    <p>There are {{ getAllCats.length }} cats.</p>
    <button class="btn btn-primary" @click="togglePetForm()">Add new pet</button>

    <b-form @submit.prevent="handleSubmit" v-if="showPetForm">
      <b-form-group id="input-group-2" label="Pet's Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="formData.name"
          type="text"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Species:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="formData.species"
          :options="['cats','dogs']"
          required
        ></b-form-select>
      </b-form-group>
      <b-form-group id="input-group-4" label="Pet's Age:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="formData.age"
          type="number"
          required
          placeholder="Enter age"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
  </div>
</template>

<script>
  import {mapActions} from 'vuex';
  import {mapGetters} from 'vuex';

  export default {
    name: 'Home',
    data() {
      return {
        showPetForm: false,
        formData: {
          name: '',
          age: 0,
          species: null,
        },
      };
    },
    computed: {
      ...mapGetters([
        'animalsCount',
        'getAllCats'
      ]),
    },
    methods: {
      ...mapActions([
        'addPet'
      ]),
      togglePetForm() {
        this.showPetForm = !this.showPetForm;
      },
      handleSubmit() {
        const {species, age, name} = this.formData;
        const payload = {
          species: species,
          pet: {
            species: species,
            name: name,
            age: age,
          },
        };
        this.addPet(payload);

        // reset the form after submit
        this.formData = {
          name: '',
          age: 0,
          species: null,
        };

        this.showPetForm=false;
      },
    },
  };
</script>
