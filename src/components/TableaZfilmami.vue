<template>
    <div>
        <table>
            <tr>
                <th>Title</th>
                <th>Production Year</th>
                <th>Cast</th>
                <th>Genres</th>
            </tr>
                <tr v-for="mov,index in filtedMovies(movs) " :key="index">
                    <td>{{mov.title}}</td>
                    <td>{{mov.year}}</td>
                    <td>{{mov.cast}}</td>
                    <td>{{mov.genres}}</td>
                </tr>
        </table>
      <button @click="Dodaj">Zobacz więcej {{number}}</button>
    </div>
  </template>
  
  <script>
  import movies from "E:/VueProject/hello-world/wikipedia-movie-data-master/wikipedia-movie-data-master/movies.json"
  import _ from "underscore"
  export default {
    data(){
        return{
            movs : movies,
            number :10
        }
    },
    methods: {
        Dodaj() {
            this.number += 10;
        },
        filtedMovies(m) {
            if(!this.attr[0] && !this.attr[2] && !this.attr[3] && !this.attr[4] && !this.attr[1]){
                return []
            }
            else{
            return _.filter(m, (movie) => {
                if((this.attr[2] ? _.find(movie.cast,(c)=>c.toLowerCase().includes(this.attr[2])) : true) &&
                (this.attr[0] ? movie.title.toLowerCase().includes(this.attr[0] ) : true) &&
                (this.attr[3] ? _.find(movie.genres,(c)=>c.toLowerCase().includes(this.attr[3])) : true) &&
                ((this.attr[1] ? movie.year > this.attr[1]-1 : true) && (this.attr[4] ? movie.year < this.attr[4]+1 : true)))
                {
                return movie
            }}).slice(0, this.number)
            }
        }
    },
    props: {
        attr : [],
    }
  }
  </script>
  