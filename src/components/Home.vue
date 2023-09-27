<template>
    <Header />
    <div class="container ">

        <h1 class="text-center">List of restaurant</h1>
        <div class="my-5 wrapper">
            <table class="table table-dark">
                <thead>
                    <tr>
                        <th scope="col">#</th>
                        <th scope="col">Restaurant</th>
                        <th scope="col">Address</th>
                        <th scope="col">Contact</th>
                        <th scope="col text-center">
                            <h6 class="text-center mb-0">Actions</h6>
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="items in restaurant" :key="items.id">
                        <th scope="row">{{ items.id }}</th>
                        <td>{{ items.name }}</td>
                        <td>{{ items.address }}</td>
                        <td>{{ items.contact }}</td>
                        <td>
                            <div class="wrapper">
                                <router-link :to="'/update/' + items.id">
                                    <i class="fa-solid fa-pen-to-square"></i>
                                </router-link>
                                <i class="fa-solid fa-trash-can mx-3 " style="color: #ea0634;"
                                    v-on:click="deletedata(items.id)"></i>
                            </div>

                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import Header from "./Header.vue"
export default {
    name: "Home",
    data() {
        return {
            restaurant: []
        }
    },
    components: {
        Header
    },
    methods: {
        async deletedata(id) {
            try {
                const res = await axios.delete(`http://localhost:3000/restaurant/${id}`)
                console.log(res, this.$data.restaurant.filter((el) => el.id !== id));
                this.$data.restaurant = this.$data.restaurant.filter((el) => el.id !== id)
            } catch (error) {

                console.log(error);
            }
        }
    },
    mounted() {
        if (!localStorage.getItem("userinfo")) {
            this.$router.push({ name: "SignUp" })
        }
        fetch("http://localhost:3000/restaurant", {
            method: "get"
        }).then((data) => data.json()).then((data) => this.$data.restaurant = data).catch((err) => console.log(err))
        // 
    }
}
</script>