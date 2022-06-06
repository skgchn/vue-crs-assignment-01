<script>
import { ref } from 'vue';

export default {
    emits: [ 'user-info-changed' ],
    setup(_, {emit}) {
        const username = ref('');
        const ageAsStr = ref('');
        const age = ref(-1);
        const ageField = ref(null); // require a ref to the field to stop the user from typing non-digits or 00..

        function updateUsername({target: {value: newName}}) {
            username.value = newName;
            emit('user-info-changed', username.value, age.value);
        }

        function updateAge({target: {value: newAgeAsStr}}) {
            const newAge = newAgeAsStr.length === 0? -1 : Number(newAgeAsStr);
            age.value = isNaN(newAge) || newAge < 0? -1 : newAge;
            ageField.value.value = ageAsStr.value = age.value < 0? '' : `${age.value}`;
            emit('user-info-changed', username.value, age.value);
        }
        return {
            username,
            ageAsStr,
            age,
            ageField,
            updateUsername,
            updateAge
        }
    },
    // data() {
    //     return {
    //         username: '',
    //         ageAsStr: '',
    //         age: -1
    //     };
    // },
    // methods: {
    //     updateUsername(event) {
    //         this.username = event.target.value;
    //         this.$emit('user-info-changed', this.username, this.age);
    //     },
    //     updateAge(event) {
    //         const age = event.target.value.length === 0? -1 : Number(event.target.value);
    //         this.age = isNaN(age) || age < 0? -1 : age;
    //         this.ageAsStr = this.age < 0? '' : `${this.age}`;
    //         this.$refs.ageField.value = (this.age < 0)? '' : this.age;
    //         this.$emit('user-info-changed', this.username, this.age);
    //     }
    // }
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