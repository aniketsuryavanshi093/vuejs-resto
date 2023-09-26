<template>
    <h1>Home</h1>
</template>

<script>
    export default{
        name: "Home",
        mounted(){
            if(!localStorage.getItem("userinfo")){
                this.$router.push({name: "SignUp"})
            }
        }
    }
</script>