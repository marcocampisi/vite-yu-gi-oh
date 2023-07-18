<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import { store } from './store.js';
import axios from "axios";

export default {
    data() {
        return {
            store,
            filteredCards: store.cards
        }
    },
    components: {
        HeaderComponent,
        MainComponent
    },
    methods: {
        getCards() {
            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=50&offset=0', {
                    params: {
                        // name: this.store.searchText,
                        archetype: this.store.archetypeOptions
                    }
                })
                .then(response => {
                    const cards = response.data.data;
                    store.cards = cards;
                })
                .catch(error => {
                    console.error(error);
                });
        },
        performSearch() {
            console.log('Intercettata search');
            this.getCards();
        }
    }, created() {
        this.getCards();
    },

}
</script>

<template>
    <HeaderComponent @search="performSearch()" />
    <MainComponent />
</template>

<style lang="scss">
@import "assets/scss/main.scss";

body {
    background-color: $body-color;
}
</style>
