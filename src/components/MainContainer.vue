<template>
    <main>
        <MovieCard v-for="movie in movies" :key="movie.id" :movie="movie"/>
    </main>
</template>

<script>
import MovieCard from './MovieCard.vue'

export default {
    components: {
        MovieCard,
    },
    props: {
        movies: Array
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