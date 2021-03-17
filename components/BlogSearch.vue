<template>
    <div>
        <AppHeader />
        <div class="row">
          <div class="col-sm-3">
            <AppMenu/>
          </div>
          <div class="col-sm-9">
            <h3>Search Blog</h3><br>
            <div>Tiêu đề &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input style="width: 80%;" v-model="keySearch"></div><br>
            <button type="button" placeholder="Tiêu đề.." class="btn btn-success" @click="searchTitle(keySearch)">Search</button><br>
            <br>
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
                <tr  v-for="blogs in result" :key="blogs.id">
                    <th scope="row">{{blogs.id}}</th>
                    <td>{{blogs.title}}</td>
                    <td>2</td>
                    <td>{{blogs.public}}</td>
                    <td></td>
                    <td>{{blogs.data_pubblic}}</td>
                    <td><a href="/edit">Edit</a></td>
                    <td><button type="button" class="btn btn-outline-danger" @click="deletedBlog(blogs.id)">Delete</button></td>
                </tr>
             </tbody>
        </table>
          </div>
        
        </div>
          
    </div>
</template>
<script>
import AppHeader from '../components/AppHeader.vue'
import AppMenu from '../components/AppMenu.vue'
import table from '../components/table-blog.vue'
import axios from 'axios'
export default {
  name: 'admin',
  data (){
    return {
      title : '',
      dataBlog : [],
      result : [],
      keySearch :'',
    }
  },
  mounted() {
    this.listData();
  },
  components: {
    AppHeader,
    AppMenu, 
    table
  },
  methods:{
    listData(){
      axios({method: 'GET',url: 'http://localhost:3000/blogs',data: null}).then(res =>{this.dataBlog = res.data; this.result= this.dataBlog
      }).catch(err => {console.log(err)})
    }, 
    searchTitle(keySearch){
      // this.dataBlog = this.dataBlog.filter(blog => blog.title.includes(keySearch))
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