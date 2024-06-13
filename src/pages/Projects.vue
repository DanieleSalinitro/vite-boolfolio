<!-- <template>
    <div class="container">
      <h1>Progetti</h1>
      <div v-if="error" class="alert alert-danger">{{ error }}</div>
      <div class="row">
        <div class="col-md-4" v-for="project in projects" :key="project.id">
          <CardComponent :project="project" />
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import CardComponent from '../components/CardComponent.vue';
  
  export default {
    name: 'Projects',
    components: {
      CardComponent
    },
    data() {
      return {
        projects: [], 
        error: ''
      };
    },
    created() {
      axios.get('http://localhost:8000/api/projects')
        .then(response => {
          this.projects = response.data;
          console.log(response.data);
        })
        .catch(error => {
          console.error('Error fetching projects:', error);
          this.error = 'Errore nel caricamento dei progetti';
        });
    }
  };
  </script>
  
  <style scoped>

  </style> -->
  <template>
    <div class="container p-4">  
      <h1>Progetti</h1>
      <div class="row row-cols-1 row-cols-md-3 g-4">
        <div class="col" v-for="project in projects" :key="project.id">
          <CardComponent :project="project" />
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import CardComponent from '../components/CardComponent.vue';
  
  export default {
    name: 'Projects',
    components: {
      CardComponent
    },
    data() {
      return {
        projects: []
      };
    },
    created() {
      axios.get('http://localhost:8000/api/projects')
        .then(response => {
          this.projects = response.data;
          console.log(response.data);
        })
        .catch(error => {
          console.error('Error fetching projects:', error);
        });
    }
  };
  </script>
  
  <style scoped>
  /* Aggiungi eventuali stili personalizzati qui */
  .card {
    height: 100%;
  }
  .card-text {
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
  }
  </style>