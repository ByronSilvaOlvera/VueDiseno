<template>
  <div class="main-001">
    <v-row class="proceso" style="margin: 0 !important">
      <v-col class="col-3">
        <div class="title-left" >
            <div>
                <v-icon>mdi-book</v-icon>
            </div>
            <div>
                Proceso
            </div>
        </div>  
        <v-list dense>
          <!-- <v-subheader>REPORTS</v-subheader> -->
          <v-list-item-group v-model="selectedItem" color="primary">
            <v-list-item v-for="(item, i) in items" :key="i"  @click="cambiomenu(i)" >
              <v-list-item-icon>
                <v-icon v-text="item.icon"> mdi-grid-view </v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title v-text="item.text"></v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-item-group>
        </v-list>
      </v-col>
      <v-col class="col-9" style="border: 2px solid blue" >
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
import ComponenteOne from "./component-001.vue";
import ComponenteTwo from "./component-002.vue";
import ComponenteThree from "./component-003.vue";

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
      return{
        selectedItem: 1,
        items: [
            { text: 'Relacion', icon: 'mdi-clock' },
            { text: 'Borrador', icon: 'mdi-account' },
            { text: 'Asignacion', icon: 'mdi-flag' },
        ],
        num:0
      }
  },
  methods : {
      cambiomenu(numero){
        this.num = numero
      }
  }
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

.title-left{
    min-height: 40px;
    border: 2px solid orange ;
    display: flex;
    justify-content: start;
    align-items: center;
    padding: 0 16px;
    div:nth-child(1){
        margin-right: 32px;
    }
}
</style>
