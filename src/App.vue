<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import axios from "axios";
import { store } from "./store.js"

export default {
    data() {
        return {

        }
    },
    components: {
        HeaderComponent,
        MainComponent
    },
    methods: {},
    created() {
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
            .then(response => {
                console.log(response.data.results);
            });
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
