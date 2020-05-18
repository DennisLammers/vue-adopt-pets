<template>
  <div>
    <h1>{{animal.name}} ({{this.$route.params.species}})</h1>
    <p>Age: {{animal.age}} years old</p>
    <p>Breed: {{animal.breed}}</p>
  </div>
</template>

<script>
  import {mapState} from 'vuex';

  export default {
    name: 'Cats',
    data() {
      return {
        animal: {},
      };
    },
    computed: {
      ...mapState(['cats', 'dogs']),
    },
    mounted() {
      this.animal = this[this.$route.params.species][this.$route.params.id];
    },
  };
</script>

<style scoped>

</style>
