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
                <button type="button" v-on:click="UpdateRestaurant" class="btn btn-success mt-4 cp"> update Restaurant
                </button>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import Header from "./Header.vue"
export default {
    name: "UpdateRestaurant",
    data() {
        return {
            restaurant: {
                name: "",
                address: "",
                contact: "",
            }
        }
    },
    components: {
        Header
    },
    methods: {
        async UpdateRestaurant() {
            try {
                const res = await axios.put(`http://localhost:3000/restaurant/${this.$route.params.id}`, this.$data.restaurant)
                this.$router.push({ name: "Home" })
            } catch (error) {
                console.log(error)
            }
        }
    },
    async mounted() {
        if (!localStorage.getItem("userinfo")) {
            this.$router.push({ name: "Login" })
        }
        const res = await axios.get(`http://localhost:3000/restaurant/${this.$route.params.id}`)
        this.$data.restaurant = res.data
    }
}
</script>