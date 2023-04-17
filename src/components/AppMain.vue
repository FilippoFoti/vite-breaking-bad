<script>
import CharacterCard from "./CharacterCard.vue";
import AppLoader from "./AppLoader.vue"
import { store } from "../store"

export default {
    name: "AppMain",
    components: {
        CharacterCard,
        AppLoader
    },
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <main>
        <AppLoader v-if="store.loading" />
        <div class="container d-flex align-items-center py-4">
            <select name="" id="">
                <option value="">Alien</option>
                <option value="">Alien</option>
                <option value="">Alien</option>
            </select>
        </div>
        <div class="container white p-5">
            <div class="black d-flex align-items-center">
                <h3 class="m-0 px-4">Found 39 cards</h3>
            </div>
            <div class="row row-cols-5 v-else">
                <div class="col mb-3" v-for="character in store.characters">
                    <CharacterCard :character="character"/>
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped lang="scss">
@use "../style/partials/variables" as *;

main {
    background-color: $background;

    select {
        padding: 8px 100px 8px 10px;
        font-size: 1.3rem;
        border-radius: 10px;
    }

    .white {
        background-color: $text-color;

        .black {
            height: 60px;
            background-color: black;

            h3 {
                color: $text-color;
                font-size: 1.3rem;
            }
        }
    }
}
</style>