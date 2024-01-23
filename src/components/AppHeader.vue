<script>
import axios from 'axios';
import { store } from '../store.js';


export default {
    data() {
        return {
            searchArchetype:'',
            store,  
        };
    },
    methods: {
        handleFormSubmit() {
            if(this.searchArchetype.length > 0) {
                this.getDataFromApi();
            }
            else {
                this.getDataFromApi(); 
            }
        },
        getDataFromApi() {
            let queryString = '';

            if(this.searchArchetype.length > 0) {
                queryString = '?archetype=' + this.searchArchetype;
            }

            const fullUrl = this.store.baseUrl + queryString;
            console.log(fullUrl);

            axios
                .get(fullUrl)
                .then((response) => {
                    // console.log(response);
                    this.store.cards = response.data.data;
                    console.log(this.store.cards);

                });
        }
    },
}
</script>

<template>
    <header class="pb-4">
        <div class="container pt-3">
            <div class="row">
                <div class="col w-50">
                    <img src="../../Yugioh.svg" alt="Yu-Gi-Oh">
                </div>
                <div class="col-10">
                    <h1>
                        Yu-Gi-Oh!
                    </h1>
                </div>
            </div>

            <div class="row">
                <div class="col-6 offset-2">
                    <form @submit.prevent="handleFormSubmit()">
                        <div class="row">
                            <div class="col-5">                                <select class="form-select" aria-label="Default select example" v-model="searchArchetype">
                                    <option selected value="">Select status</option>
                                    <option value="alien">Alien</option>
                                    <option value="infernoble arms">Infernoble Arms</option>
                                    <option value="noble knight">Noble Knight</option>
                                </select>
                            </div>

                            <div class="col-auto">
                                <button type="submit" class="btn btn-primary mb-3">
                                    Search
                                </button>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </header>
</template>

<style lang="scss" scoped>
    header {
        background-color: rebeccapurple;
    }
</style>
