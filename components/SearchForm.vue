<template>
    <div>
    <div>Tiêu đề &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input style="width: 80%;" v-model="keySearch"></div><br>
    <button type="button" placeholder="Tiêu đề.." class="btn btn-success" @click="getKeySearch()">Search</button><br>
    </div>
</template>

<script>
export default {
    data (){
        return{
        keySearch : '',
        }
    },
    methods:{
        getKeySearch(){
            this.$emit('getKeySearch', this.keySearch)
        }
    }
}
</script>

<style>

</style>