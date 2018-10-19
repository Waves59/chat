<template>
    <div class="users">
        <TopUser :user='user' />
        <div class="scroll-list">
            <ul>
                <User v-for="(user, index) in users" :key="index" :user="user" />
            </ul>
        </div>
    </div>
</template>

<script>
import TopUser from "@/components/TopUser"
import User from "@/components/User"
import store from "../store"
export default {

    components: {
        User,
        TopUser
    },
    computed: {
        users: () => store.users,
        user: () => store.user
    }
}
</script>

<style lang="stylus">
    .users
        height 100%
        background-color #323232
</style>

