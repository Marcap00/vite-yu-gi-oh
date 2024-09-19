<script>
/* import { store } from '../store.js' */

export default {
    data() {
        return {
            /* store */
        }
    },
    props: {
        cards: {
            type: Array,
            required: true
        }
    }
}

</script>

<template>
    <div class="banner-found-cards">
        <p>Found {{ cards.length }} Cards</p>
    </div>
</template>

<style lang="scss" scoped>
@use '../styles/partials/variables.scss' as *;

.banner-found-cards {
    background-color: $bg-banner;
    color: white;
    font-weight: 700;
    padding: 1rem;
    margin-bottom: 1rem;
}
</style>