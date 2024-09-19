<script>
import axios from 'axios'

export default {
    data() {
        return {
            urlCardArchetypes: `https://db.ygoprodeck.com/api/v7/archetypes.php`,
            archetypes: [],
            selectedArchetype: ''
        }
    },
    methods: {
        getArchetypesList() {
            axios.get(this.urlCardArchetypes)
                .then(response => {
                    console.log('Risposta della chiamata:', response.data);
                    this.archetypes = response.data;

                    console.log('Array di archetipi popolato:', this.archetypes);
                })
                .catch(error => {
                    console.log(error);
                })
        },
        emitArchetype(archetype) {
            this.selectedArchetype = archetype
            console.log('Archetipo selezionato 1:', this.selectedArchetype);
            this.$emit('archetype', this.selectedArchetype)

        }


    },
    created() {
        this.getArchetypesList()
    },
}

</script>

<template>
    <select name="type-cards" id="type-cards">
        <option selected value="all">All</option>
        <option v-for="(archetype, index) in archetypes" value="alien" :key="index"
            @click="emitArchetype(archetype.archetype_name)">
            {{ archetype.archetype_name }}
        </option>
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