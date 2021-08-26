<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      
    </v-app-bar>

    <v-main>
      <Main01 v-if="false" />
      <Main02 />

    </v-main>
  </v-app>
</template>

<script>


import Main01 from "./components/layout01/main";
import Main02 from "./components/layaut02/main";

export default {
  name: 'App',

  components: {
    Main01,
    Main02,
  },

  data: () => ({
    //
  }),
};
</script>

<style lang="scss">
  *{
   
    box-sizing: border-box;
  }
</style>
