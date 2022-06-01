<script>
    import ActiveUser from './components/ActiveUser.vue'
    import UserData from './components/UserData.vue'

    export default {
        components: {
            ActiveUser,
            UserData
        },
        data() {
            return {
                username: '',
                age: -1
            }
        },
        methods: {
            displayUser(username, age) {
                this.username = username;
                this.age = age;
            }
        }
    }
</script>

<template>
    <section class="app">
        <active-user :username="username" :age="age"></active-user>
        <user-data @user-info-changed="displayUser"></user-data>
    </section>
</template>
<style>
    :root {
        font-family: 'Open Sans', Helvetica, sans-serif;
        font-size: 16px;
    }
    *, *:before, *:after {
        font-family: inherit;
        font-size: inherit;
    }
</style>
<style scoped>
    section.app {
        margin: 2rem auto;
        display: flex;
        width: 80%;
        background: lightgray;
        padding: 1rem;

        /* Styles as a flex container */
        justify-content: center; /* where to place all the items along the main axis */
        align-items: flex-start; /* where to place all the items along the cross axis */
        align-content: flex-start; /* when wrapped, how should the items align to each other */
        column-gap: 2rem;
        row-gap: 3rem;
        flex-wrap: wrap;
    }
</style>