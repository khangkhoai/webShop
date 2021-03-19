<template>
        <ul class="list-group" >
          <li class="list-group-item"><nuxt-link to="/blog/list"><button>List</button></nuxt-link></li>
          <li class="list-group-item"><nuxt-link to="/blog/new"><button>New</button></nuxt-link></li>
          <li class="list-group-item"><nuxt-link to="/blog/search"><button>Search</button></nuxt-link></li>
          <li class="list-group-item"><nuxt-link to=""><button>Edit</button></nuxt-link></li>
        </ul>  
</template>

<script>
export default {
     name : "AppMenu"
}
</script>

<style>
.list-group-item{
 margin-left: 30px;
 margin-right: 20px;
 text-align: center;
}
.li button{
  background-color:white;
  font-weight: bold;
  border: 1px solid black;
  display: block;
}
button{
  background-color: white;
  border: none;
}
</style>