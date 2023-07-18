<script>
import { store } from '../store.js';

export default {
    name: "HeaderComponent",
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="headerContainer">
        <nav class="navbar navbar-expand-lg bg-body-tertiary">
            <div class="container-fluid px-5">
                <a class="navbar-brand fw-bold" href="#">Yu-Gi-Oh API</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                    aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse justify-content-end" id="navbarSupportedContent">
                    <form class="d-flex" role="search" @submit.prevent="$emit('search')">
                        <input class="form-control me-2" type="text" placeholder="Ricerca..." aria-label="Search"
                            v-model="store.searchText">
                        <button class="btn btn-outline-success" type="submit">Vai</button>
                    </form>
                </div>
            </div>
        </nav>
    </div>
</template>

<style lang="scss" scoped>
input {
    color: black;
}
</style>