<template>
    <header>
        <nav-bar :user="user"/>
        <div class="header-label">
            <h1>Ads Listings</h1>
            <p>Choose product you want</p>
        </div>
    </header>
</template>

<script>
    import NavBar from "./NavBar";

    export default {
        name: "PageHeader",
        components: {NavBar},
        props: {
            user: Object
        }
    }
</script>

<style scoped>
    header {
        min-height: 500px;
        height: 30vh;
        background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)), url(../assets/images/hero_1.jpg);
        background-position: 50% 0;
        background-size: cover;
        background-repeat: no-repeat;
    }

    .header-label {
        display: flex;
        flex-direction: column;
        padding-top: 180px;
        text-align: center;
    }

.header-label h1 {
    font-size: 3rem;
    font-weight: 400;
    color: #fff;
}
    .header-label p {
        color: rgba(255, 255, 255, 0.5);
        font-size: 1.2rem;
    }
</style>