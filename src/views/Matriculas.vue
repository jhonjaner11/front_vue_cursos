<template>
  <v-card
  elevation="2"
  >
    {{matriculas}}
  </v-card>
</template>

<script>
//import HelloWorld from "../components/HelloWorld";
import axios from "axios";
export default {
  name: "Matriculas",
  data(){
    return{
      matriculas: '',
    }
  },
  
  components: {
    //HelloWorld,
  },
  mounted () {
    axios
      .get('http://localhost:3000/api/matriculas/')
      .then(response => (this.matriculas = response.data.enrollments))
  }
};
</script>
