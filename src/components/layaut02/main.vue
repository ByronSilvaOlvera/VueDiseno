<template>
  <div class="main-001">
    
    <v-row style="margin: 0 !important" class="py-4" > 
      <v-sheet class="mx-auto" max-width="700">
        <v-slide-group multiple show-arrows>
          <v-slide-item v-for="n in 25" :key="n" v-slot="{ active }">
            <v-btn
              class="mx-2"
              :input-value="active"
              active-class="purple white--text"
              depressed
              rounded
              @click="cambiomenu(n-1)"
            >
              Options {{ n }}
            </v-btn>
          </v-slide-item>
        </v-slide-group>
      </v-sheet>
    </v-row>

    <v-row class="proceso" style="margin: 0 !important">
      <v-col class="col-12" style="border: 2px solid blue">
        <!-- 1 -->
        <ComponenteOne v-if="num == 0" />
        <!-- 2 -->
        <ComponenteTwo v-if="num == 1" />
        <!-- 3 -->
        <ComponenteThree v-if="num == 2" />
      </v-col>
    </v-row>
    <v-row class="tb" style="margin: 0 !important">
      <tb-component></tb-component>
    </v-row>
  </div>
</template>

<script>
import Table from "./table.vue";
import ComponenteOne from "../layout01/component-001.vue";
import ComponenteTwo from "../layout01/component-002.vue";
import ComponenteThree from "../layout01/component-003.vue";

export default {
  props: {
    tipo: Number,
  },
  components: {
    "tb-component": Table,
    ComponenteOne,
    ComponenteTwo,
    ComponenteThree,
  },
  data() {
    return {
      selectedItem: 1,
      items: [
        { text: "Relacion", icon: "mdi-clock" },
        { text: "Borrador", icon: "mdi-account" },
        { text: "Asignacion", icon: "mdi-flag" },
      ],
      num: 0,
    };
  },
  methods: {
    cambiomenu(numero) {
      this.num = numero;
    },
  },
};
</script>

<style lang="scss" >
.tb {
  border: 2px solid red;
}
.main-001 {
  .proceso {
    height: 350px;
  }

  v-row {
    margin: 0 !important;
    border: 0 !important;
  }
}

.title-left {
  min-height: 40px;
  border: 2px solid orange;
  display: flex;
  justify-content: start;
  align-items: center;
  padding: 0 16px;
  div:nth-child(1) {
    margin-right: 32px;
  }
}
</style>
