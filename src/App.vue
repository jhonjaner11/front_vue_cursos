<template>
  <v-app>
     <v-card
    color="grey lighten-4"
    flat
    height="200px"
    tile
  >
    <v-toolbar dense>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Cursera DEMO</v-toolbar-title>

     

       

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>

       <template v-if="$store.state.auth">
         <v-spacer></v-spacer>
        <span>{{$store.state.user.firstname}}</span> 
        <v-btn icon v-on:click="logout">
        <v-icon>mdi-logout</v-icon>
        </v-btn>
      </template>
    </v-toolbar>
    <v-card-text>
      <router-view />
    </v-card-text>
     
      
    
  </v-card>


   
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    //
  }),
  methods: {
    async logout (){
      await this.$store.dispatch("logout");
      this.$router.push("/login")
    }
  }
};
</script>
