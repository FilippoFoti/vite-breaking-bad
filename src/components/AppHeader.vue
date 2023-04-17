<script>
export default {
    name: "AppHeader"
}
</script>

<template>
    <header class="d-flex align-items-center">
        <figure class="m-0 mx-4">
            <img src="../assets/img/1200px-Yu-Gi-Oh!_(Logo).jpg" alt="Logo">
        </figure>
        <h2 class="m-0">Yu-Gi-Oh Api</h2>
    </header>
</template>

<style scoped lang="scss">
@use "../style/partials/variables" as *;
// @use "../style/partials/mixins" as *;

header {
    height: 80px;

    img {
        width: 70px;
    }

    h2 {
        font-size: 3rem;
        color: $primary;
    }
}
</style>