<template>
    <div>
         <h3>Search Blog</h3><br>
          <SearchForm @getKeySearch=searchTitle></SearchForm>
          <br>
          <Table :dataBlog="listBlogs"/>
    </div>
</template>
<script>
import SearchForm from '../components/SearchForm.vue'
import Table from '../components/table-blog.vue'

export default {
   
  data (){
    return {
      dataBlog : [],
      result : [],
    }
  },
  components: {
    SearchForm,
    Table
  },
  methods:{
    searchTitle(keySearch){
      this.result = keySearch
      ? this.dataBlog.filter((blog) => blog.title.includes(keySearch))
      : this.dataBlog 
      console.log(this.result);
    }
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
btn btn-success{
    background-color: #28a745;
}
.col-sm-9{
    padding-right: 90px;
}
</style>