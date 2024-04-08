<script>
    import axios from 'axios';

    export default {
      components: {
      },
    
      name:'ProjectList',
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
    
      <main class="container">
        <h3 class="text-center fw-bold py-3">Clicca qui per vedere i miei progetti:</h3>
        
        <div class="d-flex justify-content-center mt-3">
            <div>
                <ul>
                    <li v-for="(element, index) in arrayProjects" :key="element.id">
                        <a href="#">{{element.title}}</a>
                    </li>
                </ul>

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
    