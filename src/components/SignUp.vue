<template>
    <img alt="Vue logo" src="../assets/resto-logo.png">
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" placeholder="Enter Name" v-model="name">
        <input type="text" placeholder="Enter Email" v-model="email">
        <input type="password" placeholder="Enter password" v-model="password">
        <button v-on:click="signUp">Sign Up</button>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'SignUp',
    data() {
        return {
            name: "",
            email: "",
            password: ""
        }
    },
    methods: {
        async signUp() {
            console.warn("result");
            const result = await axios.post("http://localhost:3000/users", {
                name: this.name,
                email: this.email,
                password: this.password
            });
            if(result.status === 201) {
                alert("sign-up done");
                localStorage.setItem("userInfo", JSON.stringify(result.data))
            }
        }
    }
}
</script>
<style lang="scss">
.logo {
    width: 100px;
}
.register {
    input {
        width: 300px;
        height: 40px;
        padding-left: 20px;
        display: block;
        margin-bottom: 30px;
        margin-right: auto;
        margin-left: auto;
        border: 1px solid skyblue; 
    }
    button {
        width: 320px;
        height: 40px;
        border: 1px solid skyblue;
        background: skyblue;
        color: #fff;
        cursor: pointer;
    }
}
</style>