<template>
    <div class="card-single">

        <div class="copertina" >

            <div class="img-container">

                <img v-if="card.poster_path!==null" :src="`https://image.tmdb.org/t/p/w185${card.poster_path}`" alt="">
                <img  class="placeholder" v-else src="@/assets/placeholder.jpg" alt="placeholder">
            </div>
        </div>

        <div class="content-card ">

            <div v-if="card.title!==undefined" class="title mg">
                Titolo: 
                {{card.title}}
            </div>
            <div v-else class="title">
                Titolo: 
                {{card.name}}
            </div>

            <div v-if="card.original_title!==undefined" class="original-title mg-x">
                Titolo originale: 
                {{card.original_title}}
            </div>
            <div v-else class="original-title mg-x">
                Titolo originale: 
                {{card.original_name}}
            </div>

            <div class="language mg-x">
                Lingua: 
                <div class="container-flag" v-if="flags.includes(card.original_language)">
                    <img class="flag" accept="image/*" :src=img  :alt="`${card.original_language}`">
                </div>
                <span v-else>{{card.original_language}}</span>
            </div>

            <div class="vote mg-x">
                Voto: 
                <span v-for="el in starConvert" :key="el">
                    <star-value/>
                </span>
            </div>
        </div>
    </div>
</template>

<script>
import StarValue from "./StarValue.vue"
export default {
    components:{
        StarValue
    },
    data(){
        return{
            img:`/flags/${this.card.original_language}.png`
        }
    },
    props: {
        card:Object,
        flags:Array
    },
    computed:{
        starConvert(){
            return Math.round(this.card.vote_average/2)
        }
    }
    
}
</script>

<style lang="scss" scoped>

@import '@/style/main.scss';

.card-single{
    
    width:185px;
    color: #fff;
    position: relative;
    
   
   
    .copertina{
        display: block;
       
        .img-container{
            min-width: 100%;
            min-height: 100%;
        }
        img{
            max-width: 100%;
            max-height: 100%;
            object-fit: cover;
        }
        
    }

    .content-card{
        display: none;
        height: 100%;
        width: 100%;
        padding: 15px;
        background: rgba(0, 0, 0, 0.8);
        
        .title{
            color:#fff;
        }
        .container-flag{
            width: 30px;
            display:inline-block;
        } 
        .flag{
            width: 100%;
        }

    }

    &:hover .content-card{
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        text-align: center;
        position: absolute;
        top: 0;
        left: 0;
        
    }
}
   
</style>