<template>
  <div class="row">
        <table class="table table-bordered">
            <thead class="thead">
                <tr>
                    <th scope="col">ID</th>
                    <th scope="col">Tin</th>
                    <th scope="col">Loại</th>
                    <th scope="col">Trạng thái</th>
                    <th scope="col">Vị trí</th>
                    <th scope="col">Ngày public</th>
                    <th scope="col">Edit</th>
                    <th scope="col">Delete</th>
                </tr>
            </thead>
             <tbody>
                <tr  v-for="blogs in dataBlog" :key="blogs.id">
                    <th scope="row">{{blogs.id}}</th>
                    <td>{{blogs.title}}</td>
                    <td>2</td>
                    <td>{{blogs.public}}</td>
                    <td></td>
                    <td>{{blogs.data_pubblic}}</td>
                    <td><nuxt-link :to="`/${blogs.id}`">Edit</nuxt-link></td>
                    <td><button type="button" class="btn btn-outline-danger" @click="deletedBlog(blogs.id)">Delete</button></td>
                </tr>
             </tbody>
        </table>
    
  </div>
</template>

<script>
import axios from 'axios'
export default {
  components : {
  },
  data(){
    return {
      dataBlog : [],
    }
  },
  mounted() {
    this.listData();
  },
  computed: {
    
  },
  methods:{
    listData(){
      axios({method: 'GET',url: 'http://localhost:3000/blogs',data: null}).then(res =>{this.dataBlog = res.data;
      }).catch(err => {console.log(err)})
    }, 
    deletedBlog(blogId){
       axios.delete('http://localhost:3000/blogs/' + blogId)
                .then(response => {
                    this.dataBlog.splice((blogId-1), 1)
                });
                console.log(this.dataBlog);
    }
  }
}

</script>

<style>

</style>