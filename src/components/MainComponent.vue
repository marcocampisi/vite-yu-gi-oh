<script>
import CardComponent from './CardComponent.vue';
import { store } from '../store.js';

export default {
    name: 'MainComponent',
    data() {
        return {
            store
        }
    },
    components: {
        CardComponent
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