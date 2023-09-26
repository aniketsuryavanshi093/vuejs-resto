<template >
    <div class="wrapper flex-column mt-5 signupwrapper">
        <div class="wrapper flex-column w-100">
            <img src="../assets/Restaurant.webp" class="logo" alt="logo" />
            <h2>Sign Up</h2>
        </div>
        <div class="wrapper flex-column w-100 mt-3">
            <input type="text" v-model="name" placeholder="Enter Name" class="form-control" />
            <input type="text" v-model="email" placeholder="Enter Email" class="form-control my-3" />
            <input type="password" v-model="password" placeholder="Enter Password" class="form-control" />
            <button type="button" v-on:click="signUp" class="btn btn-success mt-4 cp"> Sign Up </button>
        </div>
    </div>
</template>

<script>
import axios from "axios"
export default {
    name: "SignUp",
    data(){
        return {
            name: "",
            email: "",
            password: ""
        }
    },
    methods: {
        async signUp(){
            console.log({
                    email: this.$data.email,
                    password: this.$data.password,
                    name: this.$data.name,
                });
            const result = await axios.post("http://localhost:3000/users" ,  {
                    email: this.$data.email,
                    password: this.$data.password,
                    name: this.$data.name,
                },
            )
            localStorage.setItem("userinfo",JSON.stringify(result.data))
           this.$router.push({name: "Home"})
        },
    }
}
</script>


<style>
.logo {
    width: 100px;
}

.signupwrapper {
    width: 25%;
}
</style>