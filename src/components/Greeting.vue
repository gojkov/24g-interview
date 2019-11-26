<template>
    <div class="greeting">
        <p>Welcome, <span>{{ user }}</span></p>
    </div>
</template>

<script>

export default {
    name: 'Greeting',
    props: {
        user: String
    }
}

</script>

<style scoped lang="scss">

.greeting {
    display: flex;
    font-family: 'Brandon Grotesque Light';
    font-size: 1.1rem;
    background: $blue-light;
    height: 5vh;
    width: 100%;
    color: $gray-light;

    p {
        //margin-left: 2.7rem;
        padding-left: 4rem;
        letter-spacing: .02em;

        align-items: baseline;
        justify-content: flex-start;
        align-self: center;
    }

    span {
        font-family: 'Brandon Grotesque Medium';
    }
}

</style>