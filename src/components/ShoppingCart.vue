<template>
  <div>
    <h2>Корзина</h2>
    <div v-if="cart.length > 0">
      <div v-for="item in cart" :key="item.id" class="cart-item">
        <p>{{ item.name }} ({{ item.quantity }}) - {{ item.price }} ₽</p>
        <button @click="removeFromCart(item.id)">Удалить</button>
      </div>
      <h3>Общая сумма: {{ totalPrice }} тнг</h3>
    </div>
    <p v-else>Корзина пуста</p>
  </div>
</template>

<script>
export default {
  name: 'ShoppingCart', 
  props: ['cart'],
  computed: {
    totalPrice() {
      return this.cart.reduce((sum, item) => sum + item.price * item.quantity, 0);
    },
  },
  methods: {
    removeFromCart(productId) {
      this.$emit('remove-from-cart', productId); 
    },
  },
};
</script>

<style>
.cart-item {
  display: flex;
  justify-content: space-between;
  padding: 10px;
  border-bottom: 1px solid #ddd;
}
</style>
