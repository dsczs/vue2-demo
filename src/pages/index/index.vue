<style lang="less" scoped>
    .login-msg {
        padding: 50px;
        text-align: center;
    }

    .msg {
        padding: 50px;
        text-align: center;
        font-size: 20px;
        color: red;
    }
</style>
<template>
    <div>
        <v-header title="首页">
            <router-link slot="right" to="/home" v-if="user.id">{{user.name}}</router-link>
        </v-header>
        <div class="login-msg" v-if="!user.id">
            <router-link to="/login">你还未登录，请先登录</router-link>
        </div>
        <div class="msg" v-if="user.id">
            <img :src="logo" alt="" width="50"> <br>
            哈哈，恭喜你已经入坑Vue2
        </div>
    </div>
</template>
<script>
    import {mapState} from 'vuex'
    import logo from './logo.png'

    export default {
        data() {
            return {
                logo
            }
        },
        computed: mapState({user: state => state.user}),
    }
</script>