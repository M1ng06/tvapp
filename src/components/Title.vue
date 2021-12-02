<template>
<div>
    <h1>{{title}}</h1>
</div>
    
</template>

<script>
export default {
    name:'Title',
    props:['title']
}
</script>

<style scoped>
*{
    box-sizing: border-box;
}
.title{
    background-color: grey;
    color: white;
    padding: 10px;
    text-align: center;
}
    
</style>