<template> 
  <div>
    <AppHeader />
        <div class="row">
          <div class="col-sm-3">
            <AppMenu/>
          </div>
          <div class="col-sm-9">
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
                <input type="text" style="width: 50%;" v-model="dataBlog.des">
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ errors.detail }}
                </p>
                <p>Mô tả chi tiết</p>
                <textarea name="" id="" cols="30" rows="10" style="width: 50%;" v-model="dataBlog.detail"></textarea>
                <p>Hình ảnh </p>
                <input type="file" name="thumps" id="" />
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ errors.category }}
                </p>
                <p>Loại</p>
                <select v-model="dataBlog.category">
                <option value="1">Thời Sự</option>
                <option value="2">Kinh Doanh</option>
                <option value="3">Thế Giới</option>
                <option value="4">Thể Thao</option>
                </select>
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ dataBlog.position }}
                </p>
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
                </p>
                <p>Public</p>
                <input type="radio" id="checkbox1" name="yes" :value="true" v-model="dataBlog.public"><label for="checkbox1">Yes</label><br>
                <input type="radio" id="checkbox2" name="no" :value="false" v-model="dataBlog.public"><label for="checkbox2">No</label><br>
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ errors.data_pubblic }}
                </p>
                <p>Date Public</p>
                <input type="date" name="" id="" v-model="dataBlog.data_pubblic">
                <br><br><br>
                <button type="button" class="btn btn-success" @click="edit" >Success</button>
                <button type="button" class="btn btn-primary">Primary</button>
            </div>  
          </div>
        </div>  
    </div>
</template>

<script>
import AppHeader from '../components/AppHeader.vue'
import AppMenu from '../components/AppMenu.vue'
import Table from '../components/table-blog.vue'
import { CATEGORY } from "../store/constant";
import { POSITION } from "../store/constant";
import axios from 'axios'
export default {
  name: 'edit',
  components: {
    AppHeader,
    AppMenu, 
    Table
  },
  data (){
    return { 
      dataBlog : [],
      CATEGORY,
      POSITION,
      form: {
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
  mounted() {
    this.listData();
  },
   methods:{
     listData() {
            axios({
                method: 'GET',
                url: `http://localhost:3000/blogs/` + this.$route.params.id,
                data: null
            }).then(res => {
                console.log(this.$route.params.id),
                    this.dataBlog = res.data;
                console.log(this.dataBlog)
            }).catch(err => {
                console.log(err)
            })
        },
    edit(){
      this.validate();
      if (Object.keys(this.errors).length > 0) {
        
        console.log(this.errors);
      } else{
      axios.put('http://localhost:3000/blogs/' + this.$route.params.id,this.dataBlog)
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
      if (this.dataBlog.public == '') {
      this.errors.public ="Puclic required";
      }
      if (this.dataBlog.position == '') {
      this.errors.position ="Vị Trí Trống";
      }
      if (this.dataBlog.data_pubblic == '') {
      this.errors.data_pubblic ="Thời Gian Trống";
      }
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
</style>