<script>
export default {
    name: "CharacterCard",
    props: {
        character: Object
    }
}
</script>

<template>
    <div class="card">
        <img :src="character.card_images[0].image_url_small" alt="">
        <h3 class="m-0 m-3 text-center">{{ character.name }}</h3>
        <p class="text-center">{{ character.archetype }}</p>
    </div>
</template>

<style scoped lang="scss">
@use "../style/partials/variables" as *;

.card {
    background-color: $background;
    border-radius: 0;
    height: 100%;

    h3 {
        color: $text-color;
        font-size: 1.2rem;
        text-transform: uppercase;
    }
}
</style>