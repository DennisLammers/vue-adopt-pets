<template>
  <div>
    <h1>Cats for adoption</h1>
    <b-table :items="cats" hover striped>
      <template v-slot:cell(name)="data">
        <router-link :to="`/pets/cats/${data.index}`">
          {{ data.value }}
        </router-link>
      </template>
    </b-table>
  </div>
</template>

<script>
  import {mapState} from 'vuex';

  export default {
    name: 'Cats',
    data() {
      return {};
    },
    computed: {
      ...mapState(['cats']),
    },
  };
</script>

<style scoped>

</style>
