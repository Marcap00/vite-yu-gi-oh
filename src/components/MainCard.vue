<script>
export default {
    data() {
        return {

        }
    },
    props: {
        cardObj: {
            type: Object,
            required: true
        }
    }
}

</script>

<template>
    <div class="col">
        <div class="card">
            <img :src="cardObj.card_images[0].image_url" class="card-img-top" alt="Card Image">
            <div class="card-body">
                <ul>
                    <li class="card-name mb-1">
                        Card Name:
                        <br>
                        <h5>{{ cardObj.name }}</h5>
                    </li>
                    <li v-if="cardObj.archetype" class="card-type">
                        Archetype:
                        <br>
                        <h5>{{ cardObj.archetype }}</h5>
                    </li>
                </ul>
            </div>
        </div>
    </div>

</template>

<style lang="scss" scoped>
@use '../styles/partials/variables.scss' as *;

.card {
    margin-bottom: 1rem;
}

.card-body {
    background-color: $bg-main;

    min-height: 120px;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 10px;
    text-align: center;

    li {
        font-weight: 600;
        font-size: 13px;

        h5 {
            font-size: 13px;
            font-weight: 700;
            color: #fff;
        }
    }
}
</style>