<template>
  <div>
    <AppHeader />
        <div class="row">
          <div class="col-sm-3">
            <AppMenu/>
          </div>
          <div class="col-sm-9">
            <div class="blogNew">
                <h3>Edit Blog</h3>
                <p>Tiêu đều</p>
                <input type="text" style="width: 50%;">
                <p>Mô tả ngắn</p>
                <input type="text" style="width: 50%;">
                <p>Mô tả ngắn</p>
                <textarea name="" id="" cols="30" rows="10" style="width: 50%;"></textarea>
                <p>Hình ảnh </p>
                <input type="file" name="" id=""/>
                <p>Loại</p>
                <select>
                <option value="">Thời Sự</option>
                <option value="">Saab</option>
                <option value="">Opel</option>
                <option value="">Audi</option>
                </select>
                <p>Vị trí</p>
                <input type="checkbox" name="" id=""><label for="vehicle1"> Việt Nam  </label><br>
                <input type="checkbox" name="" id=""><label for="vehicle1"> Châu Âu </label><br>
                <input type="checkbox" name="" id=""><label for="vehicle1"> Châu Á  </label><br>
                <input type="checkbox" name="" id=""><label for="vehicle1"> Châu Mỹ </label><br>
                <p>Public</p>
                <input type="radio" name="puclic" id=""><label for="vehicle1"> Yes</label><br>
                <input type="radio" name="puclic" id=""><label for="vehicle1"> No</label><br>
                <p>Date Public</p>
                <input type="date" name="" id="">
                <br><br><br>
                <button type="button" class="btn btn-success">Success</button>
                <button type="button" class="btn btn-primary">Primary</button>
            </div>  
          </div>
        </div>  
    </div>
</template>

<script>
import AppHeader from '../components/AppHeader.vue'
import AppMenu from '../components/AppMenu.vue'
import Table from '../layouts/Table.vue'
export default {
  name: 'edit',
  components: {
    AppHeader,
    AppMenu, 
    Table
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