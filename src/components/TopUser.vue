<template>
    <div class="profile">
        <div class="slogan">
            <span>WE'RE WATCHING YOU</span><br>
            <span>{{user.username}}</span>
        </div>
    </div>
</template>

<script>
export default {
  props: ['user']
}
</script>

<style lang="stylus" scoped>
    .profile
        background:url(../assets/eye-bg-black.svg) no-repeat;
        background-position center
        color #fbea4e!important
        margin-top 10px
        font-size 1.5em
        font-weight 800
        color: #ffffff
        height 100px
        background-size: 140px;
        margin-bottom: 20px;
    .slogan
        position: relative;
        padding: 30px 0 0 0;
</style>
