<script>
import axios from 'axios';

export default {
  name:'AppMain',
  data(){
    return{
      arrayProjects: []
    }
  },
  methods: {
    getProjects(){

      axios.get('http://127.0.0.1:8000/api/test')
      .then(res => {
        console.log(res.data.projects)

        this.arrayProjects = res.data.projects
      })
    }
  },
  mounted() {
    this.getProjects()
    
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
