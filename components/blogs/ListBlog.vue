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
                <tr  v-for="(blogs,index) in dataBlog" :key="index">
                    <th scope="row">{{blogs.id}}</th>
                    <td>{{blogs.title}}</td>
                    <td>{{categories[blogs.category]}}</td>
                    <td>{{blogs.public == true ? "public" : "private"}}</td>
                    <td>{{filterPosition(blogs.position)}}</td>
                    <td>{{blogs.data_pubblic}}</td>
                    <td><nuxt-link :to="`/blog/${blogs.id}`">Edit</nuxt-link></td>
                    <td><button type="button" class="btn btn-outline-danger" @click="deletedBlog(blogs.id)">Delete</button></td>
                </tr>
             </tbody>
        </table>    
  </div>
</template>

<script>
import axios from 'axios'
import { CATEGORY } from "@/store/constant";
import { POSITION } from "@/store/constant";
export default {
  components : {
  },
  props: {
   dataBlog: {
      type: Array,
      default: () => [],
    },
  },
  data () {
    return {
      CATEGORY,
      POSITION
    }
  },
  mounted() {
    
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
    deletedBlog(blogId){
      if(confirm("Do you really want to delete?")){
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
      }
    },
    filterPosition(pos) {
      return pos
        .map((item) => {
          return this.POSITION[item];
        })
        .join(",");
    },
  }
}
</script>
<style>

</style>