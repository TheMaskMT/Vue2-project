<template>
  <div id="app">
    <!-- <h1>"Hello, World!" Example</h1> -->
    <Product/>
  </div>
</template>

<script>
import Product from './components/Product.vue'
import Dialog from './components/Dialog.vue'
export default {
  name: 'App',
  components: {
    Product
  }
}
</script>