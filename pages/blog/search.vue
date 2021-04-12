<template>
    <div>
         <h3>Search Blog</h3><br>
          <SearchForm @getKeySearch=searchTitle></SearchForm>
          <br>
          <Table :dataBlog="result"/>
          
    </div>
</template>
<script>
import SearchForm from '@/components/blogs/SearchForm.vue'
import Table from '@/components/blogs/ListBlog.vue'
import axios from 'axios'
export default {
  data (){
    return {
      dataBlog : [],
      result : [],
     
    }
  },
   mounted() {
    
  },
  components: {
    SearchForm,
    Table
    },
  methods:{
    
    searchTitle(keySearch){
      
      console.log(this.result)
      const url =  'http://127.0.0.1:8000/api/blogs/search/' + keySearch;
      axios
        .get(url)
        .then((res) => {
          this.result = res.data;
        });
       
      // ? this.dataBlog.filter((blog) => blog.title.includes(keySearch))
      // : this.dataBlog 
      // console.log(this.result);
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