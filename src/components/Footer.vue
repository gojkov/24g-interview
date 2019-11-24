<template>
    <div class="img-container">
        <img class="footer-image" src="../assets/svg/powered_by_24g.svg" alt="powered by 24G">
    </div>
</template>

<script>

export default {
    name: 'Footer'
}

</script>

<style lang="scss">

.img-container {
    margin-top: 1rem;
    width: 840px;
    display: flex;

    .footer-image {
        justify-content: center;
        margin: 1rem auto;
        width: 140px;
    }
}

</style>