<template>
  <div>
    <h1>Dogs for adoption</h1>
    <b-table :items="dogs" hover striped>
      <template v-slot:cell(name)="data">
        <router-link :to="`/pets/dogs/${data.index}`">
          {{ data.value }}
        </router-link>
      </template>
    </b-table>
  </div>
</template>

<script>
  import {mapState} from 'vuex';

  export default {
    name: 'Dogs',
    data() {
      return {};
    },
    computed: {
      ...mapState(['dogs']),
    },
  };
</script>

<style scoped>

</style>
