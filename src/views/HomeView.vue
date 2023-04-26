<template>
  <div class="home">
    <div class="featured-card">
        <router-link to="/movie/tt1745960">
          <video :src="'/videos/Top Gun Maverick.mp4'"
          autoplay
          loop
          class="featured-img"/>
          <div class="detail">
            <h3>Top Gun Maverick</h3>
            <p>After thirty years, Maverick is still pushing the envelope as a top naval aviator, but must confront ghosts of his past when he leads TOP GUN's elite graduates on a mission that demands the ultimate sacrifice from those chosen</p>
          </div>
        </router-link>
    </div>

    <form @submit.prevent="SearchMovies()" class="search-box">
      <input type="text" placeholder="¿Que estas buscando?" v-model="search">
      <input type="submit" value="Buscar">
    </form>

    <!-- luego de haber consumido la api procedemos a crear las cartas con 
    la informacion que nos da la apikey  -->
    <div class="movies-list">
        <div class="movie" v-for="movie in movies" :key="movie.imdbID">
            <router-link :to="/movie/ + movie.imdbID" class="movie-link">
                <div class="product-image">
                    <img :src="movie.Poster" alt="Movie Poster">
                    <div class="type">{{ movie.Type }}</div>
                  </div>
                  <div class="detail">
                      <p class="year">{{ movie.Year }}</p>
                      <h3>{{ movie.Title }}</h3>
                  </div>
            </router-link>
        </div>
    </div>
  </div>


</template>

<script>
import { ref } from 'vue';
//En este punto se esta importando la ApiKey

export default {
  setup () {
    const search = ref("")
    const movies = ref([])

    const SearchMovies = () => {
      if(search.value != ""){
        // implementacion de api con metodo fetch
        fetch(`https://www.omdbapi.com/?apikey=fcc1eb7e&s=${search.value}`)
        .then(response => response.json() )
        .then(data => {
           movies.value = data.Search;
           search.value = "";
          
        });
        
      }
    } 
    return{
      search,
      movies,
      SearchMovies
    }
  }
}
</script>

<style lang="scss">

  .home{
    .featured-card{
      position: relative;

      .featured-img {
        display: block;
        width: 100%;
        height: 600px;
        object-fit: cover;

        position: relative;
        z-index: 0;
      }

      .detail{
          position: absolute;
          left: 0;
          right: 0;
          bottom: 0;
          background-color: rgba(0,0,0,0.6);
          padding: 16px;
          z-index: 1;

          h3{
            color: #fff;
            margin-bottom: 16px;
            text-align: center;
          }

          p{
            color: #fff;
            text-align:center;
          }
      }
    }

      .search-box{
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
          padding: 20px;

          input{
            appearance: none;
            border: none;
            outline: none;
            background: none;

            &[type="text"] {
              width: 80%;
              color: #fff;
              background-color: #1A1A1A;
              font-size: 20px;
              padding: 10px 16px;
              border-radius: 8px;
              margin-bottom: 15px;
              transition: 0.4s;

              &::placeholder {
                color: #f3f3f3 ;
                font-family: sans-serif;
                text-align: center;
              }

              &:focus{
                box-shadow: 0px 3px 6px rgba(0,0,0,0.2);
              }
            }

            &[type="submit"] {
                width: 80%;
                max-width: 300px;
                background-color: #011640;
                color: white;
                padding: 16px;
                border-radius: 8px;
                font-size: 20px;
                text-transform: uppercase;
                transition: 0.4s;

                &:active {
                    background-color: #1A1A1A;
                }
            }
          }
      }


      .movies-list{
        display: flex;
        flex-wrap: wrap;
        margin: 0px 8px;
        color: white;

        .movie{
          max-width: 20%;
          height: 400px;
          flex: 1 1 20%;
          padding: 16px 8px;

          .movie-link{
            display: flex;
            flex-direction: column;
            width: 100%;

            .product-image {
              position: relative;
              display: block;

              img {
                display: block;
                width: 100%;
                height: 275px;
                object-fit: cover;
              }

              .type {
                width: 100%;
                position: absolute;
                padding: 8px 16px;
                background-color: #011640;
                color: #fff ;
                bottom: 16px;
                left: 0px;
                text-transform: capitalize;
              }
            }

            .detail{
              background-color: #1A1A1A;
              padding: 16px 8px;
              flex: 1 1 100%;
              border-radius: 0px 0px 8px 8px ;

              .year{
                color: #AAA;
                font-size: 14px ;
              }


              h3 {
                color: #fff;
                font-weight: 600;
                font-size: 18px;
              }
            }
          }
        }
      }
  }

  @media screen and (max-width: 1200px){
    .detail{
          left: 0;
          right: 0;
          bottom: 0;
          background-color: rgba(0,0,0,0.6);
          z-index: 1;

          h3{
            color: #fff;
            margin-bottom: 16px;
            text-align: center;
          }

          p{
            width: 100%;
            height: auto;
            color: #fff;
            text-align:center;
            font-size: 18px;
          }
      }

    
      .movies-list{
        display: flex;
        flex-wrap: row wrap;
        margin: 0px 8px;
        color: white;

        .movie{
          max-width: 50%;
          flex: 1 1 50%;
          padding: 16px 8px;

          .movie-link{
            display: flex;
            flex-direction: column;
            width: 100%;

            .product-image {
              position: relative;
              display: block;

              img {
                display: block;
                width: 80%;
                height: 275px;
                object-fit: cover;
              }

              .type {
                position: absolute;
                padding: 8px 16px;
                background-color: #E10813;
                color: #fff ;
                bottom: 16px;
                left: 0px;
                text-transform: capitalize;
              }
            }

            .detail{
              background-color: #1A1A1A;
              padding: 16px 8px;
              flex: 1 1 50%;
              border-radius: 0px 0px 8px 8px ;

              .year{
                color: #AAA;
                font-size: 10px ;
              }


              h3 {
                color: #fff;
                font-weight: 600;
                font-size: 10px;
              }
            }
          }
        }
      }
  }

  @media screen and (max-width: 700px){

    .home{
      .detail{
          left: 0;
          right: 0;
          bottom: 0;
          background-color: rgba(0,0,0,0.6);
          z-index: 1;

          h3{
            color: #fff;
            margin-bottom: 16px;
            text-align: center;
          }

          p{
            width: 90%;
            height: auto;
            color: #fff;
            text-align:center;
            font-size: 18px;
          }
      }

      .movies-list{
        display: flex;
        flex-wrap: wrap;
        margin: 0px 8px;
        color: white;
        .movie{
          max-width: 50%;
          height: none;
          flex: 1 1 50%;
          padding: 16px 8px;
        }
      }

    }
   
     
     
  }

  @media screen and (max-width: 500px){
    .detail{

          left: 0;
          right: 0;
          bottom: 0;
          background-color: rgba(0,0,0,0.6);
          // padding: 16px;
          z-index: 1;

          h3{
            color: #fff;
            margin-bottom: 16px;
            text-align: center;
          }

          p{
            width: 100%;
            height: auto;
            color: #fff;
            text-align:justify;
            font-size: 18px;
          }
      }

      .movies-list{
        display: flex;
        flex-wrap: wrap;
        margin: 0px 8px;
        color: white;

        .movie{
          max-width: 50%;
          flex: 1 1 50%;
          padding: 16px 8px;

          .movie-link{
            display: flex;
            flex-direction: column;
            width: 100%;

            }

          
          }
        }
      }

  

</style>
