<template>
    <div class="wrapper">
        <picture>
            <source srcset="@/assets/images/illustration-sign-up-desktop.svg" media="(min-width: 1024px)"/>
            <img src="@/assets/images/illustration-sign-up-mobile.svg" alt="" width="100%" />
        </picture>
        <div class="content">
            <h1>
                Stay Updated!
            </h1>
            <p>
                Join 60,000+ product managers receiving monthly updates:
            </p>
            <ul>
                <li v-for="update in updatesContent" :key="update">
                    {{ update }}
                </li>
            </ul>
            <form @submit.prevent="validateSubscribtion">
                <label for="email">
                    <div>
                        <span>Email</span>
                        <span v-if="!validEmail" class="warning">Valid email required!</span>
                    </div>
                    <input name="email" type="email" placeholder="email@company.com" v-model="email" :class="{warning : !validEmail}">
                </label>
                <input name="submit" type="submit" value="Subscribe to monthly newsletter">
            </form>
            <!-- <button @click="$emit('subscribe')">Subscribe</button> -->
        </div>
    </div>
</template>

<script setup>

import {ref, defineEmits, defineProps } from 'vue'

const emit = defineEmits(['subscribe'])

const updatesContent = ref([
    "Product discovery and building what matters",
    "Measuring to ensure updates are a success",
    "And more!"
])

const email = ref('')
const validEmail = ref(false || email.value.length === 0)

function validateSubscribtion() {
    validEmail.value = /^[\w\-\.]+@([\w-]+\.)+[\w-]{2,}$/.test(email.value);
    if (validEmail.value) {
        emit('subscribe', email.value)
        console.log('emitted')
    }
}

</script>

<style scoped>

h1 {
    font-size: 2rem;
    font-weight: 700;
    /* margin-bottom: 1rem; */
}

ul {
    list-style: none;
    padding: 1rem 0;
}

ul li {
    background-image: url(@/assets/images/icon-list.svg);
    background-repeat: no-repeat;

    padding-left: 2rem;
    padding-bottom: .5rem;
}

form {
    display: flex;
    flex-direction: column;
    gap: .75rem;

    padding-bottom: 1rem;
}

form input {
    padding: 1rem;
    border-radius: 8px;

    border: 1px solid transparent;
}

form label {
    display: flex;
    flex-direction: column;

    gap: .25rem
}

form label div {
    display: flex;
    flex-direction: row;
    justify-content: space-between;

    padding: 0 .25rem;
}

form label div span {
    font-size: 0.825rem;
    font-weight: 700;
}

form input[type=email] {
    border: 1px solid var(--color-border);
    font-weight: 700;
}

form input[type=submit] {
    background-color: var(--color-button);
    color: var(--c-neutral-white);

    font-weight: 700;
}


form input[type=submit]:is(:hover, :focus, :active) {
    background-color: var(--color-primary);
}


.wrapper {
    background-color: var(--c-neutral-white);

    display: flex;
    flex-direction: column;
    width: 100dvw;
}

.content {
    /* background-color: green; */

    padding: 2rem 3rem;
}

.warning {
    color: var(--color-warning-text);
}


form input[type=email]:is(:focus, :hover, :active) {
    border: 1px solid var(--color-border-hover);
    color: var(--color-text);
    outline: none;
}

form input[type=email]:is(:focus, :hover, :active):has(.warning)  {
    color: var(--color-warning-text);
    background-color: var(--color-warning-background);
    font-weight: 700;
}


@media screen and (min-width: 1024px){
    h1 {
        font-size: 3.25rem;
        font-weight: 700;
    }

    .wrapper {
        display: flex;
        flex-direction: row-reverse;
        justify-content: space-between;


        padding: 2rem;
        border-radius: 2rem;

        max-width: 1024px;
        
        
    }

    .content {
        display: flex;
        flex-direction: column;

        gap: 1rem;
    
        max-width: 50%;
    }
}

</style>

