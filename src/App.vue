<template>
  <div id="app">
  <Header />
  <InstagramUsernameInput v-on:get-user="getUserInfo" />



  <div v-if="pagenotfound || notInitiated">
    <NotFound v-bind:notInitiated="notInitiated" />
  </div>
  <div v-else>
    <UserInfo v-bind:info="info" />
  </div>

   
  </div>
</template>

<script>

import Header from './components/Header';
import InstagramUsernameInput from './components/InstagramUsernameInput';
import UserInfo from './components/UserInfo';
import axios from 'axios';
import NotFound from './components/NotFound'




export default {
  name: 'App',
  data(){
     return{
       notInitiated:true,
       pagenotfound:false,
       info:{
         username:''
       }
     }
    },
  components: {
    Header,
    InstagramUsernameInput,
    UserInfo,
    NotFound
  },
  methods:{
    getUserInfo(username){


      (async()=>{
        try{
        axios.get( `https://www.instagram.com/${username}?__a=1`,{validateStatus:false})
      .then((response)=>{
        console.log(response);

        if (response.status===200){
           this.info=response.data.graphql.user;
           this.pagenotfound=false;
           this.notInitiated=false;
        }else{
          this.pagenotfound=true;
          this.info={};
          this.notInitiated=false;
        }

       

      })
      .catch((error)=>{
        if (error.response.status==200){
          this.pagenotfound=true;
          this.info={};
          this.notInitiated=false;
        }
      });
      }catch(err){
          this.pagenotfound=true;
          this.info={};
          this.notInitiated=false;
      }
      })();

  
      console.log(username)

    },

    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
