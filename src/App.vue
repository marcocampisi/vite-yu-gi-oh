<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import axios from "axios";

export default {
    data() {
        return {

        }
    },
    components: {
        HeaderComponent,
        MainComponent
    },
    methods: {}
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
