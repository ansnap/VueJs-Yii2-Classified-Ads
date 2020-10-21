<template>
    <form @submit.prevent="login" class="form">
        <div v-if="errors" class="errors">
            <p v-for="(error, field) in errors" :key="field">
                {{error[0]}}
            </p>
        </div>
        <div>
            <label for="username">Username</label>
            <input type="text" v-model="form.username" id="username">
        </div>
        <div>
            <label for="password">Password</label>
            <input type="password" v-model="form.password" id="password">
        </div>
        <p>
            Нет аккаунта?
            <router-link to="/register">Зарегистрироваться</router-link>
        </p>
        <div>
            <button>Войти</button>
        </div>
    </form>
</template>

<script>
    import authService from "../services/auth.service";

    export default {
        name: "Login",
        data() {
            return {
                form: {
                    username: '',
                    password: ''
                },
                errors: null
            }
        },
        methods: {
            async login() {
                const {success, errors} = await authService.login(this.form);
                if (success) {
                    this.$router.push({name: 'Home'});
                } else {
                    this.errors = errors;
                }
            }
        }
    }

</script>

<style scoped>

</style>