<template>
  <!--Section: Block Content-->
  <section class="mb-5">
    <div class="row">
      <div class="col-md-6 mb-4 mb-md-0">
        <div id="mdb-lightbox-ui"></div>
        <div class="mdb-lightbox">
          <div class="row product-gallery mx-1">
            <div class="col-12 mb-0">
              <figure class="view overlay rounded z-depth-1 main-img">
                <a href="" data-size="710x823">
                  <img
                    v-bind:src="'http://127.0.0.1:8000/' + listProducts.thumb"
                    class="img-fluid z-depth-1"
                  />
                </a>
              </figure>
            </div>
          </div>
        </div>
      </div>
      <div class="col-md-6">
        <h5>{{ listProducts.name }}</h5>
        <p class="mb-2 text-muted text-uppercase small">Shirts</p>
        <p>
          <span class="mr-1"
            ><strong>{{ listProducts.price }} VND</strong></span
          >
        </p>
        <p class="pt-1">{{ listProducts.desc }}</p>
        <hr />
        <div class="table-responsive mb-2">
          <table class="table table-sm table-borderless">
            <tbody>
              <tr>
                <td class="pl-0 pb-0 w-25">Quantity</td>
                <td class="pl-0">
                  <div class="def-number-input number-input safari_only mb-0">
                    <button
                      onclick="this.parentNode.querySelector('input[type=number]').stepDown()"
                      class="minus"
                    ></button>
                    <input
                      class="quantity"
                      min="0"
                      v-bind:max="listProducts.amount"
                      name="quantity"
                      value="1"
                      v-model="quantity"
                      type="number"
                      
                    />
                    <button
                      onclick="this.parentNode.querySelector('input[type=number]').stepUp()"
                      class="plus"
                    ></button>
                  </div>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <button type="button" class="btn btn-primary btn-md mr-1 mb-2">
          Buy now
        </button>
        <button type="button" @click="addCart(listProducts)" class="btn btn-light btn-md mr-1 mb-2">
          <i class="fas fa-shopping-cart pr-2"></i>Add to cart
        </button>
      </div>
    </div>
  </section>
  <!--Section: Block Content-->
</template>
<script>
import axios from 'axios'
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
      badge: '0',
      quantity: 1,
      totalprice: '0',
    }
  },

  methods: {
    getDetails(id) {
      axios({ method: 'GET', url: 'http://127.0.0.1:8000/api/product/' + id })
        .then((res) => {
          this.listProducts = res.data
        })
        .catch((err) => {
          console.log(err)
        })
    },
    viewCart() {
      if (localStorage.getItem('carts')) {
        this.carts = JSON.parse(localStorage.getItem('carts'));
        this.badge = this.carts.length;
        this.price = this.carts.reduce((total, item) => {
          return total + item.amount*item.price
        }, 0);
        console.log(this.carts);
        // console.log(this.badge);
        // console.log(this.price)
      }
    },
    addCart(pro) {
      if((this.carts.map(a=>a.id))==pro.id)
      {
        
        this.carts[0].amount = +this.carts[0].amount  +  +this.quantity
        console.log(this.carts)
      }
      else
      {
      this.cartadd.id = pro.id;
      this.cartadd.name = pro.name;
      this.cartadd.thumb = pro.thumb;
      this.cartadd.amount = this.quantity;
      this.cartadd.price = pro.price;
      this.carts.push(this.cartadd);
      }
      this.cartadd = {};
      this.storeCart();
    },
   
    storeCart() {
       
      let parsed = JSON.stringify(this.carts)
      localStorage.setItem('carts', parsed)
      this.viewCart()
    },
  },
  mounted() {
    if (this.$route.params.id != null) {
      this.getDetails(this.$route.params.id)
    }
  },
}
</script>

<style></style>
