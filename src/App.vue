<template>
  <v-app>
    
    <v-main>
      <div style="width: 960px; margin: 0 auto; margin-top: 200px">
      <AniTable/>

      </div>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';
import AniTable from './components/AniTable.vue';

export default Vue.extend({
  name: 'App',

  components: {
    AniTable,
  },

  data: () => ({
    //
  }),
});
</script>
