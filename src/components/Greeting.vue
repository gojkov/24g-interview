<template>
    <b-container>
        <!-- As a heading -->
        <b-navbar tag="div" class="greeting w-100 mb-0">
            <b-navbar-brand tag="p">Welcome, <span>{{ user}}</span></b-navbar-brand>
        </b-navbar>
    </b-container>
</template>

<script>

export default {
    name: 'Greeting',
    props: {
        user: String
    }
}

</script>

<style lang="scss">

.greeting {
    display: flex;
    font-family: 'Brandon Grotesque Light';
    font-size: 1.1rem;
    background: $blue-light;
    height: 5vh;
    padding-left: 4rem;
    align-items: center;
    
    color: $gray-light;

    p {
        letter-spacing: .02em;
    }

    span {
        font-family: 'Brandon Grotesque Medium';
    }
}

</style>