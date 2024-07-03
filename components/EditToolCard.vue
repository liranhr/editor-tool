<template>
    <div class="item">
        <h3>{{lable}}</h3>
        <hr>
    </div>
</template>

<script>
export default {
    props:{
        lable: String
    }
}
</script>

<style>
.item{
    border: 1px solid black;
    border-radius: 10px;
    background-color: white;
    margin: 15px;
    width: 35rem;
    height: 14rem;
}
</style>