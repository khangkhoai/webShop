<template>
  <div class="row">
    <div class="col-sm-3">
      <div class="row" style="margin-left: 50px">
        <img
          class="float-left"
          src="@/assets/image/logo.png"
          width="70"
          height="50"
          alt=""
        />
      </div>
    </div>
    <div class="col-sm-9">
      <!-- Navbar -->
      <nav class="navbar navbar-expand-md navbar-light bg-primary">
        <a class="navbar-brand" href="/product"> Home </a>

        <!-- Links -->
        <div class="collapse navbar-collapse" id="basicExampleNav1">
          <!-- Right -->
          <ul class="navbar-nav ml-auto">
            <li class="nav-item">
              <a href="#!" class="nav-link navbar-link-2 waves-effect">
                <span class="badge badge-pill red">1</span>
                <i class="fas fa-shopping-cart pl-0"></i>
                 
              </a>
            </li>

            <li class="nav-item">
              <a href="#!" class="nav-link waves-effect"> Contact </a>
            </li>
            <li class="nav-item">
              <a href="#!" class="nav-link waves-effect"> Sign in </a>
            </li>
            <li class="nav-item pl-2 mb-2 mb-md-0">
              <a
                href="#!"
                type="button"
                class="btn btn-outline-info btn-md btn-rounded btn-navbar waves-effect waves-light"
                >Sign up</a
              >
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
import { fas } from '@fortawesome/free-solid-svg-icons'
export default {
  computed: {
    fas () {
       return fas 
    },
    
  },
}
</script>

<style></style>
