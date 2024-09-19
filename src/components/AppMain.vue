<script>
import axios from 'axios'
/* import { store } from '../store.js' */
import BasicLoader from './BasicLoader.vue'
import MainSelect from './MainSelectType.vue'
import MainBannerFounds from './MainBannerFounds.vue';
import MainCard from './MainCard.vue'


export default {
    data() {
        return {
            urlCardInfo: `https://db.ygoprodeck.com/api/v7/cardinfo.php`,
            cards: [],
            archetype: '',
            /* store */


        }
    },
    methods: {
        getCardsInfo(query) {
            axios.get(this.urlCardInfo, {
                params: {
                    num: 100,
                    offset: 0,
                    archetype: query
                }
            })

                .then(response => {
                    console.log(response.data.data);
                    this.cards = response.data.data;
                    console.log(this.cards);
                })
                .catch(error => {
                    console.log(error);
                })
        },
        getArchetype(archetype) {
            this.archetype = archetype
            console.log('Archetipo selezionato 2:', this.archetype);
            this.getCardsInfo(this.archetype)
        }
    },
    components: {
        BasicLoader,
        MainSelect,
        MainBannerFounds,
        MainCard,
    },
    created() {
        /* setTimeout(this.getCardsInfo, 5000) */
        this.getCardsInfo()
    }

}

</script>

<template>
    <main>
        <BasicLoader v-if="!this.cards.length" />
        <div v-else class="container">
            <MainSelect @archetype="getArchetype" />
            <div class="wrapper">
                <!-- <MainBannerFounds /> -->
                <MainBannerFounds :cards="this.cards" />
                <!-- Banner found cards -->
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
        /* padding-top: 3rem; */

        .wrapper {
            background-color: #fff;
            width: 100%;
            min-height: 100vh;
            padding: 1rem;
        }
    }

}
</style>