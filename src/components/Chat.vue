<template>
    <section>
        <ChatListMessage :messages='messages'/>
        <Sendbox @messageSent="onMessageSent"/>
    </section>
</template>

<script>
import ChatListMessage from '@/components/ChatListMessage'
import Sendbox from '@/components/Sendbox'
import store from '../store'

export default {
    methods: {
        onMessageSent(message) {
            store.messages.push(message) 
            this.$api.messageSend(message)    
        }
    },
    computed: {
        messages: () => store.messages
    },
    components: {
        ChatListMessage,
        Sendbox
    },

}
</script>

<style lang="stylus">
    section
        background-color #212121
        height: 100vh
        overflow hidden
        padding 0 25px 0 25px
</style>
