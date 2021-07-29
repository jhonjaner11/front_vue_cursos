<template>

  <v-container class="grey lighten-5">
    <v-card>
      <v-card-title primary-title>
        Contenido {{this.id}}
      </v-card-title>
      <v-card-text>
        <p class="card-text" v-html="contenido"></p>
      </v-card-text>
    </v-card>
    
  </v-container>

</template>

<script>
import axios from "axios";
export default {
  name: "Contenido",
  props: ['id'],
  
  data(){
    return{
      items: [],
      
      contenido: "",
    }
  },
  components: {
  
  },
   mounted () {
    
    let aa = 'http://localhost:3000/api/contenido/'+this.id;
    axios
      .get(aa)
      .then(response => (this.contenido = response.data))
  }
};
</script>
