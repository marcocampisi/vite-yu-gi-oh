<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import { store } from './store.js';
import axios from "axios";

export default {
    data() {
        return {
            store
        }
    },
    components: {
        HeaderComponent,
        MainComponent
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
    }, created() {
        this.getCards();
    }
}
</script>

<template>
    <HeaderComponent />
    <MainComponent />
</template>

<style lang="scss">
@import "assets/scss/main.scss";

body {
    background-color: $body-color;
}
</style>
