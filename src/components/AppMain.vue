<script>
import MainCard from './MainCard.vue'
import BasicLoader from './BasicLoader.vue'
import axios from 'axios'

export default {
    data() {
        return {
            urlCardInfo: `https://db.ygoprodeck.com/api/v7/cardinfo.php?num=200&offset=0`,
            cards: [],
            maxLength: 200,

        }
    },
    methods: {
        getCardsInfo() {
            axios.get(this.urlCardInfo)
                .then(response => {
                    console.log(response.data.data);
                    this.cards = response.data.data;
                    console.log(this.cards);
                })
                .catch(error => {
                    console.log(error);
                })
        }
    },
    components: {
        MainCard,
        BasicLoader
    },
    created() {
        setTimeout(this.getCardsInfo, 5000)
    }

}

</script>

<template>
    <main>
        <BasicLoader v-if="this.cards.length !== maxLength" />
        <div v-else class="container">
            <div class="wrapper">
                <div class="banner-found-cards">
                    <p>Found {{ this.cards.length }} Cards</p>
                </div>
                <div class="row row-cols">
                    <MainCard v-for="card in cards" :key="card.id" :cardObj="card" />
                </div>
            </div>
        </div>
    </main>

</template>

<style lang="scss" scoped>
@use '../styles/partials/variables.scss' as *;

main {
    background-color: $bg-main;
    min-height: 100vh;

    .container {
        padding-top: 3rem;

        .wrapper {
            background-color: #fff;
            width: 100%;
            min-height: 100vh;
            padding: 1rem;

            .banner-found-cards {
                background-color: #212429;
                color: white;
                font-weight: 700;
                padding: 1rem;
                margin-bottom: 1rem;
            }
        }
    }

}
</style>