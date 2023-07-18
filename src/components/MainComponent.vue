<script>
import CardComponent from './CardComponent.vue';
import { store } from '../store.js';

export default {
    name: 'MainComponent',
    data() {
        return {
            store,
            archetype: ""
        }
    },
    components: {
        CardComponent
    },
    computed: {
        filteredCards() {
            if (this.archetype === "") {
                return this.store.cards.filter(card => {
                    const searchText = this.store.searchText && typeof this.store.searchText === 'string' ? this.store.searchText.toLowerCase() : '';
                    return card.name.toLowerCase().includes(searchText);
                });
            } else {
                return this.store.cards.filter(card => {
                    const searchText = this.store.searchText && typeof this.store.searchText === 'string' ? this.store.searchText.toLowerCase() : '';
                    return card.archetype === this.archetype && card.name.toLowerCase().includes(searchText);
                });
            }
        },
        getUniqueArchetypes() {
            const archetypes = new Set(this.store.cards.map(card => card.archetype));
            return Array.from(archetypes);
        }
    }
}
</script>

<template>
    <div class="container-fluid">
        <div class="container">
            <div class="col-sm-2 my-5">
                <select class="form-select" aria-label="Filter" v-model="archetype">
                    <option value="">Seleziona un archetipo</option>
                    <option v-for="archetypeOption in getUniqueArchetypes" :key="archetypeOption" :value="archetypeOption">
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

<style lang="scss" scoped>
select {
    cursor: pointer;
    color: black;
}
</style>
