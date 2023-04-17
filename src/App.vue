<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";
import { store } from "./store";

export default {
    components: {
        AppHeader,
        AppMain
    },
    data() {
      return {
        store
      }
    },
    mounted() {
      store.loading = true;
      axios.get(store.apiURL).then((resp) => {
        this.store.characters = resp.data.data;
        store.loading = false;
      })
    }
}
</script>

<template>
    <AppHeader />
    <AppMain />
</template>

<style lang="scss">
@use "./style/general.scss"
</style>