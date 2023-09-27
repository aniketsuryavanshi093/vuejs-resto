<template>
    <Header />
    <div class="container ">
        <p class="mb-0 text-center mt-3">Hello {{ name }} !</p>
        <h1 class="text-center mt-4"> Add restaurant</h1>
        <div class="w-100 ">
            <div class="wrapper restaurantform my-5 flex-column mt-3">
                <input type="text" v-model="restaurant.name" placeholder="Restaurant Name" class="form-control" />
                <input type="text" v-model="restaurant.contact" placeholder="Contact No." class="form-control my-3" />
                <input type="text" v-model="restaurant.address" placeholder="Enter Address" class="form-control" />
                <button type="button" v-on:click="createRestaurant" class="btn btn-success mt-4 cp"> Create Restaurant
                </button>
            </div>
        </div>

    </div>
</template>

<script>
import axios from "axios"
import Header from "./Header.vue"
export default {
    name: "AddRestaurant",
    data() {
        return {
            name: "",
            restaurant: {
                name: "",
                address: "",
                contact: "",
            }
        }
    },
    methods: {
        async createRestaurant() {
            try {
                const res = await axios.post("http://localhost:3000/restaurant", {
                    name: this.$data.restaurant.name,
                    address: this.$data.restaurant.address,
                    contact: this.$data.restaurant.contact
                })
                this.$router.push({ name: "Home" })
                console.log(res)
            } catch (error) {
                console.log()
            }
        }
    },
    components: {
        Header
    },
    mounted() {
        this.$data.name = JSON.parse(localStorage.getItem("userinfo")).name
        if (!localStorage.getItem("userinfo")) {
            this.$router.push({ name: "Login" })
        }
    }
}
</script>

<style>
.restaurantform {
    margin: auto;
    width: 300px;
}
</style>