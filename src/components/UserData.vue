<script>
export default {
    data() {
        return {
            username: '',
            ageAsStr: '',
            age: -1
        };
    },
    emits: [ 'user-info-changed' ],
    methods: {
        updateUsername(event) {
            this.username = event.target.value;
            this.$emit('user-info-changed', this.username, this.age);
        },
        updateAge(event) {
            const age = event.target.value.length === 0? -1 : Number(event.target.value);
            this.age = isNaN(age) || age < 0? -1 : age;
            this.ageAsStr = this.age < 0? '' : `${this.age}`;
            this.$refs.ageField.value = (this.age < 0)? '' : this.age;
            this.$emit('user-info-changed', this.username, this.age);
        }
    }
}
</script>

<template>
        <section class="user-data">
            <div>
                <label for="username">Username</label>
                <input
                    type="text"
                    name="username"
                    @input="updateUsername"
                    :value="username"
                    placeholder="Enter your name"
                    autofocus="autofocus" />
            </div>
            <div>
                <label for="ageAsStr">Age</label>
                <input
                    type="text"
                    name="ageAsStr"
                    placeholder="Enter your age"
                    @input="updateAge"
                    ref="ageField"
                    :value="ageAsStr" />
            </div>
        </section>
</template>

<style scoped>
.user-data {
    width: 48%; /* width 48% of parent */

    /* Styles as a flex child item */
    flex: 1 1 auto; /* grow(yes), shrink(yes, default), basis ==> max_size, min_size, ideal_size */

    /* Styles as a flex container */
    display: flex;
    flex-direction: column;
    justify-content: flex-start; /* Where to place the items in the container along the main axis */
    align-items: center; /* Decides how the items align to each other.
                                Only when flex-wrap = nowrap, decides where to place the items
                                in the container along the cross axis.*/
    row-gap: 1rem;
}

.user-data>div {
    width: 98%; /* These two together look good after having wrapped */
    padding: 0 1%; /* 98% + 1% left padding + 1% right padding = 100% width */

    /* Styles as a flex container */
    display: flex;
    flex-direction: column;
    justify-content: flex-start; /* Where to place the items in the container along the main axis */
    align-items: flex-start; /* Decides how the items align to each other.
                                Only when flex-wrap = nowrap, decides where to place the items
                                in the container along the cross axis.*/
    row-gap: 5px;
}

.user-data>div>input {
    width: 100%;
}
</style>