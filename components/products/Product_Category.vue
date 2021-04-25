<template>
  <div>
    <Table :dataBlog="listBlogs" />
  </div>
</template>
<script>
import Table from '@/components/products/ListProduct'
import axios from 'axios'
export default {
  name: 'admin',
  components: {
    Table,
  },
  data() {
    return {
      listBlogs: [],
      page: {},
      currentPage: 1,
    }
  },

  methods: {
    listData(id) {
      axios({
        method: 'GET',
        url: 'http://127.0.0.1:8000/api/category/get/' +id,
      })
        .then((res) => {
          this.listBlogs = res.data
        })
        .catch((err) => {
          console.log(err)
        })
        console.log(this.listBlogs)
    },
  },
  mounted() {
    if (this.$route.params.id != null) {
    this.listData(this.$route.params.id);   
    } 
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
