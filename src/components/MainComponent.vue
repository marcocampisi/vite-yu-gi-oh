<script>
import CardComponent from './CardComponent.vue';
import { store } from '../store.js';
import axios from "axios";

export default {
    name: 'MainComponent',
    data() {
        return {
            store
        }
    },
    components: {
        CardComponent
    },
    methods: {
        getCards() {
            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                .then(response => {
                    const cards = response.data.data;
                    this.store.cards = cards;
                })
                .catch(error => {
                    console.error(error);
                });
        }
    }, mounted() {
        this.getCards();
    }
}
</script>

<template>
    <div class="container-fluid">
        <div class="container">
            <div class="col-sm-2 my-5">
                <select class="form-select" aria-label="Filter" v-on:change="getCards">
                    <option value="1">Alien</option>
                    <option value="2">Two</option>
                    <option value="3">Three</option>
                </select>
            </div>
        </div>
        <div class="container bg-white d-flex">
            <div class="row w-100 justify-content-between p-5">
                <div class="col-md-3" v-for="(card, i) in store.cards" :key="card.id">
                    <CardComponent :store="card" />
                </div>
            </div>
        </div>

    </div>
</template>

<style scoped></style>