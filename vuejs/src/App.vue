<template>
    <div id="app">
        <page-header :user="user"/>
        <div class="container">
            <router-view/>
        </div>
        <page-footer/>
    </div>
</template>

<script>
    import PageHeader from "./components/PageHeader";
    import PageFooter from "./components/PageFooter";
    import authService from "./services/auth.service";

    export default {
        components: {PageFooter, PageHeader},
        data() {
            return {
                user: {}
            }
        },
        async mounted() {
            this.user = await authService.getUser();
        }
    }
</script>

<style>
    body {
        margin: 0;
        font-family: Arial, Helvetica, sans-serif;
        background: #f8f9fa;
    }

    .container {
        max-width: 1140px;
        margin: 0 auto;
    }

    a {
        color: #30e3ca;
    }

    a:hover {
        color: #18af9a;
    }

    .form {
        background-color: white;
        padding: 3rem;
        width: 50%;
        margin: 80px auto;
    }

    .form > div {
        margin-bottom: 1.5rem;
    }

    .form input {
        border: 1px solid #ced4da;
        height: 28px;
        display: block;
        width: calc(100% - 1.5rem);
        padding: 0.375rem 0.75rem;
    }

    .form input:focus {
        border-color: #30e3ca;
    }

    .form label {
        display: inline-block;
        margin-bottom: 0.7rem;
    }

    .form input, button {
        font-size: 1rem;
        outline: 0;
    }

    button {
        color: white;
        padding: 0.5rem 1.5rem;
        border: 1px solid #30e3ca;
        background-color: #30e3ca;
        cursor: pointer;
        transition: background-color 0.15s ease-in-out, border-color 0.15s ease-in-out;
    }

    button:hover {
        background-color: #1cd1b7;
        border-color: #1bc5ad;
    }

    .form .errors {
        padding: 5px;
        background-color: #a94442;
        color: #fff;
    }
</style>
