<template>
    <form @submit.prevent="getUserInfo">
    <span class="at">@</span><input type="text" name="username" placeholder="Instagram Username(e.g: ohidurbappy)" v-model="username">

        <button type="submit">Submit</button>
    </form>
</template>


<script>
export default {
    name: 'InstagramUsernameInput',
    data(){
        return{
            username: ''
        }
        
    },
    methods:{
        getUserInfo(e){
            e.PreventDefault;

            this.$emit('get-user',this.username);

            

        }
    }
}
</script>

<style scoped>
.at{
    font-size: 22px;
    margin: 2px;
    margin-right: 10px;
}
form{
    text-align: center;

}

button{
    border: none;
      text-decoration: none;
    display: inline-block;
    background: #833ab4;
    color: white;
    padding: 8px;
    margin: 2px;
    font-size: 22px;
    font-family: Arial, Helvetica, sans-serif;
    border-radius: 5px;
    transition:linear 0.2s background;
    
}

button:hover{
    background:#c13584;
}

input{
    font-size: 22px;
    margin: 2px;
    padding: 4px;
    width: 60%;
    max-width: 400px;
    
}
</style>