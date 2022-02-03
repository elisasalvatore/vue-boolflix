<template>  
    <div class="container-cards">
        <div class="cards">
            <img :src="getMoviePoster()" alt="">

            <!-- <div class="cards-hover">
                <div class="title">Titolo: {{movie.title}}</div>
                <div class="original-title">Titolo originale: {{movie.original_title}}</div>
                <div class="language">Lingua originale: {{movie.original_language}}</div>
                <div class="vote">Voto: {{movie.vote_average}}</div>
                <div class="overview">Overflow: {{movie.overview}}</div>
            </div> -->
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
            if (this.movie.poster_path === null) {
                return `https://www.wanted.gr/wp-content/uploads/2021/11/Image-Not-Available.png`
            }
            return `https://image.tmdb.org/t/p/w200/${this.movie.poster_path}`
        }
    }
}
</script>

<style lang="scss" scoped>
.container-cards {
    margin-top: 20px;

    .cards{
        padding: 10px;

        img {
            // width: 200px;
            height: 300px;
        }
    }

    // .cards-hover {
    //     width: 200px;
    //     height: 300px;
    //     padding: 15px;
    //     color: white;
    //     background-color: black;
    //     border: 2px solid #fff;
        
    //     > div {
    //         margin: 5px 0;
    //     }
    // }
}
</style>