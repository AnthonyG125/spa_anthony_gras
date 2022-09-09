<template>
  <div class="home">
    <div class="page-content p-5" id="content">

      <div class="content">
        <h1>Liste des articles</h1>
        <div class="row justify-content-center">
          <!------- Parcours de la liste articles ----->
          <div v-for="article in articles" class="col-4 col-md-4 col-sm-4">
            <b-card

                img-top
                tag="article"
                style="height: 20rem"
                class="mb-2 col-sm"
            >
              <span class="avatar-number"><h3>{{ article.title[0].toUpperCase()}}</h3></span><b-card-title>{{ article.title }}</b-card-title>
              <b-card-text>
                {{ article.body }}
              </b-card-text>

              <!---- Redirection à la vue article avec l'id en parametre de l'url ----->
              <b-button :to="{ name:'article', params: {id : article.id} }" variant="primary">Detail</b-button>
            </b-card>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>

.avatar-number {
  display: inline-block;
  width: 3rem;
  height: 3rem;
  line-height: 30px;
  padding: 2px;
  text-align: center;
  border-radius: 50%;
  background: #aaaaaa;
}
#content.active {
  width: 100%;
  margin: 0;
}

.card-title {
  display : inline;
  margin : 5px;
}
</style>


<script>
// @ is an alias to /src
import Home from '@/components/Home.vue'
import axios from 'axios'

export default {
  name: 'HomeView',
  components: {
    Home
  },
  props: {
    id : Number,
  },
  data() {
    return {
      articles: [],
    }
  },
  mounted () {
    //---- Récupération des articles ------//
    axios
        .get('https://jsonplaceholder.typicode.com/posts')
        .then(response => (this.articles = response.data))
  }
}
</script>
