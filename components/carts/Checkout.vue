<template>
<div class="container" style="margin-top: 35px">
    <div class="row">
      <div class="col-md-10">
       <!--Section: Block Content-->
  <section>
    <!--Grid row-->
    <div class="row">
      <!--Grid column-->
      <div class="col-lg-8 mb-4">
        <!-- Card -->
        <div class="card wish-list pb-1">
          <div class="card-body">
             <h5 class="mb-2">CustomerID</h5>
            <div class="md-form md-outline my-0">
              <input v-model="dataForm.customer_id" type="text"  class="form-control mb-0" />
            </div>
            <h5 class="mb-2">Name</h5>
            <div class="md-form md-outline my-0">
              <input v-model="dataForm.name" type="text"  class="form-control mb-0" />
            </div>
            <h5 class="mb-2">Address</h5>
            <div class="md-form md-outline my-0">
              <input v-model="dataForm.address" type="text"  class="form-control mb-0" />
            </div>
            <h5 class="mb-2">Phone</h5>
            <div class="md-form md-outline my-0">
              <input v-model="dataForm.phone" type="text"  class="form-control mb-0" />
            </div>
            <h5 class="mb-2">Date</h5>
            <div class="md-form md-outline my-0">
              <input v-model="dataForm.date" type="date"  class="form-control mb-0" />
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
                <span
                  ><strong>{{ this.total }} VNĐ</strong></span
                >
              </li>
            </ul>

            <button @click="addOrder()" class="btn btn-danger">Purchase</button>
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
import axios from 'axios'
export default {
  data() {
    return {
      listProducts: [],
      carts: [],
      dataForm : {
        status : 0,
        total_price : 0
      },
      orderDetail : {
        order_id : 1,
        product_id : 0,
        amount : 0,
        sub_total : 0
      },
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
        this.dataForm.total_price = this.total
        this.orderDetail.product_id=this.carts[0].id;
      this.orderDetail.amount=this.carts[0].amount;
      this.orderDetail.sub_total=this.carts[0].amount* this.carts[0].price;
      }
    },
    addOrder() {
      axios
        .post("http://127.0.0.1:8000/api/order/", this.dataForm)
        .then(res => {
      
        });
      this.addOrderDetail()
    },
    addOrderDetail() {
      
      axios
        .post("http://127.0.0.1:8000/api/order_detail/", this.orderDetail)
        .then(res => {
      
        });
    },
    // viewOrder()
    // {
    //   axios
    //     .get("http://127.0.0.1:8000/api/order/", this.dataForm)
    //     .then(res => {
      
    //     });
    // }
  },
  mounted() {
    this.viewCart()
  },
}
</script>

<style></style>
