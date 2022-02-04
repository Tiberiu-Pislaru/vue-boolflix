<template>
    <div >

        <div class="img-container">

            <img :src="`https://image.tmdb.org/t/p/original${card.poster_path}`" alt="">
        </div>

        <div class="title">
            Titolo: 
            {{card.title}}
        </div>

        <div class="original-title">
            Titolo originale: 
            {{card.original_title}}
        </div>

        <div class="language">
            Lingua: 
            <div class="container-flag" v-if="flags.includes(card.original_language)">
                <img class="flag" accept="image/*" :src=img  :alt="`${card.original_language}`">
            </div>
            <span v-else>{{card.original_language}}</span>
        </div>

        <div class="vote">
            Voto: 
            {{card.vote_average}}
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            img:`C:/Users/TIBERIO/Desktop/Sviluppo/vue-boolflix/src/assets/${this.card.original_language}.png`
        }
    },
    props: {
        card:Object,
        flags:Array
    }
}
</script>

<style lang="scss" scoped>
.title{
    color:#fff;
}
.img-container{
    width: 100%;
    img{
        width:100%;
        object-fit: cover;
    }
}
.container-flag{
    width: 30px;
    display:inline-block;
    
    .flag{
        width: 100%;
    }
}
   
</style>