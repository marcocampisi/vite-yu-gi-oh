<script>
import CardComponent from './CardComponent.vue';
import { store } from '../store.js';

export default {
    name: 'MainComponent',
    data() {
        return {
            store,
            archetype: "",
            archetypeOptions: []
        }
    },
    components: {
        CardComponent
    },
    computed: {
        filteredCards() {
            if (this.archetype === "") {
                return this.store.cards;
            } else {
                return this.store.cards.filter(card => card.archetype === this.archetype);
            }
        },
    },
    methods: {
        getArchetypeOptions() {
            const archetypes = new Set();
            for (const card of this.store.cards) {
                archetypes.add(card.archetype);
            }
            this.archetypeOptions = Array.from(archetypes);
        },
    },
    created() {
        const archetypes = new Set();
        for (const card of this.store.cards) {
            if (card.archetype) {
                archetypes.add(card.archetype);
            }
        }
        this.archetypeOptions = Array.from(archetypes);
    }
}
</script>

<template>
    <div class="container-fluid">
        <div class="container">
            <div class="col-sm-2 my-5">
                <select class="form-select" aria-label="Filter" v-model="archetype">
                    <option value="">Seleziona un archetipo</option>
                    <option v-for="archetypeOption in archetypeOptions" :key="archetypeOption" :value="archetypeOption">
                        {{ archetypeOption }}
                    </option>
                </select>
            </div>
        </div>
        <div class="container bg-white d-flex">
            <div class="row w-100 justify-content-between p-5">
                <div class="col-md-3" v-for="(card, i) in filteredCards" :key="card.id">
                    <CardComponent :store="card" />
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
