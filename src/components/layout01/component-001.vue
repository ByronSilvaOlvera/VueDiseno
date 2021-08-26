<template>
  <div>
      Componente 1

    <div>
        <v-row style="margin:0 !important" >
            <v-col cols="12"  class="d-flex" >  
                <v-autocomplete class="col-3" v-model="value" :items="Sector" dense label="Region"></v-autocomplete>
                <v-autocomplete class="col-3" v-model="value" :items="Sector" dense label="Provincia"></v-autocomplete>
            </v-col>
        </v-row>
        <v-row style="margin: 0 !important" >
            <v-col cols="6" >
                <v-list dense>
                    <!-- <v-subheader>REPORTS</v-subheader> -->
                    <v-list-item-group v-model="selectedItem" color="primary">
                        <v-list-item v-for="(item, i) in Sector" :key="i"  @click="cambiomenu(i)" >
                            <v-list-item-icon>
                                <v-icon v-text="item.icon"> mdi-grid-view </v-icon>
                            </v-list-item-icon>
                            <v-list-item-content>
                                <v-list-item-title v-text="item.text"></v-list-item-title>
                            </v-list-item-content>
                            <v-list-item-icon v-if="item.estado" >
                                <v-icon > mdi-check  </v-icon>
                            </v-list-item-icon>
                        </v-list-item>
                    </v-list-item-group>
                </v-list>
            </v-col>
            <v-col cols="6" >  
                <div v-if=" num > -1" >
                    <div  v-for="(item, i) in sectorBarrio" :key="i" >
                        <v-checkbox   style="margin-top: 0 !important " class="check-box-1"
                                        v-model="item.estado"
                                        
                                        :label="`${item.text}: ${item.estado.toString()}`"
                        ></v-checkbox>
                    </div>
                </div>
                <!-- <v-list dense>
                    
                    <v-list-item-group v-model="selectedItem" color="primary">
                        <v-list-item v-for="(item, i) in barrio" :key="i"  @click="cambiomenu(i)" >
                            <v-list-item-icon>
                                <v-icon v-text="item.icon"> mdi-grid-view </v-icon>
                            </v-list-item-icon>
                            <v-list-item-content>
                                <v-checkbox style="margin-top: 0 !important " class="check-box-1"
                                v-model="checkbox"
                                :label="`Checkbox 1: ${checkbox.toString()}`"
                                ></v-checkbox>
                            </v-list-item-content>


                            <v-list-item-icon v-if="item.estado" >
                                <v-icon  v-text="item.icon"> mdi-grid-view </v-icon>
                            </v-list-item-icon>
                           
                        </v-list-item>
                    </v-list-item-group>
                </v-list> -->
            </v-col>
        </v-row>
    </div>
  </div>
</template>

<script>
export default {
  props: {},
   data() {
      return{
        selectedItem: 1,
        Sector: [
            { text: 'Florida', icon: 'mdi-clock' , estado: false },
            { text: 'Bastion', icon: 'mdi-account' , estado: false},
            { text: 'Mapasingue', icon: 'mdi-flag' , estado: false},
        ],
        barrio: [

            { text: 'Coop Unidos Somos Mas', icon: 'mdi-clock' , estado: false , secto: 0},
            { text: 'Coop Calle Azul', icon: 'mdi-account' , estado: false, secto: 0},
            { text: 'Patria Nueva', icon: 'mdi-flag' , estado: false, secto: 0},

            { text: 'Coop BUs', icon: 'mdi-clock' , estado: false , secto: 1},
            { text: 'Coop Sedan', icon: 'mdi-account' , estado: false, secto: 1},
            { text: 'Patria CAmioneta', icon: 'mdi-flag' , estado: false, secto: 1},

            { text: 'Coop Perro', icon: 'mdi-clock' , estado: false , secto: 2},
            { text: 'Coop Gato', icon: 'mdi-account' , estado: false, secto: 2},
            { text: 'Patria Loro', icon: 'mdi-flag' , estado: false, secto: 2},
        ],
        sectorBarrio : [], 
        num:-1,
        checkbox: true,
      }
  },
  methods:{
      cambiomenu(i){
          console.log(i, this.num);
          i == this.num ? this.num = -1 : this.num = i ;
         console.log(i);
          this.Sector.forEach( (x, a) => {
              this.num == a ? x.estado = true : x.estado = false;
          })
          if ( i > -1 ){
              this.sectorBarrio = [];
              this.sectorBarrio = this.barrio.filter( x => x.secto == i )
          }
      }
  }
};
</script>

<style lang="scss">
    .check-box-1{
        .v-messages{
            display: none !important;
        }
        .v-input__slot{
            margin-top: 0 !important;
        }
    }
</style>