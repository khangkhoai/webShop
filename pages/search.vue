<template>
    <div>
        <AppHeader />
        <div class="row">
          <div class="col-sm-3">
            <AppMenu/>
          </div>
          <div class="col-sm-9">
            <h3>Search Blog</h3><br>
            <div>Tiêu đề &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input style="width: 80%;"></div><br>
            <button type="button" placeholder="Tiêu đề.." class="btn btn-success">Search</button><br>
            <br>
            <Table/>
          </div>
        
        </div>
          
    </div>
</template>
<script>
import AppHeader from '../components/AppHeader.vue'
import AppMenu from '../components/AppMenu.vue'
import Table from '../layouts/Table.vue'
export default {
  name: 'admin',
  components: {
    AppHeader,
    AppMenu, 
    Table
  }
}
</script>
<style scoped>
.col-sm-3{
  margin-top: 20px;
  
}
.input {
    text-align: left;
}
button{
    background-color: #28a745;
}
.col-sm-9{
    padding-right: 90px;
}
</style>