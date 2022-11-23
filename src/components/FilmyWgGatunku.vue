<template>
<div v-for="(name,index) in gen" :key="index">
    <p> {{name}} </p>
    <ol>
        <li v-for="mov,index in checkgen(movs,name) " :key="index">
            {{ mov.title}}
        </li>
    </ol>
</div>
</template>
<script>
import genres from "E:/VueProject/hello-world/wikipedia-movie-data-master/wikipedia-movie-data-master/genres.json"
import movies from "E:/VueProject/hello-world/wikipedia-movie-data-master/wikipedia-movie-data-master/movies.json"
import _ from "underscore"
export default {
    data(){
        return{
            movs : movies,
            gen : genres,
        }
    },
    methods: {
        checkgen(m,na) {
           return _.filter(m,(g)=>{ return g.genres.includes(na)})
        }

    }
}

</script>