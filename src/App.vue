<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'

export default {
    data() {
        return {

        }
    },
    components: {
        AppHeader,
        AppMain
    }
}

</script>

<template>
    <div>
        <AppHeader />
        <AppMain />
    </div>

</template>

<style lang="scss">
@use './styles/general.scss' as *;
</style>
