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
            <span  v-if="flags.includes(card.original_language)">
                <img class="flag" :src="`@/assets/flag/${card.original_language}.png`"  :alt="`${card.original_language}`">
            </span>
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
    .flag{
        width:36px;
        height:27px;
    }
}
   
</style>