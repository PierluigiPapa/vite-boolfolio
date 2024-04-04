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
    getProjects(projectApiPage){

      axios.get('http://127.0.0.1:8000/api/test',
      {
        params: {
          page: projectApiPage
        }
      }
      )
      .then(res => {
        console.log(res.data.projects.data)

        // this.arrayProjects = res.data.projects

        this.arrayProjects = res.data.projects.data
        this.currentPage = res.data.projects.current_page
        this.lastPage = res.data.projects.last_page
      })
    }
  },
  mounted() {
    this.getProjects()
    
  },
}
</script>

<template>

  <main>
    <h3>Cliccate qua per vedere i progetti:</h3>
    
    <ul>
      <li v-for="(element, index) in arrayProjects" :key="index"><a href="#">{{element.title}}</a></li>
    </ul>
  </main>

</template>

<style scoped>

</style>
