<template>  
    <div class="container-cards">
        <div class="cards">
            <img :src="getMoviePoster()" alt="">
            <!-- <div class="title">{{movie.original_title}}</div>  NELL'HOVER-->
        </div>
    </div>
</template>

<script>
export default {
    props: { 
        movie: Object
    },
    methods: {
        getMoviePoster() {
            return `https://image.tmdb.org/t/p/w200/${this.movie.poster_path}`
        }
    }
}
</script>

<style lang="scss" scoped>
.container-cards {
    margin-top: 20px;
    
    .cards {
    
    padding: 10px;

    img {
        // width: 200px;
        height: 300px;
    }
}
}
</style>