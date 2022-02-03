<template>
    <div >

        <div class="title">
            Titolo: {{card.title}}
        </div>

        <div class="original-title">
            Titolo originale: {{card.original_title}}
        </div>

        <div class="language">
            Lingua: {{card.original_language}}
        </div>

        <div class="vote">
            Voto: {{card.vote_average}}
        </div>
        <!-- <img :src="`https://image.tmdb.org/t/p/original${card.poster_path}`" alt=""> -->
    </div>
</template>

<script>
export default {
    props: {
        card:Object
    }
}
</script>

<style lang="scss" scoped>
.titolo{}
   
</style>