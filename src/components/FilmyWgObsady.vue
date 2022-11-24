<template>
    <button class="btn btn-primary mb-3" @click="hidden">Pokaż/schowaj liste z obsadom</button>
    <div v-show="hidde">
      <div v-for="(name,index) in getAllActors(movs)" :key="index">
          <p> {{name}} </p>
          <ol>
              <li v-for="(mov,index) in checkact(movs, name) " :key="index">
                  {{mov.title}}
              </li>
          </ol>
      </div>
    </div>
</template>
<script>
import movies from "../../public/movies.json"
import _ from "underscore"
export default {
    data(){
        return{
            movs : _.shuffle(movies?.slice(-101, -1)),
            hidde : false,
        }
    },
    methods: {
        getAllActors(movies) {
            let actors = [];
            movies.forEach(movie => {
                actors = actors.concat(Object.values(movie.cast))
            });
            return [...new Set(actors)]
        },
        checkact(movies, actor) {
           return movies.filter(movie=> movie.cast.includes(actor))
        },
        hidden(){
            this.hidde = !this.hidde
        }

    }
}

</script>