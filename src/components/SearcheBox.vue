<template>
    <header class="pd-all">
        <div class="left">
            <div class="logo">
                BOOLFLIX
            </div>
        </div>
        <div class="right">

            <input type="text" v-model="inputSearch">
            <button @click="$emit('search', inputSearch)">&#128270;</button>
        </div>
    </header>
</template>

<script>
export default {
    data(){
        return{
            inputSearch: '',
        }
    }
}
</script>


<style lang="scss" scoped>
@import "@/style/main.scss";
header{
    position: sticky;
    display: flex;
    align-items: center;
    top: 0;
    left: 15px;
    display: flex;
    justify-content: space-between;
    

    .left {
        
        .logo {
            font-size:30px;
            color: rgb(80, 80, 80);
        }
    }
    
    .right{

        button{
            all:unset;
            cursor: pointer;
            font-size: 30px;
        }
    }
}
</style>