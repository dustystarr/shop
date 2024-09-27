<template>
  <div id="app">
    <h1>Магазин товаров</h1>
    <ProductList @add-to-cart="addToCart" />
    <ShoppingCart :cart="cart" @remove-from-cart="removeFromCart" />
    <OrderForm :totalAmount="totalAmount" />
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';
import ShoppingCart from './components/ShoppingCart.vue';
import OrderForm from './components/OrderForm.vue';

export default {
  components: {
    ProductList,
    ShoppingCart,  // Используем многословное имя
    OrderForm,
  },
  data() {
    return {
      cart: [], // Корзина для товаров
    };
  },
  computed: {
    totalAmount() {
      // Вычисляем общую сумму товаров в корзине
      return this.cart.reduce((sum, item) => sum + item.price * item.quantity, 0);
    },
  },
  methods: {
    addToCart(product) {
      // Добавление товара в корзину
      const existingProduct = this.cart.find(item => item.id === product.id);
      if (existingProduct) {
        existingProduct.quantity += 1;
      } else {
        this.cart.push({...product, quantity: 1});
      }
    },
    removeFromCart(productId) {
      // Удаление товара из корзины
      this.cart = this.cart.filter(item => item.id !== productId);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
}
</style>
