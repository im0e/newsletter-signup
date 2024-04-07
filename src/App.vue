
<script setup>
import SubscribeForm from '@/components/SubscribeForm.vue'
import SubscribedMessage from './components/SubscribedMessage.vue'

import {ref} from 'vue'

const subscribed = ref(false)
const email = ref('email')

function toggleSubscribe(emailAddress) {
  email.value = emailAddress
  subscribed.value = !subscribed.value
}

</script>
<template>
  <SubscribeForm v-if="!subscribed" @subscribe="toggleSubscribe"/>
  <SubscribedMessage v-else @subscribe="toggleSubscribe" :email="email"/>
</template>