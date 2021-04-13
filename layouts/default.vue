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
        <AppFooter />
    </div>
</template>
<script>
import AppHeader from '@/components/common/AppHeader.vue'
import AppMenu from '@/components/common/AppMenu.vue'
import AppFooter from '@/components/common/AppFooter.vue'
export default {
  name: 'admin',
  components: {
    AppHeader,
    AppMenu,
    AppFooter   
  }, 
}
</script>
<style scoped>
.col-sm-3{
  margin-top: 20px;
  margin-right: 0px;
}

</style>