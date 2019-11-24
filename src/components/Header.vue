<template>
    <div class="header">
        <img src="../assets/svg/24g_logo.svg" alt="24G logo">
        <span>Video Player</span>
    </div>
</template>

<script>

export default {
    name: 'Header'
}

</script>

<style lang="scss">

.header {
    height: 15vh;
    background: $gray-midnight;
    width: 100%;
    display: flex;

    img {
        width: 5rem;
        justify-content: flex-start;
        padding-left: 4rem;
    }

    span {
        font-family: 'Brandon Grotesque Medium';
        text-transform: uppercase;
        color: $gray-light;
        font-size: 1.4rem;
        letter-spacing: .1em;
        margin-top: 2.6rem;
        margin-left: 1.2rem;
    }
}

</style>