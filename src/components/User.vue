<template>
    <li>
        <div class="userlist">
            <div class="shape">{{user.username[0]}}</div>
            <div class="usern">{{user.username}}</div>
        </div>
    </li>
</template>

<script>
export default {
    props: ['user']
}
</script>

<style lang="stylus">
    .avatarusers
        width 30px
        height 30px
    .userlist
        background-color #000000
        display: inline-flex;
        padding: 10px;
        overflow: hidden;
        text-align: center;
        line-height 50px
        width: 300px;
        margin: auto;

    .shape
        background-color #fbea4e
        border-radius 100px
        height 50px
        width 50px
        line-height 50px
    .usern
        margin-left 10px
</style>


