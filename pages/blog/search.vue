<template>
<BlogSearch></BlogSearch>
</template>

<script>
import BlogSearch from '@/components/BlogSearch.vue'
export default {
    components: {
        BlogSearch
    },
    props: {
    dataBlog: {},
  }
}
</script>
<style>

</style>