<template>
  <div class="blogNew">
    <h3>New Blog</h3>
    <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
    {{ errors.title }}
    </p>
    <p>Tiêu đề</p>
    <input type="text" style="width: 50%;" v-model="dataBlog.title">
    <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
    {{ errors.des }}
    </p>
    <p>Mô tả ngắn</p>
    <input type="text" style="width: 50%;" v-model="dataBlog.des"><br>
    <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
    {{ errors.detail }}
    </p>
    <p>Mô tả chi tiết</p>
    <textarea name="" id="" cols="30" rows="10" style="width: 50%;" v-model="dataBlog.detail"></textarea><br>
    <p>Hình ảnh </p>
    <input type="file" name="thumps" id="" /><br><br>
    <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
    {{ errors.category }}
    </p>
    <p>Loại</p>
    <select v-model="dataBlog.category">
    <option v-for="(cate, index) in CATEGORY" :key="index" :value="index">{{cate}}</option>                      
    </select><br>
    <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">            
    {{ errors.position }}              
    </p><br>            
    <p>Vị trí</p>                        
    <ul class="list-group list-group-flush">           
      <li v-for="(post,key) in POSITION" :key="post" class="list-group-control">
        <div class="custom-control custom-checkbox">
          <input type="checkbox" :value="key" class="custom-control-input" :id="'check' + key + 1" v-model="dataBlog.position">
          <label class="custom-control-label" :for=" 'check' + key + 1">{{ post }}</label>
        </div>
      </li>
    </ul>
    <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">            
    {{ errors.public }}              
    </p><br>            
    <p>Public</p>            
    <input type="radio" id="checkbox1" name="yes" :value="true" v-model="dataBlog.public"><label for="checkbox1">Yes</label><br>
    <input type="radio" id="checkbox2" name="no" :value="false" v-model="dataBlog.public"><label for="checkbox2">No</label><br>
    <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
    {{ errors.data_pubblic }}
    </p>
    <p>Date Public</p>
    <input type="date" name="" id="" v-model="dataBlog.data_pubblic">
    <br><br><br>
    <button type="button" class="btn btn-success" v-show="ShowAdd" @click="addBlog" >Add</button>
    <button type="button" class="btn btn-success" v-show="showEdit" @click="editBlog(dataBlog.id)" >Edit</button>          
  </div>  
</template>

<script>
import axios from 'axios'
import { CATEGORY } from "@/store/constant";
import { POSITION } from "@/store/constant";
import Table from '@/components/blogs/ListBlog.vue'
export default {
  name: 'new',
  components: {
    Table
    
  },
  data() {
    return {
        ShowAdd: true,
        showEdit: false,
        CATEGORY,
        POSITION,
          dataBlog: {
            'id' : '',
            'title': '',
            'des': '',
            'detail': '',
            'thumps' : '',
            'category' :'',
            'public': '',
            'position': [],
            'data_pubblic': '',
          },
          errors : {},
        }
    },
  methods : {
    addBlog(){
      this.validate();
      if (Object.keys(this.errors).length > 0) {
        
        console.log(this.errors);
      } else {
      
      axios.post('http://localhost:3000/blogs/',this.dataBlog)
      window.location.href = '/blog/list'
      }
    },
    getBlogByID(id) {
      axios
        .get("http://localhost:3000/blogs/" + id)
        .then((res) => (this.dataBlog = res.data));
    },
    editBlog(id){
      this.validate();
      if (Object.keys(this.errors).length > 0) {
        
        console.log(this.errors);
      } else{
      axios.put('http://localhost:3000/blogs/' + id,this.dataBlog)
      window.location.href = '/blog/list'
      }
    },
    validate()
    {
      this.errors = {};
      if (this.dataBlog.title == '') {
      this.errors.title ="Tiêu Đề Trống";
      }
      if (this.dataBlog.des == '') {
      this.errors.des ="Mô tả Trống";
      }
      if (this.dataBlog.detail == '') {
      this.errors.detail ="Mô Tả Chi Tiết Trống";
      }
      // if (this.dataBlog.public == '') {
      // this.errors.public ="Trạng Thái Trống";
      // }
      if (this.dataBlog.position == '') {
      this.errors.position ="Vị Trí Trống";
      }
      if (this.dataBlog.data_pubblic == '') {
      this.errors.data_pubblic ="Thời Gian Trống";
      }
    }
  },
  mounted() {
    if (this.$route.params.id != null) {
      this.getBlogByID(this.$route.params.id);
      this.showEdit = !this.showEdit;
      this.ShowAdd = !this.ShowAdd;
    }
  },
}
</script>
<style>
.col-sm-3{
  margin-top: 20px; 
}
.col-sm-9{
    padding-right: 90px;
}
.list-group {
  list-style: none;
}
</style> 