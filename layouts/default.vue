<template>
    <div>
        <AppHeader />
        <div class="row">
          <div class="col-sm-3">
            <AppMenu/>
          </div>
          <div class="col-sm-9">
          <Nuxt /> 
          </div>
        
        </div>
          
    </div>
</template>
<script>
import AppHeader from '../components/AppHeader.vue'
import AppMenu from '../components/AppMenu.vue'

export default {
  name: 'admin',
  components: {
    AppHeader,
    AppMenu
    
  },
  
}
</script>
<style scoped>
.col-sm-3{
  margin-top: 20px;
}
.col-sm-9{
    padding-right: 90px;
}
</style>