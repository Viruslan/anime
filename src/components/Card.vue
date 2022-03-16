<template>
    <div class="card">
        <a :href="'https://shikimori.one/'+anime.url" target="_blank">
            <img :src="'https://shikimori.one/'+anime.image.original" >
            <h3>{{anime.russian}}</h3>
        </a>
    </div>
</template>

<script>
export default {
    props: ['anime']
}
</script>

<style lang="scss" scoped>
.card{
    width: 237px;
    
    
    padding: 0px 8px;
    margin-bottom: 16px;

    img{
        width: 100%;
        height: 300px;
        border-radius: 16px;
        box-shadow: 0px 4px 8px rgba(0, 0, 0 , 0.15);
        transition: 0.4s;
    }

    h3{
        padding: 16px;
        color: #313131;
    }
    &:hover{
        img{
            transform: scale(1.05);
        }
        h3{
            color: #24c444;
            transition: 0.4s;
        }
    }

}
</style>