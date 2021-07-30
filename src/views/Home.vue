<template>

<v-container class="grey lighten-5">
  <v-row>
    <v-col
      v-for="item in items" 
      :key="item.id"
      justify='center'
      cols="6"
       
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
  
  
  data(){
    return{
      items: [],
      //id: 326,
    }
  },
  beforeCreate: function () {
    console.log("estado: "+this.$store.state.auth);
    if (!this.$store.state.auth) {
      this.$router.push("/login");
    }
  },
  components: {
  
  },
  methods:{

    get_contenido: function (id) {
      // `this` dentro de los métodos apunta a la instancia de Vue
      this.$router.push({ name: 'Contenido', params: {id: id }})
    },

    logout: function () {
      
      this.$router.push("/")
    }
  },
   mounted () {
    
    let aa = '/matriculas/'+this.$store.state.user.id;
    axios
      .get(aa)
      .then(response => (this.items = response.data))
  }
};
</script>
