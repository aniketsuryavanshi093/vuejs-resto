<template >
    <div class="wrapper flex-column mt-5 signupwrapper">
        <div class="wrapper flex-column w-100">
            <img src="../assets/Restaurant.webp" class="logo" alt="logo" />
            <h2>Sign Up</h2>
        </div>
        <div class="wrapper flex-column w-100 mt-3">
            <input type="text" placeholder="Enter Name" class="form-control" />
            <input type="text" placeholder="Enter Email" class="form-control my-3" />
            <input type="password" placeholder="Enter Password" class="form-control" />
            <button type="button" class="btn btn-success mt-4 cp"> Sign Up </button>
        </div>
    </div>
</template>

<script>
export default {
    name: "SignUp"
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