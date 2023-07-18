<script>
export default {
    name: "CardComponent",
    props: {
        store: {
            type: Object,
            required: true
        }
    }
}
</script>

<template>
    <div class="singleCard text-center mb-5">
        <div>
            <img class="w-100 rounded" :src="store.card_images[0].image_url" :alt="store.name">
        </div>
        <div class="titleContainer py-3 mt-2 rounded">
            <h2 class="text-white fw-bold text-uppercase fs-4 text-break">{{ store.name }}</h2>
            <h3 class="text-black fw-light fs-5">{{ store.archetype }}</h3>
        </div>
    </div>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables.scss' as *;

.singleCard {
    img {
        cursor: pointer;
    }
}

.titleContainer {
    background-color: $bg-body-color;
    min-height: 150px;

    h2 {
        text-shadow: 2px 2px 2px gray;
    }
}
</style>