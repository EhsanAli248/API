<template>
<img alt="Vue logo" src="./assets/logo.png"><br><br>
<!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
<!-- <h1>Calling API Lecture</h1> -->
<!-- <table   v-for="item in list" :key="item">
  <img :src="item.avatar"/>
  <td>
    <tr>{{item.id}}</tr>
  </td>
  <td>
    <tr>{{item.first_name}}</tr>
  </td>
  <td>
    <tr>{{item.last_name}}</tr>
  </td>
  <td>
    <tr>{{item.email}}</tr>
  </td>
 
 
 
      
    </table> -->
    <input type="tex" name="email" placeholder="Please enter your Email" v-model="email"/><br><br>
    <input type="password" name="password" placeholder="Please enter your password" v-model="password"><br><br>
    <button type="submit" @click="adduser()">Add User</button>
    

</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios';
export default {
    name: 'App',
    components: {
        // HelloWorld
    },
    data() {
        return {
            // list: []
            email:'',
            password:''
        }
    },
    // async mounted() {
    //     let result = await axios.get("https://reqres.in/api/users?page=1");
    //     console.warn("API Data", result.data.data);
    //     this.list = result.data.data;
    // }
    methods:{
      async adduser(){
        console.warn(this.email,this.password)
        let result= await axios.post("https://reqres.in/api/users?page=1",{
          email:this.email,
          password:this.password
        });
        console.warn("result:", result)
        this.email=''
        this.password=''
      }
    }
    
    
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

.item {
    border: '20px';
    color: blue;
    padding: 10px;
    text-align: center;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
.item img{
  width: 50px;
  height: 50px;
}
</style>
