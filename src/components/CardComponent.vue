<!-- <template>
    <div class="card mb-3">
      <div class="card-body">
        <h5 class="card-title">{{ project.title }}</h5>
        <p class="card-text">{{ project.content }}</p>
        <p class="card-text"><small class="text-muted">Tipologia: {{ project.type ? project.type.name : 'Nessuna' }}</small></p>
        <p class="card-text">
          <small class="text-muted">Tecnologie: 
            <span v-if="project.technologies.length > 0">
              <span v-for="technology in project.technologies" :key="technology.id">
                {{ technology.name }}
              </span>
            </span>
            <span v-else>
              Nessuna tecnologia
            </span>
          </small>
        </p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CardComponent',
    props: {
      project: {
        type: Object,
        required: true
      }
    }
  };
  </script>
  
  <style scoped>
  </style> -->
  <template>
    <div class="card mb-3">
      <div class="card-body d-flex flex-column">
        <h5 class="card-title">{{ project.title }}</h5>
        <p class="card-text">
          <span v-if="!expanded">{{ truncatedDescription }}<span v-if="isTruncated">...</span></span>
          <span v-else>{{ project.content }}</span>
          <span v-if="!expanded && isTruncated">
            <a href="#" @click.prevent="toggleExpand"> Leggi di più</a>
          </span>
          <span v-if="expanded && isTruncated">
            <a href="#" @click.prevent="toggleExpand"> Leggi di meno</a>
          </span>
        </p>
        <p class="card-text"><small class="text-muted">Tipologia: {{ project.type ? project.type.name : 'Nessuna' }}</small></p>
        <p class="card-text">
          <small class="text-muted">Tecnologie: 
            <span v-if="project.technologies.length > 0">
              <span v-for="technology in project.technologies" :key="technology.id">
                {{ technology.name }}
              </span>
            </span>
            <span v-else>
              Nessuna tecnologia
            </span>
          </small>
        </p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CardComponent',
    props: {
      project: {
        type: Object,
        required: true
      }
    },
    data() {
      return {
        expanded: false // Stato per tracciare se il testo è espanso o no
      };
    },
    computed: {
      truncatedDescription() {
        // Troncamento della descrizione a circa 2 righe basato sul numero di caratteri
        const charLimit = 100; // Limite di caratteri per troncare la descrizione
        if (this.project.content.length > charLimit) {
          return this.project.content.slice(0, charLimit);
        }
        return this.project.content;
      },
      isTruncated() {
        // Verifica se la descrizione è troncata
        const charLimit = 100;
        return this.project.content.length > charLimit;
      }
    },
    methods: {
      toggleExpand() {
        this.expanded = !this.expanded;
      }
    }
  };
  </script>
  
  <style scoped>
  .card-text a {
    color: #434343;
    text-decoration: underline;
    cursor: pointer;
  }
  .card-text a:hover {
    text-decoration: none;
  }
  </style>