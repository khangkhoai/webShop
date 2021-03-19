<template>
    <div>
        <AppHeader />
        <div class="row">
          <div class="col-sm-3">
            <AppMenu/>
          </div>
          <div class="col-sm-9">
             <h3>List Blogs</h3>
      <Table :dataBlog="listBlogs"/>    
          </div>
        
        </div>
          
    </div>
</template>
<script>
import AppHeader from '../components/AppHeader.vue'
import AppMenu from '../components/AppMenu.vue'
import Table from '../components/table-blog.vue'
export default {
  name: 'admin',
  components: {
    AppHeader,
    AppMenu,
    Table
  },
  data(){
    return {
      listBlogs : [],
    }
  },
}
</script>
<style scoped>
.col-sm-3{
  margin-top: 20px;
}
.col-sm-9{
    padding-right: 90px;
}
</style>