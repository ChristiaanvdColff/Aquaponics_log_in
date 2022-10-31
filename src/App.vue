<template>
    <div id="app">
        <div id="nav">
            <img id="fish" src="./assets/fish.png" />
            <h2>AQUAPONICS</h2>
            <!-- <router-link v-if="$auth.isAuthenticated" to="/"> </router-link> -->
            <img id="profile" src="./assets/user-profile.png" />
            <!-- <router-link v-if="$auth.isAuthenticated" to="/"> </router-link> -->
            <img id="bell" src="./assets/bell.png" />
        </div>
        <router-view />
        <div v-if="!$auth.loading">
            <button @click="login" v-if="!$auth.isAuthenticated">
                Login
            </button>

            <div id="logged in" v-if="$auth.isAuthenticated">
                <button href="http://127.0.0.1:1880/ui">View Live Data</button>
            </div>
            <div id="logout">
                <button @click="logout" v-if="$auth.isAuthenticated">
                    Logout
                </button>
            </div>
        </div>
        <div id="footer">
            <img id="fish2" src="./assets/fish2.png" />
            <h5>AQUAPONICS</h5>
            <h4>© 2022 AQUAPONICS, all rights reserved</h4>
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
    font-family: 'Jost';
    display: flex;
    justify-content: center;
    padding: 30px;
    text-decoration: none;
    text-transform: uppercase;
    font-size: 1em;
    letter-spacing: 0.2em;
    background-color: #fff;
    justify-content: right;
}
#nav a {
    font-weight: bold;
    color: #42b983;
    padding: 0 5px;
}
#nav a.router-link-exact-active {
    color: #2c3e50;
}
#nav a.router-link-exact-active:hover {
    color: #42b983;
    transform: translateX(5px);
    transition: transform 0.5s;
}
#profile {
    position: absolute;
    width: 25px;
    height: 25px;
    left: 1430px;
    top: 35px;
}
#bell {
    position: absolute;
    width: 25px;
    height: 25px;
    left: 1480px;
    top: 35px;
}
#footer {
    font-family: 'Jost';
    background-color: #2c3e50;
    justify-content: right;
    position: fixed;
    left: 0;
    bottom: 0;
    width: 100%;
    text-align: center;
    color: #fff;
}
button {
    font-family: 'Jost';
    padding: 5px 10px;
    background: #42b983;
    color: #0e2a47;
    text-decoration: none;
    text-transform: uppercase;
    font-size: 1em;
    letter-spacing: 0.1em;
    padding: 10px 30px;
    transition: 0.5s;
    border-radius: 25px;
}
button:hover {
    background: #0e2a47;
    color: #fff;
    box-shadow: 0 0 35px var(--clr);
    transform: translateX(5px);
    transition: transform 0.5s;
}
#fish {
    position: absolute;
    width: 310px;
    height: 281px;
    left: -85px;
    top: -97px;
    transform: matrix(-1, 0, 0, 1, 0, 0);
}
#fish2 {
    position: absolute;
    width: 150px;
    height: 86.14px;
    left: 939px;
    top: 1893px;

    transform: matrix(-1, 0, 0, 1, 0, 0);
}
h2 {
    position: absolute;
    width: 244px;
    height: 46px;
    left: 125px;
    top: 1px;

    font-family: 'Jost';
    font-style: normal;
    font-weight: 600;
    font-size: 32px;
    line-height: 46px;
    display: flex;
    align-items: center;
    text-align: center;
    letter-spacing: 0.1em;

    color: #0e2a47;
}
#logout {
    margin-top: 15px;
}
</style>
