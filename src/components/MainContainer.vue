<template>
    <main>
        <MovieCard v-for="movie in movies" :key="movie.id" :movie="movie" />
        <SerieCard v-for="serie in series" :key="serie.id" :serie="serie" />
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
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    background-color: #333;
}
</style>