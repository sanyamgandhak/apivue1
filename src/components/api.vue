<template>
  <div class="content">
           <button @click="created()">get request</button>
         
    <button @click="put()">put request</button>
    <button @click="post()">post request</button>
    <button @click="patch()">patch request</button>
    <button @click="delet()">delete request</button><hr>
    <label>Enter User To ADD</label>
    <input type="text" v-model="newUser" @keyup="addUser">
       <li>{{datas}}</li>
   
               
  
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: 'api',
  data(){
      return{
          datas:[],
          newUser:''
      }
  },
mounted(){

},
methods:{
  created() {
    axios.get("https://reqres.in/api/users?page=2").then((result) => {
      console.log(result.data);
      this.datas = result.data
    })
  },
  put() {
    axios.put("https://reqres.in/api/users/2",{
        "name":"rama",
        "job":"leader"
    }).then((result) => {
      console.log(result.data);
      this.datas = result.data
    })
  },
   post() {
    axios.post("https://reqres.in/api/users",{
        "name":"rama",
        "job":"leader"
    }).then((result) => {
      console.log(result.data);
      this.datas = result.data
    })
  },
   patch() {
    axios.patch("https://reqres.in/api/users/2",{
        "name":"rama",
        "job":"notleader"
    }).then((result) => {
      console.log(result.data);
      this.datas = result.data
    })
   },
    delet() {
    axios.delete("https://reqres.in/api/users/2").then((result) => {
      console.log(result.data);
      this.datas = result.data
    })
  },
  addUser(){
      axios.post("https://reqres.in/api/users",{
          name:this.newUser
      }).then((result)=>{
          const data =result.data;
          this.datas.push(data);
          this.newUser=""
      })
  }
}
};

</script>

<style scoped lang="scss">
</style>
