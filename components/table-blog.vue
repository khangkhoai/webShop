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
                    <td>{{categories[blogs.category]}}</td>
                    <td>{{blogs.public}}</td>
                    <td>{{positions[blogs.position]}}</td>
                    <td>{{blogs.data_pubblic}}</td>
                    <td><nuxt-link :to="`/blog/edit/${blogs.id}`">Edit</nuxt-link></td>
                    <td><button type="button" class="btn btn-outline-danger" @click="deletedBlog(blogs.id)">Delete</button></td>
                </tr>
             </tbody>
        </table>    
  </div>
</template>

<script>
import axios from 'axios'
import { CATEGORY } from "../store/constant";
import { POSITION } from "../store/constant";
export default {
  components : {
  },
  props: {
    dataBlog: {},
  },
  data () {
    return {
      CATEGORY,
      POSITION
    }
  },
  mounted() {
    this.listData();
  },
  computed : {
    categories(){
      return this.CATEGORY
    },
    positions(){
      return this.POSITION
    }
  },
  methods:{
    listData(){
      axios({method: 'GET',url: 'http://localhost:3000/blogs',data: null}).then(res =>{this.dataBlog = res.data; this.result= this.dataBlog
      }).catch(err => {console.log(err)})
    }, 
    deletedBlog(blogId){
      const index = this.dataBlog.findIndex((element, index) => {
        if(element.id === blogId) 
        {
        return true 
        }
      })
      axios.delete('http://localhost:3000/blogs/' + blogId).then(response => {
        this.dataBlog.splice((index), 1)
        });
      console.log(this.dataBlog);
    },
  }
}
</script>
<style>

</style>