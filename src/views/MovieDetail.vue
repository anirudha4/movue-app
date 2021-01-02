<template>
    <div v-if="!loading" class="container">
        <router-link class="back" to="/">Back</router-link>
        <div class="title">
            <h2>{{movie.Title}}</h2>
            <p class="rating">
                IMDB RATING - {{movie.imdbRating}}
            </p>
        </div>
        <div class="movie-details">
            <div class="poster">
                <img :src="movie.Poster" alt="">
            </div>
            <div class="movie-info">
                <div class="block">
                    <p class="field">Directed By - </p>
                    <p class="value">{{movie.Director}}</p>
                </div>
                <div class="block">
                    <p class="field">Cast - </p>
                    <p class="value">{{movie.Actors}}</p>
                </div>
                <div class="block">
                    <p class="field">Plot - </p>
                    <p class="value">{{movie.Plot}}</p>
                </div>
                <div class="block">
                    <p class="field">Written By - </p>
                    <p class="value">{{movie.Writer}}</p>
                </div>
                <div class="block">
                    <p class="field">Production - </p>
                    <p class="value">{{movie.Production}}</p>
                </div>
                <div class="block">
                    <p class="field">BoxOffice Collection - </p>
                    <p class="value">{{movie.BoxOffice}}</p>
                </div>
                <div class="block">
                    <p class="field">Genre - </p>
                    <p class="value">{{movie.Genre}}</p>
                </div>
                <div class="block">
                    <p class="field">Awards - </p>
                    <p class="value">{{movie.Awards}}</p>
                </div>
                <div class="block">
                    <p class="field">Runtime - </p>
                    <p class="value">{{movie.Runtime}}</p>
                </div>

            </div>
        </div>
    </div>
    <div v-else class="loading">
        <div class="circle"></div>
        <div class="circle"></div>
        <div class="circle"></div>
                        
    </div>
</template>

<script>
import { onBeforeMount, onMounted, ref } from 'vue'
import {useRoute} from 'vue-router'
import env from '../env'
export default {
    setup(props){
        const route = useRoute()
        const loading = ref(true)
        const movie = ref({})
        onMounted( async () => {
            const temp = await fetch(`https://omdbapi.com/?apikey=${env.api_key}&i=${route.params.id}&plot=full`)
            movie.value = await temp.json()
            loading.value = false
        })
        return { movie, loading }
    }

}
</script>

<style>
    .container{
        width: 80%;
        position: relative;
        margin: 0 auto;
    }
    .back{
        position: absolute;
        top: 0px;
        right: 0px;
        padding: 10px 12px;
        border-radius: 4px;
        text-decoration: none;
        font-weight: bold;
        font-size: 18px;
        color: rgb(0, 255, 0);
    }
    .title{
        margin: 30px 0;
    }
    .title h2{
        letter-spacing: 1.4px;
        font-size: 2em;
        color: #333;
        margin-bottom: 10px;
    }
    .title  p.rating{
        font-size: 1.3em;
        font-weight: bold;
        color: #555;
    }
    .movie-details{
        display: grid;
        grid-template-columns: auto 1fr;
        gap: 30px;
        align-items: flex-start;
    }
    .poster{
        width: 100%;
        height: 100%;
    }
    .movie-info{

    }
    .movie-info .block{
        display: flex;
        justify-content: flex-start;
        margin: 10px 0;
        font-size: 1.1em;
        color: #555;
        font-weight: bold;
    }
    .block .value{
        flex: 1;
    }
    .loading{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        display: flex;
    }
    .loading .circle{
        border-radius: 5px;
        width: 20px;
        height: 20px;
        background: rgb(0, 255, 0);
        margin: 0 10px;
        animation: loading 1s infinite alternate forwards;
    }
    @keyframes loading {
        from{
            margin: 0;
        }
        to{
            margin: 10px;
        }
    }

    @media (max-width: 700px) {
        .movie-details{
            grid-template-columns: 1fr;
        }
        .title{
            text-align: center;
        }
        .poster{
            text-align: center;
        }
    }
</style>