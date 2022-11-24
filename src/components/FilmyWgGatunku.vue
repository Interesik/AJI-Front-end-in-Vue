<template>
<button class="btn btn-primary mb-3" @click="hidden">Pokaż/schowaj liste z gatunkami</button>
  <div v-if="hidde">
    <div v-for="(name,index) in gen" :key="index">
        <p> {{name}} </p>
        <ol>
            <li v-for="(mov,index) in checkgen(movs,name) " :key="index">
                {{mov.title}}
            </li>
        </ol>
    </div>
  </div>
</template>
<script>
import genres from "../../public/genres.json"
import movies from "../../public/movies.json"
import _ from "underscore"
export default {
    data(){
        return{
            movs : _.shuffle(movies?.slice(-101, -1)),
            gen : genres,
            hidde : false,
        }
    },
    methods: {
        checkgen(m,na) {
           return _.filter(m,(g)=>{ return g.genres.includes(na)})
        },
        hidden(){
            this.hidde = !this.hidde
        }

    }
}

</script>