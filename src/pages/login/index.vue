<style lang="less" scoped>
    .login {
        padding: 50px;
        text-align: center;

        .line {
            padding: 5px;

            input {
                padding: 0 10px;
                line-height: 28px;
            }
        }

        button {
            padding: 0 20px;
            margin-top: 20px;
            line-height: 28px;
        }
    }
</style>
<template>
    <div>
        <v-header title="登录">
            <router-link slot="left" to="/">返回</router-link>
        </v-header>
        <form class="login" v-on:submit.prevent="submit">
            <div class="line">
                <div v-show="btn && !form.id">id不能为空</div>
                <input placeholder="输入你的id" type="number" v-model="form.id">
            </div>
            <div class="line">
                <div v-show="btn && !form.name">用户名不能为空</div>
                <input placeholder="输入你的用户名" type="text" v-model="form.name">
            </div>
            <button>登录</button>
        </form>
    </div>
</template>
<script>
    import {mapActions} from 'vuex'
    import {USER_SIGNIN} from 'store/user'

    export default {
        data() {
            return {
                btn: false, //true 已经提交过， false没有提交过
                form: {
                    id: '',
                    name: ''
                }
            }
        },
        methods: {
            ...mapActions([USER_SIGNIN]),
            submit() {
                this.btn = true
                if (!this.form.id || !this.form.name) return
                this.USER_SIGNIN(this.form)
                this.$router.replace({path: '/home'})
            }
        }
    }
</script>