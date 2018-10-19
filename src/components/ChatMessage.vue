<template>
    <transition name="appears">
        <li>
            <div class="message">
                <div :class="{'right': profile.username == message.user.username }">
                    <div class="username">{{message.user.username}}</div> 
                    <div class="user-message">{{message.text}}</div>
                </div>
            </div>
        </li>
    </transition>
</template>

<script>
import store from "../store"
export default {
    props: ['message'],
    computed: {
        profile: () => store.user
    }
}
</script>

<style lang="stylus">
    li
        color #ffffff
        list-style-type none
        margin 5px
        border-radius 20px
        text-align center
        padding 8px
        font-size 1.4em
    
    section li
        text-align left

    .appears-enter-active
        transition all .8s ease
    
    .appears-leave-active 
        transition all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0)
    
    .appears-enter, .appears-leave-to
        transform translateX(10px)
        opacity 0
    .avatar-users
        width 150px
        height 150px
    .username
        text-align: left 
    .user-message
        background-color #000000
        padding 20px
        word-wrap: break-word;
        display: inline-flex;
    .right
        float: right;
    .right .username
        text-align right 
        padding-right 5px
    .userList
        text-align left 
        padding: 2px;
</style>
