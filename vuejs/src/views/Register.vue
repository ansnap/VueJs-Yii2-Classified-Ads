<template>
    <form @submit.prevent="register" class="form">
        <div v-if="errors" class="errors">
            <p v-for="(error, field) in errors" :key="field">
                {{error[0]}}
            </p>
        </div>
        <div>
            <label for="username">Имя пользователя</label>
            <input type="text" v-model="form.username" id="username">
        </div>
        <div>
            <label for="password">Пароль</label>
            <input type="password" v-model="form.password" id="password">
        </div>
        <div>
            <label for="password_repeat">Повторите пароль</label>
            <input type="password" v-model="form.password_repeat" id="password_repeat">
        </div>
        <p>
            Уже есть аккаунт?
            <router-link to="/login">Войти</router-link>
        </p>
        <div>
            <button>Зарегистрироваться</button>
        </div>
    </form>
</template>

<script>
    import authService from "../services/auth.service";

    export default {
        name: "Register",
        data() {
            return {
                form: {
                    username: '',
                    password: '',
                    password_repeat: ''
                },
                errors: null
            }
        },
        methods: {
            async register() {
                const {success, errors} = await authService.register(this.form);
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