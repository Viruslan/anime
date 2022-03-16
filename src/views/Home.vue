<template>
    <header>
        <h1>
            <Strong>ANIME</Strong>list
        </h1>
        <form class="search-box" @submit.prevent="HandleSearch">
            <input
                type="search"
                class="search-field"
                placeholder="Введи название аниме..."
                required
                v-model="search_query"
            />
        </form>
    </header>
    <main>
        <div class="cards">
            <Card v-for="anime in animelist" :key="anime.id" :anime="anime" />
        </div>
    </main>
</template>

<script>
import { ref } from 'vue'
import Card from '@/components/Card.vue'



export default {
    setup() {
        const search_query = ref("");
        const animelist = ref([]);

        const HandleSearch = async () => {
            animelist.value = await fetch(`https://shikimori.one/api/animes/search?q=${search_query.value}`)
                .then(res => res.json());


            console.log(animelist.value);
        }
        return { search_query, animelist, HandleSearch };
    },
    components: { Card }
}


</script>

<style lang="scss">
a {
    text-decoration: none;
}
header {
    padding-top: 50px;
    padding-bottom: 50px;

    h1 {
        color: #888;
        font-size: 350%;
        font-weight: 400;
        text-align: center;
        text-transform: uppercase;
        margin: 30px;

        strong {
            color: black;
        }
    }
    :hover {
        color: black;
    }
    .search-box {
        display: flex;
        justify-content: center;
        padding-left: 30px;
        padding-right: 30px;

        .search-field {
            appearance: none;
            background: none;
            border: none;
            outline: none;

            background-color: #f3f3f3;
            box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.15);

            display: block;
            width: 100%;
            max-width: 600px;
            padding: 15px;
            border-radius: 8px;

            color: #313131;
            font-size: 20px;

            transition: 0.4s;

            &::placeholder {
                color: #aaa;
            }

            &:focus,
            &:valid {
                color: #fff;
                background-color: #313131;
                box-shadow: 0px 0px 0px rgba(0, 0, 0, 0.15);
            }
        }
    }
}
main {
    max-width: 1200px;
    margin: 0 auto;
    padding-left: 10px;
    padding-right: 10px;
@media screen and(min-width: 1200px) {
    padding-left: 15px;
    padding-right: 15px;
}
    .cards {
        display: flex;
       
        flex-wrap: wrap;
        margin: 0 -8px;
    }
}
</style>