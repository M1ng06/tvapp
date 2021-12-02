<template>
    <div style="width:300px" class="card">
        <img class="card-img-top" style="width:100%" v-bind:src = tvobj.imgsrc>
        <div  class="card-body">
              <h4 class="card-title">{{tvobj.title}}</h4>
              <p class="card-text">{{tvobj.overview}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TV',
    props: ['tvobj'],
}
</script>
<style scoped>
.card{
margin-bottom: 20px;
}
</style>>
