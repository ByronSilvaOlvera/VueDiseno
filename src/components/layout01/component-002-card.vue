<template>
  <div>
    <v-card
      :color="active ? undefined : 'grey lighten-1'"
      class="ma-4"
      height="220"
      width="170"
      @click="toggle"
    >
      <div class="text-overline ">
        <v-icon>mdi-map-marker</v-icon>
        Ruta {{ ruta }}
      </div>
      <v-row class="fill-height" align="start" justify="left"  style="margin:0 !important" >
        <v-scale-transition>
          <v-row style="margin: 0 !important" >
            <v-col class="col-12 d-flex justify-space-between" v-for="n in 10" :key="n" style="padding: 5px 8px;"  >
              <div>
                <v-icon color="red" size="16" >mdi-book</v-icon>
                <span>Local {{ n }}</span>             
              </div>
              <div>
                <v-icon color="red" size="16" >mdi-book</v-icon>
              </div>
            </v-col>
          </v-row>
        </v-scale-transition>
      </v-row>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ruta: 1,
    };
  },
};
</script>

<style>
</style>