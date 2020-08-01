<template>
  <!-- Header Section Begin -->
  <header class="header-section">
    <div class="header-top">
      <div class="container">
        <div class="ht-left">
          <div class="mail-service">
            <i class="fa fa-envelope"></i> hello.shayna@gmail.com
          </div>
          <div class="phone-service">
            <i class="fa fa-phone"></i> +628 22081996
          </div>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="inner-header">
        <div class="row">
          <div class="col-lg-2 col-md-2">
            <div class="logo">
              <router-link to="/">
                <img src="img/logo_website_shayna.png" alt />
              </router-link>
            </div>
          </div>
          <div class="col-lg-7 col-md-7"></div>
          <div class="col-lg-3 text-right col-md-3">
            <ul class="nav-right">
              <li class="cart-icon">
                Keranjang Belanja &nbsp;
                <a href="#">
                  <i class="icon_bag_alt"></i>
                  <span>{{userCart.length}}</span>
                </a>
                <div class="cart-hover">
                  <div class="select-items">
                    <table>
                      <tbody v-if="userCart.length > 0">
                        <tr v-for="(cartItem, index) in userCart" :key="`item-${cartItem.id}`">
                          <td class="si-pic">
                            <img :src="cartItem.photo" class="photo-item" alt />
                          </td>
                          <td class="si-text">
                            <div class="product-selected">
                              <p>${{cartItem.price}} x 1</p>
                              <h6>{{cartItem.name}}</h6>
                            </div>
                          </td>
                          <td @click="removeItem(index)" class="si-close">
                            <i class="ti-close"></i>
                          </td>
                        </tr>
                      </tbody>
                      <tbody v-else>
                        <tr>
                          <td>Empty Cart</td>
                        </tr>
                      </tbody>
                    </table>
                  </div>
                  <div class="select-total">
                    <span>total:</span>
                    <h5>${{totalHarga}}.00</h5>
                  </div>
                  <div class="select-button">
                    <router-link to="/cart" class="primary-btn view-card">VIEW CARD</router-link>
                    <a href="#" class="primary-btn checkout-btn">CHECK OUT</a>
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </header>
  <!-- Header End -->
</template>

<script>
export default {
  name: "HeaderShayna",
  data() {
    return {
      userCart: [],
    };
  },
  methods: {
    removeItem(index) {
      this.userCart.splice(index, 1);
      const parsed = JSON.stringify(this.userCart);
      localStorage.setItem("userCart", parsed);
    },
  },
  mounted() {
    if (localStorage.getItem("userCart")) {
      try {
        this.userCart = JSON.parse(localStorage.getItem("userCart"));
      } catch (e) {
        localStorage.removeItem("userCart");
      }
    }
  },
  computed: {
    totalHarga() {
      return this.userCart.reduce(function (items, data) {
        return items + data.price;
      },0);
    },
  },
};
</script>

<style scoped>
.photo-item {
  width: 80px;
  height: 80px;
}
</style>