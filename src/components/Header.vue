<template>
    <b-container fluid>
    <!-- Image and text -->
    <b-navbar tag="div" sticky="true">
        <b-navbar-brand class="header w-100 pl-5" tag="div" href="#">
            <img src="../assets/svg/24g_logo.svg" class="d-inline-block align-top" alt="24G logo">
            <span class="ml-3">Video Player</span>
        </b-navbar-brand>
    </b-navbar>
    </b-container>
</template>

<script>

export default {
    name: 'Header'
}

</script>

<style lang="scss">

.header {
    height: 15vh;
    width: 100%;
    background: $gray-midnight;
    display: flex;
    align-items: center;

    img {
        width: 5rem;
        padding-left: 1rem;
        justify-content: flex-start;
    }

    span {
        font-family: 'Brandon Grotesque Medium';
        text-transform: uppercase;
        color: $gray-light;
        font-size: 1.2rem;
        letter-spacing: .1em;
        margin-top: .3rem;
    }
}

</style>