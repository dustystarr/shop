<template>
  <div>
    <h2>Список товаров (iPhone)</h2>
    <div v-for="product in products" :key="product.id" class="product">
      <h3>{{ product.name }}</h3>
      <p>Цена: {{ product.price }} тнг</p>
      <button @click="addToCart(product)">Добавить в корзину</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [
        { id: 1, name: 'iPhone 14', price: 499900 },
        { id: 2, name: 'iPhone 14 Pro', price: 599990 },
        { id: 3, name: 'iPhone 14 Pro Max', price: 619990 },
        { id: 4, name: 'iPhone 13', price: 69990 },
        { id: 5, name: 'iPhone SE (3rd Gen)', price: 299990 },
      ],
    };
  },
  methods: {
    addToCart(product) {
      this.$emit('add-to-cart', product); 
    },
  },
};
</script>

<style>
.product {
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 10px;
}
</style>
