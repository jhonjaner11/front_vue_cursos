<template>
   <v-app id="inspire">
      <v-content>
         <v-container fluid fill-height>
            <v-layout align-center justify-center>
               <v-flex xs12 sm8 md4>
                  <v-card class="elevation-12">
                     <v-toolbar dark color="primary">
                        <v-toolbar-title>Login form</v-toolbar-title>
                     </v-toolbar>
                     <v-card-text>
                        <v-form>
                           <v-text-field
                              prepend-icon="person"
                              name="login"
                              label="Login"
                              type="text"
                              v-model="username"
                           ></v-text-field>
                           <v-text-field
                              id="password"
                              prepend-icon="lock"
                              name="password"
                              label="Password"
                              type="password"
                              v-model="password"
                           ></v-text-field>
                        </v-form>
                     </v-card-text>
                     <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn color="primary" v-on:click="Login">Login</v-btn>
                     </v-card-actions>
                  </v-card>
               </v-flex>
            </v-layout>
         </v-container>
      </v-content>
   </v-app>
</template>

<script>

import axios from "axios";
export default {
   name: 'Login',
   props: {
      source: String,
   },
   data(){
      return {
         username: null,
         password: null
      }
   },
  
   methods: {
    Login: function () {
      
      axios
         .post('http://localhost:3000/api/login/', {"username":this.username})
         .then(response => {
            console.log(response.data[0].id);
            this.$router.push({ name: 'Home', params: {id_user: response.data[0].id }})
            //window.location.assign("/")
         })
    }
  }
};
</script>

<style></style>
