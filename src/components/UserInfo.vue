<template>
    <div class="container">

        <div class="image-container">

            <img class="profile_picture" v-bind:src="info.profile_pic_url" width="100px" height="100px" alt="">

            <h6>{{info.full_name}}</h6>
            <p style="color:#c2c;">{{info.biography}}</p>

        </div>

        <p>ID: {{info.id}}</p>
        <p>Username: {{info.username}}</p>

        <p v-if="info.is_private">
            Account type: Private
        </p>
        <p v-else>
            Account type: Public
        </p>
        
        <p>Fullname: {{info.full_name}}</p>
        <p>Followers: {{info.edge_followed_by.count}}</p>
        <p>Following: {{info.edge_follow.count}}</p>
        <p>Website: <a v-bind:href="info.external_url">{{info.external_url}}</a></p>

    </div>
</template>]



<script>
export default {
    name:'UserInfo',
    props:["info"]
}
</script>


<style scoped>

.image-container{
    text-align: center;
}

.container{
    padding-top: 20px;
    margin:12px;
    width:80%;
    max-width: 600px;
    margin: auto;
}

.profile_picture{
    border-radius: 50%;
}

*{
    margin:0;
    padding: 2px;
    font-size: 22px;
}

</style>