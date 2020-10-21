<template>
    <nav>
        <div>
            <router-link to="/" class="site-logo">Classy<span>Ads</span></router-link>
        </div>

        <div v-if="user">
            Привет, {{ user.username }}!
            <a href="javascript:void(0)" @click="logout">Выйти</a>
            <router-link to="/post" class="nav-btn">+ Опубликовать</router-link>
        </div>
        <div v-else>
            <router-link to="/about">О сайте</router-link>
            <router-link to="/login">Вход</router-link>
            <router-link to="/register">Регистрация</router-link>
        </div>
    </nav>
</template>

<script>
    import authService from "../services/auth.service";

    export default {
        name: "NavBar",
        props: {
            user: Object
        },
        methods: {
            logout() {
                authService.logout();
            }
        }
    }
</script>

<style scoped>
    nav {
        position: absolute;
        top: 20px;
        left: 50%;
        transform: translateX(-50%);
        width: 100%;
        max-width: 1140px;
        padding: 23px 30px;
        z-index: 1999;
        border-radius: 4px;
        background-color: #fff;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    nav a {
        color: #000;
        text-decoration: none;
        margin-right: 1em;
    }

    nav a:hover {
        color: #30e3ca;
    }

    .site-logo {
        font-size: 20px;
        font-weight: 900;
        text-transform: uppercase;
        color: #000;
        text-decoration: none;
    }

    .site-logo:hover {
        color: #000;
    }

    .site-logo span {
        color: #30e3ca;
    }

    .nav-btn, .nav-btn:hover {
        padding: 12px 20px;
        color: #fff;
        border-radius: 0.25rem;
        background-color: #30e3ca;
    }
</style>