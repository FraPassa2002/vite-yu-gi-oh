<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';
import { store } from './store.js';

export default {
    data() {
        return {
            store
        };
    },
    components: {
        AppHeader,
        AppMain,
        AppFooter
    },
    methods: {

    },
    created() {
        axios
            .get(this.store.baseUrl)
            .then((response) => {
                // console.log(response);
                this.store.cards = response.data.data;
                console.log(this.store.cards);

            });
        
        console.log(this.store);
    },
}
</script>

<template>
    <AppHeader />
    <AppMain />
    <AppFooter />
</template>

<style lang="scss">
@use "assets/scss/main" as *;
</style>
