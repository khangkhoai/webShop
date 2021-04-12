<template>
    <div>
        <h3>List Product</h3>
      <Table :dataBlog="listBlogs"/>    
     
    </div>
</template>
<script>
import Table from '@/components/blogs/ListBlog.vue'
import axios from 'axios'
export default {
  name: 'admin',
  components: {
    Table
  },
  data(){
    return {
      listBlogs : [],
      page: {},
      currentPage: 1,
    }
  },
  
  methods : {
    listData(){
      axios({method: 'GET',url: 'http://127.0.0.1:8000/api/product/',data: null}).then(res =>{this.listBlogs = res.data; 
      }).catch(err => {console.log(err)})
    }, 
  
  },
  mounted () {
    this.listData();
   
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