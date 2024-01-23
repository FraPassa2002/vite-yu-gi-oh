<script>
export default {
    data() {
        return {

        };
    },
    props: {
        card: Object,    
    }
}
</script>

<template>
    <div class="single-card">
        <div class="mb-2">
            <img class="w-100" :src="card.card_images[0].image_url" :alt="card.name">
        </div>

        <div>
            <h2 class="mb-3 fs-5">
                {{ card.name }}
            </h2>
            <h2 class="mb-3 fs-6">
                {{ card.archetype }}
            </h2>
        </div>
    </div>
</template>

<style lang="scss" scoped>
</style>
