<template>
  <div>
    <br />
    
    <Table :dataBlog="listBlogs" />
    <b-pagination
      v-model="currentPage"
      :total-rows="page.total"
      :per-page="page.per_page"
      @page-click="listData"
      prev-text="Prev"
      next-text="Next"
    ></b-pagination>
  </div>
</template>
<script>
import Table from '@/components/blogs/ListBlog.vue'


import axios from 'axios'
export default {
  name: 'admin',
  components: {
    Table,
   
  },
  data() {
    return {
      listBlogs: [],
      result: [],
       page: {},
      currentPage: 1,
    }
  },

  methods: {
    listData(e, page) {
      axios({
        method: 'GET',
        url: 'http://127.0.0.1:8000/api/product?page=' +page,
        data: null,
      })
        .then((res) => {
          this.listBlogs = res.data.data
          this.page = res.data;
        })
       
    },
    
  },
  mounted() {
    this.listData()
  },
}
</script>
<style scoped>
.col-sm-3 {
  margin-top: 20px;
}
.col-sm-9 {
  padding-right: 90px;
}
</style>
