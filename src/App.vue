<script>
    import { ref } from 'vue';
    import ActiveUser from './components/ActiveUser.vue'
    import UserData from './components/UserData.vue'

    export default {
        components: {
            ActiveUser,
            UserData
        },
        setup() {
            const username = ref('');
            const age = ref(-1);
            const debugFlexbox = ref(false);

            function displayUser(uname, uage) {
                username.value = uname;
                age.value = uage;
            }

            return {
                username,
                age,
                debugFlexbox,
                displayUser
            }
        },
        // data() {
        //     return {
        //         username: '',
        //         age: -1,
        //         debugFlexbox: false
        //     }
        // },
        // methods: {
        //     displayUser(username, age) {
        //         this.username = username;
        //         this.age = age;
        //     }
        // }
    }
</script>

<template>
        <section class='app'>
            <active-user :username="username" :age="age"></active-user>
            <user-data @user-info-changed="displayUser"></user-data>
        </section>

        <div v-if="debugFlexbox" class='container'>
            <div class='child child1'>1</div>
            <div class='child child2'>2</div>
            <div class='child child3'>3</div>
            <div class='child child4'>4</div>
        </div>
</template>

<style>
    :root {
        font-family: 'Open Sans', Helvetica, sans-serif;
    }

    *, *:before, *:after {
        font-size: inherit;
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
</style>

<style scoped>
    section.app {
        margin: 2rem auto;
        display: flex;
        width: 80vw;
        background: lightgray;
        padding: 1rem;

        /* Styles as a flex container */
        justify-content: center; /* Where to place the items in the container along the main axis */
        flex-wrap: wrap;
        align-content: flex-start; /* Only when flex-wrap = wrap. decides where to place the items
                                        in the container along the cross axis */

        align-items: flex-start; /* decides how the items align to each other.
                                    Only when flex-wrap = nowrap, decides where to place the items
                                    in the container along the cross axis.*/
        column-gap: 2rem;
        row-gap: 3rem;
    }
    /*    .container {
        width: 150px;
        height: 150px;
        border: 1px solid red;
        display: flex;

        justify-content: center;
        align-items: baseline;
        flex-wrap: wrap;
        align-content: center;
    }

    .child {
        width: 16px;
        height: 16px;
        border: 1px solid blue;
        text-align: center;
        line-height: 16px;
        font-size: 0.5rem;
    }

    .child1 {
        font-size: 0.5rem;
    }

    .child2 {
        height: 20px;
        width: 20px;
        line-height: 20px;
        font-size: 1rem;
    }*/
</style>