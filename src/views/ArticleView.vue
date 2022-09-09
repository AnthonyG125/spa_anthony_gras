<template>
  <div class="article">
    <div class="page-content p-5" id="content">

      <div class="content">
        <h1>Detail de l'article</h1>
        <div>
            <b-card
                tag="article"
            >
              <b-card-header>
                <span class="avatar-number"><h3>{{ article.title[0].toUpperCase()}}</h3></span><b-card-title>{{ article.title }}</b-card-title>
              </b-card-header>

              <b-card-text>{{article.body}}</b-card-text>
              <b-card-footer>
                <h3>Commentaire</h3>
                <div v-for="comments in commentaire">
                  <h5>{{ comments.name}}</h5>

                  <a :href="`mailto:${comments.email}`">{{comments.email}}</a>

                  <p>{{ comments.body}}</p>
                  <hr>
                </div>
              </b-card-footer>
            </b-card>
          </div>
      </div>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import Article from '@/components/Article.vue'
import axios from 'axios'

export default {
  name: 'ArticleView',
  components: {
    Article
  },
  data() {
    return {
      id: 1,
      article: [],
      commentaire: []
    }
  },


  mounted () {
    //----- Recupération des informations de l'article -----/
    axios
        .get('https://jsonplaceholder.typicode.com/posts/' + this.$route.params.id)
        .then(response => (this.article = response.data))
    //----- Recupération des commentaire de l'article -----/
    axios.get('https://jsonplaceholder.typicode.com/posts/' + this.$route.params.id + '/comments')
        .then(res => (this.commentaire = res.data))
  },

}
</script>
