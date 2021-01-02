<template>
    <div class="movies-list">
        <div class="movie-container" v-for="movie in movies" :key="movie.imdbID">
            <router-link :to="{ name: 'MovieDetail', params: { id: movie.imdbID }}">
            <div class="movie card">
                <div class="movie-poster">
                    <span v-if="movie.Poster === 'N/A'">
                        <img src="../assets/placeholder.jpg" alt="">
                    </span>
                    <span v-else>
                        <img :src="movie.Poster" alt="">
                    </span>
                    <div class="type">{{movie.Type}}</div>
                </div>
                
                <div class="movie-info">
                    <p class="name">{{movie.Title}}</p>
                    <small>{{movie.Year}}</small>
                </div>
            </div>
        </router-link>
        </div>
    </div>
</template>

<script>
export default {
    props: ['movies'],
}
</script>

<style>
    a{
        text-decoration: none;
    }
    .movies-list{
        width: 80%;
        margin: 0 auto;
        z-index: 1;
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 20px;
        margin: 50px auto; 
        align-items: flex-start;
    }
    .card{
        background: white;
        border-radius: 5px;
        padding: 10px;
        display: flex;
        flex-direction: column;
    }
    .movie{
        min-height: 300px;
        width: 100%;
        box-shadow: 0 0 10px 5px rgba(0,0,0,0.08);
    }
    .movie-poster{
        flex: 2;
        width: 100%;
        height: 100%;
        position: relative;
    }

    .movie-poster img{
        border-radius: 5px;
        width: 100%;
        height: 100%;
    }
    .movie-poster .type{
        padding: 6px 10px;
        font-size: 12px;
        color: #00ff2a;
        font-weight: bold;
        border-radius: 10px;
        position: absolute;
        top: 10px;
        right: 10px;
        z-index: 1;
        background-color: rgb(255, 255, 255);
    }
    .movie .movie-info{
        flex: 1;
    }
    .movie .name{
        margin: 15px 0 0 0;
        color: #00ff2a;
        font-size: 18px;
        font-weight: bold;
        letter-spacing: 2px;
        width: 170px;
        white-space: nowrap;
        text-overflow: ellipsis;
        overflow: hidden;
    }
    .movie small{
        font-size: 13px;
        color: rgba(0,0,0,0.4);
    }

@media (max-width: 400px){
    .movie .name{
        width: 260px;
    }
}
</style>