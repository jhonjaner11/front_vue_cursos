<template>

<v-container class="grey lighten-5">
    <v-row
      v-for="item in items" 
      :key="item.id"
      justify='center'
      
    >
      <v-col
        md="4"
      >
        <v-card
          class="pa-2"
          outlined
          tile
        >
          <v-card-title primary-title>
             {{item.course}}
          </v-card-title>
          <v-card-text>
              {{item.status}}
          </v-card-text>
          <v-btn color="success" v-on:click="get_contenido(item.course)">contenido</v-btn>
        </v-card>
      </v-col>
    </v-row>
  </v-container>

</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  props: ['id_user'],
  
  data(){
    return{
      items: [],
      //id: 326,
    }
  },
  components: {
  
  },
  methods:{

    get_contenido: function (id) {
      // `this` dentro de los métodos apunta a la instancia de Vue
      this.$router.push({ name: 'Contenido', params: {id: id }})
    }
  },
   mounted () {
    
    let aa = 'http://localhost:3000/api/matriculas/'+this.id_user;
    axios
      .get(aa)
      .then(response => (this.items = response.data))
  }
};
</script>
