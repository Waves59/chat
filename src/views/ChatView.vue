<template>
    <div class="main">
        <Users />
        <Chat />
    </div>
</template>

<script>

import Users from "@/components/Users"
import Chat from "@/components/Chat"

export default {
    components: {
        Users,
        Chat
    }    
}

</script>
<style lang="stylus">
    html, body {margin: 0; height: 100%; overflow: hidden}
    .main
        display grid
        grid-template-columns: 35% 65%;
        grid-template-rows auto
</style>

