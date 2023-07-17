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
    <div class="singleCard text-center">
        <div>
            <img :src="store.card_images.image_url" :alt="store.name">
        </div>
        <div>
            <h2>{{ store.name }}</h2>
        </div>
        <div>
            <h3>{{ store.archetype }}</h3>
        </div>
    </div>
</template>

<style lang="scss" scoped></style>