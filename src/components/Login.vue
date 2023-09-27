<template>
    <div class="app-wrapper wrapper">
        <div class="wrapper flex-column mt-5 signupwrapper">
            <div class="wrapper flex-column w-100">
                <img src="../assets/Restaurant.webp" class="logo" alt="logo" />
                <h2>Login</h2>
            </div>
            <div class="wrapper flex-column w-100 mt-3">
                <input type="text" v-model="email" placeholder="Enter Email" class="form-control my-3" />
                <input type="password" v-model="password" placeholder="Enter Password" class="form-control" />
                <button type="button" v-on:click="login" class="btn btn-success mt-4 cp"> Login </button>
                <p>
                    <router-link to="/sign-up">Sign up</router-link>
                </p>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios"
export default
    {
        name: "Login",
        methods: {
            async login() {
                const result = await axios.get(`http://localhost:3000/users?email=${this.$data.email}&password=${this.$data.password}`)
                if (result.data.length > 0) {
                    localStorage.setItem("userinfo", JSON.stringify(result.data[0]));
                    this.$router.push({ name: "Home" })
                } else {
                    alert("invalid credentials!")
                }
            }
        },
        data() {
            return {
                email: "",
                password: ""
            }
        },
        mounted() {
            if (localStorage.getItem("userinfo")) {
                this.$router.push({ name: "Home" })
            }
        }
    }
</script>