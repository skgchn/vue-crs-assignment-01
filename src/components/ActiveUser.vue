<script>
export default {
    props: {
        username: {
            type: String,
            required: true
        },
        age: {
            type: Number,
            required: true
        }
    },
    computed: {
        displayAge() {
            return this.age < 0? '' : `${this.age} Years`;
        }
    }
};

</script>

<template>
        <section class="active-user">
            <p>{{ username }}</p>
            <p>{{ displayAge }}</p>
        </section>
</template>
<style scoped>
    .active-user {
        text-align: center;
        font-size: 2rem;
        width: 48%;

        /* Styles as a flex child item */
        flex: 1 1 auto; /* grow(yes), shrink(yes, default), basis ==> see as max_size, min_size, ideal_size */

        /* Styles as a flex container */
        display: flex;
        flex-direction: column;
        justify-content: flex-start; /* Where to place the items in the container along the main axis */
        align-items: flex-end; /* Decides how the items align to each other.
                                  Only when flex-wrap = nowrap, decides where to place the items
                                  in the container along the cross axis.*/
        row-gap: 1rem;
    }
    .active-user>p {
        min-height: 6.3125rem;
        line-height: 6.3125rem;
        width: 100%;
        border-radius: 5px;
    }
    .active-user>p:first-child {
        background-color: orangered;
    }
    .active-user>p:last-child {
        background-color: pink;
    }
</style>