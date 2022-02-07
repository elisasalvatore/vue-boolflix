<template>  
    <div class="container-cards">
        <div class="card">
            <img :src="getMoviePoster()" alt="">

            <div class="card-hover" >
                <div class="title"><b>Titolo:</b> {{movie.title}}</div>
                <div class="original-title"><b>Titolo originale:</b> {{movie.original_title}}</div>
                <div class="language"><b>Lingua originale:</b>
                    <img :src="require(`../../public/flags/${movie.original_language}.png`)">
                </div>
                <div class="vote"><b>Voto:</b> {{movie.vote_average}}</div>
                <div class="overview"><b>Overflow:</b> {{movie.overview}}</div> 
            </div>
        </div>

    </div>
</template>

<script>
export default {
    props: { 
        movie: Object,
    },
    methods: {
        getMoviePoster() {
            if (this.movie.poster_path === null) {
                return `https://www.wanted.gr/wp-content/uploads/2021/11/Image-Not-Available.png`
            }
            return `https://image.tmdb.org/t/p/w200/${this.movie.poster_path}` 
        },
    }
}
</script>

<style lang="scss" scoped>
@import './style/cards.scss';
</style>