<template>
    <div class="movie-detail">
      <div class="featured-img"> 
          <img :src="movie.Poster" alt="Movie Poster" />
        </div>
        <div class="detalles">
        <h2>{{movie.Title}}</h2>
        <p>{{ movie.Year }}</p>
        <p>{{ movie.Genre }}</p>
        <p class="plot">{{ movie.Plot }}</p>
        </div>
     
      
    </div>
  </template>
  
  <script>
  import { ref, onBeforeMount } from "vue";
  import { useRoute } from "vue-router";
  
  
  export default {
    setup () {
        const movie = ref({});
         const route = useRoute();
  
         onBeforeMount(() => {
             fetch(`http://www.omdbapi.com/?apikey=fcc1eb7e&i=${route.params.id}&plot=full`)
             .then(response => response.json())
             .then(data => {
                movie.value =  data;
                console.log(data)
               
             });
        });
  
        return {
            movie
        }
    }
  }
  </script>
  
  <style lang="scss">
    
  .movie-detail{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
        
    color: white;
  
    widows: 100%;  
    h2{
        color: white;
        font-size: 35px;
        font-weight: 600;
        margin-bottom: 16px;
  
    }
  
    .featured-img{
         max-width: 100%;
         max-height: 600px;
         margin-top: 30px;
        margin-bottom: 16px;
    }
  
    .detalles{
     display: flex;
     flex-direction: column;
     align-items: center;
     margin-bottom: 50px;
     width: 40%;
  
     .plot{
      margin-top: 20px;
     }
    }
  
  
    p{
        color: #fff;
        font-size: 18px;
        line-height: 1.4;
        text-align: justify;
    }
  
    @media screen and (max-width: 1200px){
      .movie-detail{
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
        
    color: white;
  
    widows: 100%;  
  
  }
  .featured-img{
         max-width: 100%;
         max-height: 600px;
         margin-top: 30px;
        margin-bottom: 16px;
    }
  
  
    }
  
  
  
  }
  
  </style>