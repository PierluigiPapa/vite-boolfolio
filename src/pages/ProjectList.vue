<script>

import axios from 'axios';
import AppProject from '../components/AppProject.vue'
import {store} from '../store.js'


export default {
  
  name:'ProjectList',
  components: {
    AppProject
  },
  data(){
    return{
      arrayProjects: [],
      currentPage: '',
      lastPage: '',
      store
      }
    },
    
    methods: {
      getProjects(projectApiPage){
        axios.get(`${store.apiBaseUrl}/api/test`,
        {
          params: {
            page: projectApiPage
          }
        }
      )
      .then(res => {
        console.log(res.data.projects.data)
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

<main class="container">
  <h1 class="text-center fw-bold py-3">Clicca qui per vedere i miei progetti:</h1>
  
  <div class="d-flex justify-content-center mt-3">
    <div>

      <AppProject v-for="(element, index) in arrayProjects" 
      :key="element.id"
      :title="element.title"
      :slug="element.slug"
      :content="element.content"
      :type="element.type ? element.type.name : ''"
      :technologies="element.technologies"
      :image= "element.cover"/>

      
      <nav aria-label="Page navigation example">
        <ul class="pagination justify-content-center">
          <li class="page-item pe-2" :class="{'disabled': currentPage === 1}"><button class="page-link" @click="getProjects(currentPage - 1)">PREV</button></li>
          <li class="page-item pe-2" v-for="(element,index) in lastPage" :key="index"><button class="page-link" @click="getProjects(element)">{{ element }}</button></li>
          <li class="page-item pe-2" :class="{'disabled': currentPage === lastPage}"><button class="page-link" @click="getProjects(currentPage + 1)">NEXT</button></li>
        </ul>
      </nav>
    </div>
  </div>
</main>
    
</template>

<style scoped>
ul li {
  text-align: left;
}
</style>
    