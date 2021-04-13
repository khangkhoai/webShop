<template>
 
    <!-- Section: Categories -->
    <section>
      <h5 style="margin-left: 50px;">Categories</h5>
      <div v-for="(dev, key) in listBlogs" :key="key" >
        <!-- <p class="mb-3"><a href="" class="card-link-secondary">{{dev.name}}</a></p> -->
        <li class="list-group-item"><nuxt-link :to="`/product_category/${dev.id}`"><button>{{dev.name}}</button></nuxt-link></li>
         
      </div>
    </section>
</template>

<script>
import axios from 'axios'
export default {
  name: 'AppMenu',
  data() {
    return {
      listBlogs: []
    }
  },
  methods: {
    getCategories() {
      axios({
        method: 'GET',
        url: 'http://127.0.0.1:8000/api/category/',
        data: null,
      })
        .then((res) => {
          this.listBlogs = res.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
  },
  mounted() {
    this.getCategories()
  },
}
</script>

<style>
.list-group-item {
  margin-left: 50px;
  margin-right: 40px;
  text-align: center;
}
.li button {
  background-color: white;
  font-weight: bold;
  border: 1px solid black;
  display: block;
}
button {
  background-color: white;
  border: none;
}
</style>
