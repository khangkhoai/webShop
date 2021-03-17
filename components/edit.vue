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
                <p>Tiêu đều</p>
                <input type="text" style="width: 50%;" v-model="dataBlog.title">
                <p>Mô tả ngắn</p>
                <input type="text" style="width: 50%;" v-model="dataBlog.des">
                <p>Mô tả ngắn</p>
                <textarea name="" id="" cols="30" rows="10" style="width: 50%;" v-model="dataBlog.detail"></textarea>
                <p>Hình ảnh </p>
                <input type="file" name="thumps" id="" />
                <p>Loại</p>
                <select v-model="dataBlog.category">
                <option value="1">Thời Sự</option>
                <option value="2">Kinh Doanh</option>
                <option value="3">Thế Giới</option>
                <option value="4">Thể Thao</option>
                </select>
                <p>Vị trí</p>
                <ul class="list-group list-group-flush">
                  <li v-for="(post,key) in CONTRY" :key="post" class="list-group-control">
                    <div class="custom-control custom-checkbox">
                      <input type="checkbox" :value="key" class="custom-control-input" :id="'check' + key + 1" v-model="dataBlog.position">
                      <label class="custom-control-label" :for=" 'check' + key + 1">{{ post }}</label>
                    </div>
                  </li>
                </ul>
                <p>Public</p>
                <input type="radio" id="checkbox1" name="yes" :value="true" v-model="dataBlog.public"><label for="checkbox1">Yes</label><br>
                <input type="radio" id="checkbox2" name="no" :value="false" v-model="dataBlog.public"><label for="checkbox2">No</label><br>
                <p>Date Public</p>
                <input type="date" name="" id="" v-model="dataBlog.data_pubblic">
                <br><br><br>
                <button type="button" class="btn btn-success" @click="submit" onclick="location.href='/list'">Success</button>
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
export const CONTRY = ["Việt Nam", 'Châu Âu', 'Châu Á', 'Châu Mỹ']
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
      form: {
                'title': '',
                'des': '',
                'detail': '',
                'public': '',
                'position': [],
                'thumps' : '',
                'data_pubblic': '',
            },
      CONTRY,
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
    submit(){
      axios.put('http://localhost:3000/blogs/' + this.$route.params.id,this.dataBlog)
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