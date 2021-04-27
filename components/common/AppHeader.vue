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
              <a href="/cart/cart" class="nav-link navbar-link-2 waves-effect">
                <span class="badge badge-pill red">{{ this.badge }}</span>
                <i class="fas fa-shopping-cart pl-0"></i>
              </a>
            </li>
            <li class="nav-item">
              <a href="#!" class="nav-link waves-effect"> Contact </a>
            </li>
            <li v-if="this.cusID !== ''" class="nav-item">
              <div>
                <b-dropdown id="dropdown-1">
                  <b-dropdown-item @click="logout">Log out</b-dropdown-item>
                </b-dropdown>
              </div>
            </li>
            <li v-else-if="this.cusID === ''" class="nav-item">
              <a href="/login" class="nav-link waves-effect"> Sign in </a>
            </li>
            <li  v-if="this.cusID === ''" class="nav-item pl-2 mb-2 mb-md-0">
              <a
                href="/user/sign-up"
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
  data() {
    return {
      listProducts: [],
      carts: [],
      cartadd: {
        id: '',
        name: '',
        thumb: '',
        price: '',
        amount: 1,
      },
      badge: 0,
      quantity: 1,
      totalprice: '0',
      cusName: '',
      cusID: 0,
    }
  },
  computed: {
    fas() {
      return fas
    },
  },
  methods: {
    viewCart() {
      if (localStorage.getItem('carts')) {
        this.carts = JSON.parse(localStorage.getItem('carts'))
        this.badge = this.carts.length
        this.price = this.carts.reduce((total, item) => {
          return total + item.amount * item.price
        }, 0)
      }
    },
    viewCustomer() {
      this.cusID = document.cookie
        .split('; ')
        .find((row) => row.startsWith('id='))
        .split('=')[1]
      this.cusName = document.cookie
        .split('; ')
        .find((row) => row.startsWith('name='))
        .split('=')[1]
    },
    logout() {
      document.cookie = 'id' + '='
      document.cookie = 'name' + '='
       this.$router.push("/product");  
    },
  },
  mounted() {
    this.viewCart()
    this.viewCustomer()
  },
}
</script>

<style></style>
