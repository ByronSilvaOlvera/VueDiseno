<template>
  <div>
    <h4>Componente 2</h4>
    <div>
        <v-row style="margin: 0 !important" >
            <v-col class="col-3" >
             <v-select :items="items"  label="Fitro Uno" dense></v-select>
             <v-select :items="items"  label="Fitro Dos" dense></v-select>
             <v-select :items="items"  label="Fitro Dos" dense></v-select>
             <v-select :items="items"  label="Fitro Dos" dense></v-select>
             <v-select :items="items"  label="Fitro Dos" dense></v-select>
            </v-col>
            <v-col class="col-9" >
                <v-sheet class="" elevation="1" max-width="100%" height="270" >
                    <v-slide-group
                    v-model="model"
                    class="pa-4"
                    active-class="success"
                    show-arrows
                    >
                    <v-slide-item v-for="n in 15" :key="n" >
                        <CardRuta style="heigth:100%" />
                    </v-slide-item>
                    </v-slide-group>
                </v-sheet>
            </v-col>
        </v-row>
      

    </div>
  </div>
</template>

<script>
import CardRuta from "./component-002-card.vue";
export default {
  components: {
    CardRuta
  },
  data: () => ({
    model: null,
     items: ['Foo', 'Bar', 'Fizz', 'Buzz'],
  })
};
</script>

<style>
</style>