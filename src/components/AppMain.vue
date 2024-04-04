<script>
import axios from 'axios';

export default {
  name:'AppMain',
  data(){
    return{

    }
  },
  methods: {
    getProjects(){

      axios.get('http://127.0.0.1:8000/api/test')
      .then(res => {
        console.log(res)
      })
    }
  },
  mounted() {
    
  },
}
</script>

<template>
  <h3>Cliccate qua per vedere i progetti:</h3>

</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
