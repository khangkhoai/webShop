<template>
  <!--Section: Block Content-->
  <section>
    <!--Grid row-->
    <div class="row">
      <!--Grid column-->
      <div class="col-lg-8 mb-4">
        <!-- Card -->
        <div class="card wish-list pb-1">
          <div class="card-body">
            <h5 class="mb-2">Name</h5>
            <div class="md-form md-outline my-0">
              <input type="text" id="name" class="form-control mb-0" />
            </div>
            <h5 class="mb-2">Address</h5>
            <div class="md-form md-outline my-0">
              <input type="text" id="address" class="form-control mb-0" />
            </div>
            <h5 class="mb-2">Phone</h5>
            <div class="md-form md-outline my-0">
              <input type="text" id="address" class="form-control mb-0" />
            </div>
            <h5 class="mb-2">Date</h5>
            <div class="md-form md-outline my-0">
              <input type="date" id="address" class="form-control mb-0" />
            </div>
          </div>
        </div>
        <!-- Card -->
      </div>
      <!--Grid column-->
      <!--Grid column-->
      <div class="col-lg-4">
        <!-- Card -->
        <div class="card mb-3">
          <div class="card-body">
            <h5 class="mb-3">The total amount of</h5>

            <ul class="list-group list-group-flush">
              <li
                class="list-group-item d-flex justify-content-between align-items-center border-0 px-0 mb-3"
              >
                <div>
                  <strong>The total amount of</strong>
                  <strong>
                    <p class="mb-0">(including VAT)</p>
                  </strong>
                </div>
                <span
                  ><strong>{{ this.total }} VNĐ</strong></span
                >
              </li>
            </ul>

            <nuxt-link :to="`/cart/checkout`" class="btn btn-primary">
              Checkout</nuxt-link
            >
          </div>
        </div>
        <!-- Card -->
      </div>

      <!--Grid column-->
    </div>
    <!--Grid row-->
  </section>
  <!--Section: Block Content-->
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
        console.log(this.total)
      }
    },
  },
  mounted() {
    this.viewCart()
  },
}
</script>

<style></style>
