<script lang="ts">
// declare var require: any;
import { defineComponent, ref } from 'vue'
import picture from '../assets/thumb-29.jpg'

export default {
  name: 'Product',
  data() {
    return {
      title: 'Welcome to My Store',
      picture,
      inventory: 5,
      productDetails: ["Hãng: Kingston", "Dung lượng: 8GB", "Bảo hành 3 năm", "Tình trạng: Hàng mới"],
      number: [
        1, 2, 3, 4, 5, 6, 7, 8, 9, 10
      ],
      detail: '',
      cart: 0,
      detailRemove: false,
      products: [
        {
          productId: 1,
          productName: 'RAM',
          productPrice: 100,
          productImage: 'https://firebasestorage.googleapis.com/v0/b/trainwarningapp-f4ac2.appspot.com/o/1671705185-414-ktc-product-ssd-snv2s-1000g-2-zm-lg.jpg?alt=media&token=c543be8f-7c08-463f-b058-2c1f77302ec6',
          productDescription: 'This is product 1'
        },
        {
          productId: 2,
          productName: 'SSD',
          productPrice: 200,
          productImage: 'https://cdn-icons-png.flaticon.com/512/3144/3144456.png',
          productDescription: 'This is product 1'
        }
      ]

    }
  },
  methods: {
    addDetail() {
      if(this.detail != '') 
      this.productDetails.push(this.detail)
    },
    removeDetail(index: number) {
      this.productDetails.splice(index, 1)
    },
    addToCart() {
      this.cart += 1
    }
  },
}
</script>

<template>
  <div>
    <header id="header">
      <div class="container">
        <div class="cart">
          <p><i class="fa fa-shopping-cart" style="color: #9F9F9F;"></i> {{ cart }}</p>
        </div>
      </div>
    </header>
    <div class="container">
      <div class="product">
        <div class="image">
          <!-- <img src="https://cdn-icons-png.flaticon.com/512/3144/3144456.png " alt="product image"> -->
          <img v-bind:src="picture" alt="product image" style="height: 20em; width: 20em; border-radius: 1em;">
        </div>
        <div class="content">
          <h1>{{ title }}</h1>
          <!-- Đoạn v if else kiểm tra tình trạng hàng -->
          <div class="stockInfo">
            <span style="color: green;" v-if="inventory > 10">Còn hàng</span>
            <span style="color: red;" v-else-if="inventory <= 10 && inventory > 0">Còn ít hàng</span>
            <span style="color: red;" v-else>Hết hàng</span>
          </div>
          <!-- Thụt hàng ul, li dấu chấm dầu -->
          <ul class="fefatures">
            <li v-for="detail in productDetails" :key="detail">
              {{ detail }} <span v-show="detailRemove" @click="removeDetail(productDetails.indexOf(detail))" style="cursor: pointer">x</span>
            </li>
          </ul>
        </div>

        <div class="products">
          <span v-for="product in products" :key="product.productId">
            {{ product.productName }}
          </span>
        </div>

        <input v-model="inventory" placeholder="edit me" type="number" min="0">
        <br>
        <div style="flex-direction: row;">
          <input v-model="detail" placeholder="edit me">
          <button title="Add Detail" @click="addDetail">+</button>
        </div>
        <button v-on:click="addToCart" title="Add To Cart">Add To Cart</button>
        <button class="remove-detail" title="Remove Detail" @click="detailRemove = !detailRemove">
          <p v-if='!detailRemove'>Remove</p>
          <p v-else>Stop Remove</p>
        </button>
        <!-- <dialog open>
          <p>Xin chào!</p>
          <form method="dialog">
            <button>Close</button>
          </form>
        </dialog> -->

        <!-- <div>{{ detailRemove }}</div> -->
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  margin: 0 auto;
}

.product {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.content {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.cart {
  display: flex;
  flex-direction: column;
  align-items: end;
}
</style>
