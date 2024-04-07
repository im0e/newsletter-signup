<template>
    <div class="wrapper">
        <div class="content">
            <img src="@/assets/images/icon-success.svg" alt="" width="64px">
            <h1>Thanks for subscribing!</h1>
            <p>
                A confirmation email has been sent to 
                <span>{{ email }}</span>
                .Please open it and click the button inside to confirm your subscription.
            </p>
        </div>
        <button @click="$emit('subscribe')"> Dismis message </button>
    </div>
</template>


<script setup>

import { ref } from 'vue'

const emit = defineEmits(['subscribe'])
const props = defineProps(['email'])

const email = ref(props.email)

</script>


<style scoped>

.wrapper {
    background-color: var(--c-neutral-white);

    display: flex;
    flex-direction: column;
    width: 100dvw;

    /* height: 100dvh; */

    display: flex;
    justify-content: space-between;

    padding: 2rem;
}

.wrapper button {

    background-color: var(--color-button);
    color: var(--c-neutral-white);

    font-weight: 700;

    padding: 1rem;
    border-radius: 8px;

    border: 1px solid transparent;
}

.wrapper button:is(:hover, :focus, :active) {
    background-color: var(--color-primary);
}

.content {
    /* background-color: green;s */

    display: flex;
    flex-direction: column;
    padding: 2rem;
    flex: 1;

    justify-content: center;
}

.content p span {
    font-weight: 700;
}

@media screen and (min-width: 1024px){
    .wrapper {
        display: flex;
        flex-direction: column;

        max-width: 460px;
        border-radius: 2rem;
    }

    .content {
        display: flex;
        flex-direction: column;

        gap: 1rem;
    }
}

</style>