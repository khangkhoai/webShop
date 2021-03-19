<template>
  <div class="blogNew">
                <h3>New Blog</h3>
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ errors.title }}
                </p>
                <p>Tiêu đề</p>
                <input type="text" style="width: 50%;" v-model="form.title">
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ errors.des }}
                </p>
                <p>Mô tả ngắn</p>
                <input type="text" style="width: 50%;" v-model="form.des">
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ errors.detail }}
                </p>
                <p>Mô tả chi tiết</p>
                <textarea name="" id="" cols="30" rows="10" style="width: 50%;" v-model="form.detail"></textarea>
                <p>Hình ảnh </p>
                <input type="file" name="thumps" id="" />
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ errors.category }}
                </p>
                <p>Loại</p>
                <select v-model="form.category">
                <option value="1">Thời Sự</option>
                <option value="2">Kinh Doanh</option>
                <option value="3">Thế Giới</option>
                <option value="4">Thể Thao</option>
                </select>
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ errors.position }}
                </p>
                <p>Vị trí</p>
                <ul class="list-group list-group-flush">
                  <li v-for="(post,key) in CONTRY" :key="post" class="list-group-control">
                    <div class="custom-control custom-checkbox">
                      <input type="checkbox" :value="key" class="custom-control-input" :id="'check' + key + 1" v-model="form.position">
                      <label class="custom-control-label" :for=" 'check' + key + 1">{{ post }}</label>
                    </div>
                  </li>
                </ul>
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ errors.public }}
                </p>
                <p>Public</p>
                <input type="radio" id="checkbox1" name="yes" :value="true" v-model="form.public"><label for="checkbox1">Yes</label><br>
                <input type="radio" id="checkbox2" name="no" :value="false" v-model="form.public"><label for="checkbox2">No</label><br>
                <p v-if="Object.keys(this.errors).length > 0" class="text text-danger">
                  {{ errors.data_pubblic }}
                </p>
                <p>Date Public</p>
                <input type="date" name="" id="" v-model="form.data_pubblic">
                <br><br><br>
                <button type="button" class="btn btn-success" @click="addBlog" >Success</button>
                <button type="button" class="btn btn-primary">Primary</button>
            </div>  
</template>

<script>


import axios from 'axios'
export const CONTRY = ["Việt Nam", 'Châu Âu', 'Châu Á', 'Châu Mỹ']
export default {
  name: 'new',
  components: {
    
    
  },
  data() {
        return {
          CONTRY,
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
  methods : {
    addBlog(){
      this.validate();
      if (Object.keys(this.errors).length > 0) {
        
        console.log(this.errors);
      } else {
      
      axios.post('http://localhost:3000/blogs/',this.form)
      // window.location.href = '/list'
      }
    },
    validate()
    {
      this.errors = {};
      if (this.form.title == '') {
      this.errors.title ="Tiêu Đề Trống";
      }
      if (this.form.des == '') {
      this.errors.des ="Mô tả Trống";
      }
      if (this.form.detail == '') {
      this.errors.detail ="Mô Tả Chi Tiết Trống";
      }
      if (this.form.public == '') {
      this.errors.public ="Puclic required";
      }
      if (this.form.position == '') {
      this.errors.position ="Vị Trí Trống";
      }
      if (this.form.data_pubblic == '') {
      this.errors.data_pubblic ="Thời Gian Trống";
      }
    }
  }
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