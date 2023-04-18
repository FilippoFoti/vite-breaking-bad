<script>
import CharacterCard from "./CharacterCard.vue";
import AppLoader from "./AppLoader.vue";
import { store } from "../store";
import axios from "axios";

export default {
    name: "AppMain",
    components: {
        CharacterCard,
        AppLoader
    },
    data() {
        return {
            store,
            statusOptions: ["Alien", "Ally of Justice", "Ancient Gear"],
            selectedStatus: "",
            characterFounded: 0,
        }
    },
    mounted() {
        this.getCard()
    },
    methods: {
    getArchetype() {
      store.loading = true;
      if (this.selectedStatus) {
        axios
          .get(store.apiURL, {
            params: {
              archetype: this.selectedStatus,
            },
          })
          .then((resp) => {
            this.store.characters = resp.data.data;
            this.characterFounded = resp.data.meta.current_rows;
            store.loading = false;
          });
      } else {
        this.getCard();
      }
    },
    getCard() {
      axios.get(store.apiURL).then((resp) => {
        this.store.characters = resp.data.data;
        this.characterFounded = resp.data.meta.current_rows;
      });
    },
  },
}
</script>

<template>
    <main>
        <AppLoader v-if="store.loading" />
        <div class="container d-flex align-items-center py-4">
            <select name="status" id="status" v-model="selectedStatus" @change="getArchetype">
                <!-- <option value="">All</option> -->
                <option :value="status" v-for="status in statusOptions">{{ status }}</option>
                <!-- <option value="">Ally of Justice</option> -->
                <!-- <option value="">Ancient Gear</option> -->
            </select>
        </div>
        <div class="container white p-5">
            <div class="black d-flex align-items-center">
                <h3 class="m-0 px-4">Found {{ characterFounded }} cards</h3>
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
        padding: 8px 30px 8px 10px;
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