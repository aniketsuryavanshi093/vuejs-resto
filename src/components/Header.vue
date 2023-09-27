<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <a class="navbar-brand" href="#">Navbar</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item active">
                    <router-link class="nav-link" to="/"><Span> Home </span></router-link>
                </li>
                <li class="nav-item active">
                    <router-link class="nav-link" to="/add">Add Restaurant</router-link>
                </li>
                <li class="nav-item active">
                    <router-link class="nav-link" to="/update">Update Restaurant</router-link>
                </li>
            </ul>
            <div class="form-inline my-2 my-lg-0">
                <button class="btn btn-outline-secondary my-2 my-sm-0" v-on:click="logout" type="button">Logout</button>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    name: "Header",
    methods: {
        logout() {
            localStorage.clear()
            this.$router.push({ name: "Login" })
        }
    }
}
</script>