<script>
import ProjectCard from './ProjectCard.vue';
import axios from 'axios';

export default {
  components: {
    ProjectCard
  },

  name:'AppMain',
  data(){
    return{
      arrayProjects: [],
      currentPage: '',
      lastPage: '',
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
    this.getProjects(1)
    
  },
}
</script>

<template>

  <main class="p-4">
    <h3 class="text-center fw-bold py-3">Clicca qui per vedere i miei progetti:</h3>
  
    <ProjectCard class="my-3" v-for="(element, index) in arrayProjects" :key="element.id" :title="element.title" :content="element.content" :type="element.type.name" :technologies="element.technologies"/>

    <nav aria-label="Page navigation example">
      <ul class="pagination justify-content-center">
        <li class="page-item pe-2" :class="{'disabled': currentPage === 1}"><button class="page-link" @click="getProjects(currentPage - 1)">PREV</button></li>
        <li class="page-item pe-2" v-for="(element,index) in lastPage" :key="element.id"><button class="page-link" @click="getProjects(element)">{{ element }}</button></li>
        <li class="page-item pe-2" :class="{'disabled': currentPage === lastPage}"><button class="page-link" @click="getProjects(currentPage + 1)">NEXT</button></li>
      </ul>
    </nav>
  </main>

</template>

<style scoped>
ul li {
  text-align: left;
}

</style>
