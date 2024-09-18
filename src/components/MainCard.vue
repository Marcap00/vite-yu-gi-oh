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
                <h5 class="card-title">Card Name: <br> {{ cardObj.name }}</h5>
                <p class="card-type">Archetype: <br> {{ cardObj.archetype }}</p>
            </div>
        </div>
    </div>

</template>

<style lang="scss" scoped></style>