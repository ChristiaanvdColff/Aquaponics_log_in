<template>
    <div id="app">
        <div id="nav">
            <router-link to="/">Home </router-link>
            |
            <router-link to="/">About </router-link>
            |
            <router-link to="/">Contact </router-link>
            |
            <router-link v-if="$auth.isAuthenticated" to="/"
                >My Profile</router-link
            >
        </div>
        <router-view />
        <div v-if="!$auth.loading">
            <button @click="login" v-if="!$auth.isAuthenticated">
                Login
            </button>

            <div  id="logged in" v-if="$auth.isAuthenticated">
            You have successfully Logged in!!

            <a href="http://127.0.0.1:1880/ui">click here</a>
        </div>
        
            <button @click="logout" v-if="$auth.isAuthenticated">
                Logout
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'App',
    methods: {
        login() {
            this.$auth.loginWithRedirect();
        },
        loginPopup() {
            this.$auth.loginWithPopup();
        },
        logout() {
            this.$auth.logout();
            this.$router.push({ path: '/' });
        }
    }
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

#nav {
    display: flex;
    justify-content: center;
    padding: 30px;
    text-decoration: none;
    text-transform: uppercase;
    font-size: 1em;
    letter-spacing: 0.2em;
    background-color: #3b5165;
    justify-content: right;
}

#nav a {
    font-weight: bold;
    color: #2c3e50;
    padding: 0 5px;
}
#nav a.router-link-exact-active {
    color: #42b983;
}
#nav a.router-link-exact-active:hover {
    color: #ffffff;
    transform: translateX(5px);
    transition: transform 0.5s;
}
button {
    padding: 5px 10px;
    background: #42b983;
    text-decoration: none;
    text-transform: uppercase;
    font-size: 1em;
    letter-spacing: 0.1em;
    padding: 10px 30px;
    transition: 0.5s;
}
button:hover {
    background: white;
    color: #42b983;
    background: var(--clr);
    color: var(--clr);
    box-shadow: 0 0 35px var(--clr);
    transform: translateX(5px);
    transition: transform 0.5s;
}
</style>
