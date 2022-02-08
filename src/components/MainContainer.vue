<template>
    <main>
        <div class="category">SERIE TV</div>
        <div class="series-container">
            <SerieCard v-for="serie in series" :key="serie.id" :serie="serie" />
        </div>

        <div class="category">FILM</div>
        <div class="movies-container">
            <MovieCard v-for="movie in movies" :key="movie.id" :movie="movie" />
        </div>
    </main>
</template>

<script>
import MovieCard from './MovieCard.vue'
import SerieCard from './SerieCard.vue'

export default {
    components: {
        MovieCard,
        SerieCard,
    },
    props: {
        movies: Array,
        series: Array,
    }
}
</script>

<style lang="scss" scoped>
main {
    background-color: #333;

    .category {
        text-align: center;
        padding: 25px 0;
        font-size: 25px;
        font-weight: 500;
        color: #fff;
    }
    .movies-container,
    .series-container {
        display: flex;
        flex-wrap:wrap; 
        justify-content: center;        
    }
}
</style>