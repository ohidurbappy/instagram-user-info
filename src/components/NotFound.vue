<template>

    <div v-if="notInitiated">
        <h2>
            Enter a username and press 'Submit'
        </h2>
    </div>
    <div v-else><h2>Page not found</h2></div>
</template>


<script>
export default {
    name:'NotFound',
    props:["notInitiated"]
}
</script>

<style scoped>
h2{
     text-align: center;
    padding: 12px;
}
h2:nth-child(0){
    color: #cc224d
}
h2:nth-child(1){
    color: #5437f6;
}
</style>