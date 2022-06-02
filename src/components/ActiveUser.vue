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
    <div>
        <section>
            <p> {{ username }} </p>
            <p> {{ displayAge }} </p>
        </section>
    </div>
</template>
<style scoped>
    section {
        text-align: center;
        font-size: 2rem;
        display: flex;

        /* Styles as a flex container */
        flex-direction: column;
        justify-content: flex-start; /* Where to place the items in the container along the main axis */
        align-items: flex-end; /* Decides how the items align to each other.
                                  Only when flex-wrap = nowrap, decides where to place the items
                                  in the container along the cross axis.*/
        row-gap: 1rem;

        /* Styles as a flex child item */
        flex: 0 0 40%; /* grow, shrink, basis ==> see as max_size, min_size, ideal_size */
    }
    section>p {
        padding: 2rem 0;
        margin: 0;
        height: 6.3125rem;
        min-width: 30rem;
    }
    section>p:first-child {
        background-color: orangered;
    }
    section>p:last-child {
        background-color: pink;
    }
</style>