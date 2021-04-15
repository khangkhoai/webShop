<template>
<div class="container" style="margin-top: 35px">
    <div class="row">
      <div class="col-md-12">
         <!--Section: Block Content-->
  <section>
    <!--Grid row-->
    <div class="row">
      <!--Grid column-->
      <div class="col-lg-8">
        <!-- Card -->
        <div
          class="card wish-list mb-3"
          v-for="(dev, key) in this.carts"
          :key="key"
        >
          <div class="card-body">
            <div class="row mb-4">
              <div class="col-md-5 col-lg-3 col-xl-3">
                <div class="view zoom overlay z-depth-1 rounded mb-3 mb-md-0">
                  <img
                    class="img-fluid w-100"
                    v-bind:src="'http://127.0.0.1:8000/' + dev.thumb"
                  />
                </div>
              </div>
              <div class="col-md-7 col-lg-9 col-xl-9">
                <div>
                  <div class="d-flex justify-content-between">
                    <div>
                      <h5>{{ dev.name }}</h5>
                    </div>
                    <div>
                      <div
                        class="def-number-input number-input safari_only mb-0 w-100"
                      >
                        <input
                          class="quantity"
                          min="0"
                          name="quantity"
                          value="1"
                          v-model="dev.amount"
                          type="number"
                        />
                      </div>
                      <small
                        id="passwordHelpBlock"
                        class="form-text text-muted text-center"
                      >
                        (Note, 1 piece)
                      </small>
                    </div>
                  </div>
                  <div
                    class="d-flex justify-content-between align-items-center"
                  >
                    <div>
                      <button
                        type="button"
                        @click="removeCart(carts)"
                        class="btn btn-light btn-md mr-1 mb-2"
                      >
                        <i class="fas fa-shopping-cart pr-2"></i>Remove Cart
                      </button>
                    </div>
                    <p class="mb-0">
                      <span
                        ><strong>{{ dev.price }}</strong></span
                      >
                    </p>
                  </div>
                </div>
              </div>
            </div>
            <hr class="mb-4" />
          </div>
        </div>
        <!-- Card -->
      </div>
      <!--Grid column-->

      <!--Grid column-->
      <div class="col-lg-4">
        <!-- Card -->
        <div class="card mb-3 ">
          <div class="card-body">
            <h5 class="mb-3">The total amount of</h5>
            <ul class="list-group list-group-flush">
              <li
                class="list-group-item d-flex justify-content-between align-items-center border-0 px-0 mb-3"
              >
                <span
                  ><strong>{{ this.total }} VNĐ</strong></span
                >
              </li>
            </ul>
            <div style="margin-left:50px">
            <nuxt-link :to="`/cart/checkout`" class="btn btn-primary">
              Checkout</nuxt-link
            >
            </div>
          </div>
        </div>
        <!-- Card -->
      </div>
      <!--Grid column-->
    </div>
    <!--Grid row-->
  </section>
  <!--Section: Block Content-->
      </div>
    </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      listProducts: [],
      carts: [],
      total: '0',
    }
  },
  methods: {
    viewCart() {
      if (localStorage.getItem('carts')) {
        this.carts = JSON.parse(localStorage.getItem('carts'))
        this.total = this.carts.reduce((total, item) => {
          return total + item.amount * item.price
        }, 0)
        console.log(this.carts)
      }
    },
    removeCart(pro) {
      this.carts.splice(pro, 1)
      this.storeCart()
    },
    storeCart() {
      let parsed = JSON.stringify(this.carts)
      localStorage.setItem('carts', parsed)
      this.viewCart()
    },
  },
  mounted() {
    this.viewCart()
  },
}
</script>

<style></style>
