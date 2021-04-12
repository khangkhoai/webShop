<template>
  <div class="row"> 
    <div class="col-sm-3">
      <div class="row" style="margin-left:50px">
        <img class="float-left" src="@/assets/image/logo.png" width="70" height="50" alt="">
      </div>
    </div>
    <div class="col-sm-9">
      <!-- Navbar -->
<nav class="navbar navbar-expand-md navbar-light bg-primary">
 <a class="navbar-brand" href="#!">
    Home
  </a>
  <form class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
      <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
  </form>
 

  <!-- Links -->
  <div class="collapse navbar-collapse" id="basicExampleNav1">

    <!-- Right -->
    <ul class="navbar-nav ml-auto">
      <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle waves-effect" id="navbarDropdownMenuLink3" data-toggle="dropdown"
          aria-haspopup="true" aria-expanded="true">
          <i class="united kingdom flag m-0"></i>
        </a>
        <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdownMenuLink">
          <a class="dropdown-item" href="#!">Action</a>
          <a class="dropdown-item" href="#!">Another action</a>
          <a class="dropdown-item" href="#!">Something else here</a>
        </div>
      </li>
     
      <li class="nav-item">
        <a href="#!" class="nav-link waves-effect">
          Contact
        </a>
      </li>
      <li class="nav-item">
        <a href="#!" class="nav-link waves-effect">
          Sign in
        </a>
      </li>
      <li class="nav-item pl-2 mb-2 mb-md-0">
        <a href="#!" type="button"
          class="btn btn-outline-info btn-md btn-rounded btn-navbar waves-effect waves-light">Sign up</a>
      </li>
    </ul>

  </div>
  <!-- Links -->

</nav>
<!-- Navbar -->
    </div>
  </div> 
</template>

<script>
export default {
     name : "AppHeader"
}
</script>

<style>

</style>