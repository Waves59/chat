<template>
    <div class="scroll-list">
        <ul>
            <ChatMessage v-for="(message, index) in messages" :key="index" :message="message"/>
        </ul>
    </div>
</template>

<script>
import ChatMessage from '@/components/ChatMessage'
export default {
    props: ['messages'],
    components: {
        ChatMessage
    }
}
</script>
<style lang="stylus">
    ul
        display -webkit-box;
        flex-direction column
        padding-inline-start: 0;
    .scroll-list
        height: 85vh;
        overflow scroll
        overflow-x: hidden;
        display: flex;
        flex-direction: column-reverse;
    section .scroll-list
        background:url(../assets/eye-bg-grey.svg) no-repeat;
        background-position center
    ::-webkit-scrollbar { 
        display none
    }
</style>