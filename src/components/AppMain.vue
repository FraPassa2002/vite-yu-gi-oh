<script>
import SingleCard from './SingleCard.vue';
import { store } from '../store.js';


export default {
    data() {
        return {
            store
        };
    },
    components: { 
        SingleCard
    },    
}
</script>

<template>
    <main>
        <div class="container rounded p-3">
            <div class="row rounded">
                <div class="col-12 col-sm-6 col-md-3 text-center mb-3 rounded" v-for="(card, i) in store.cards" :key="i">
                    <SingleCard :card="card" />
                </div>
            </div>
        </div>
    </main>
</template>

<style lang="scss" scoped>
.container {
    background-color: rebeccapurple;

}
</style>
