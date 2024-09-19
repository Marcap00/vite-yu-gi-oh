<script>
export default {
    data() {
        return {

        }
    },
}

</script>

<template>
    <select name="type-cards" id="type-cards">
        <option selected value="all">All</option>
        <option value="alien">Alien</option>
        <option value="Infernoble Arms">Infernoble Arms</option>

    </select>
</template>

<style lang="scss" scoped>
select {
    margin: 1.5rem .5rem;
    width: 150px;
    padding: .5rem;
    background-color: #fff;
    border-radius: 5px;
    border: 1px solid #fff;
    font-size: 15px;
}
</style>