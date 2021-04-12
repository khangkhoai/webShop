<template>
   <div>
     <div class="row">
        <div v-for="(dev, key) in dataBlog" :key="key" class="col-sm-4">
          <div class="card">
            <img v-bind:src="'http://127.0.0.1:8000/' + dev.thumb"  alt="" width="1%"
                height="1%"  class="c-sidebar-brand-full img-fluid w-100">
            <div class="card-body">
                <h5 class="card-title">{{ dev.name }}</h5>
                <p class="card-text">{{ dev.id }}</p>
                <nuxt-link :to="`/product/${dev.id}`" class="btn btn-primary"> Detail</nuxt-link>
            </div>
          </div>
          <br/>
        </div>
      </div>    
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
        axios.delete('http://127.0.0.1:8000/api/blogs/' + blogId).then(response => {
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