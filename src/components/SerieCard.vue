<template>  
    <div class="container-cards">
        <div class="card">
            <img :src="getSeriePoster()" alt="">

            <div class="card-hover" >
                <div class="name"><b>Titolo:</b>{{serie.name}}</div>
                <div class="original-name"><b>Titolo originale:</b>{{serie.name}}</div>
                
                <div class="language-flags">
                    <b>Lingua originale:</b>
                    <img :src="getFlags(serie.original_language)" alt="Non specificata">
                    <!-- ciò che viene scritto nell'attributo 'alt' verrà visualizzato quando l'immagine della bandiera non sarà presente nella cartella 'flags' -->
                </div>

                <div class="vote"><b>Voto:</b> {{serie.vote_average}}</div>
                <div class="overview"><b>Overflow:</b> {{serie.overview}}</div> 
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: { 
            serie: Object,
        },
        methods: {
            getSeriePoster() {
                if (this.serie.poster_path === null) {
                    return `https://www.wanted.gr/wp-content/uploads/2021/11/Image-Not-Available.png`
                }
                return `https://image.tmdb.org/t/p/w200/${this.serie.poster_path}` 
            },
            getFlags(language) {
                return "/flags/" + language + ".png"
            }
        },
    }
</script>

<style lang="scss" scoped>
    @import './style/cards.scss';
</style> 