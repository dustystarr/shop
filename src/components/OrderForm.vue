<template>
  <div>
    <h2>Оформление заказа</h2>
    <form @submit.prevent="submitOrder">
      <div>
        <label for="name">Имя:</label>
        <input type="text" v-model="name" required />
      </div>
      <div>
        <label for="email">Email:</label>
        <input type="email" v-model="email" required />
      </div>
      <div>
        <label for="address">Адрес доставки:</label>
        <input type="text" v-model="address" required />
      </div>
      <h3>Сумма заказа: {{ totalAmount }} ₽</h3>
      <button type="submit">Оформить заказ</button>
    </form>
  </div>
</template>

<script>
export default {
  props: ['totalAmount'], 
  data() {
    return {
      name: '',
      email: '',
      address: '',
    };
  },
  methods: {
    submitOrder() {

      alert(`Заказ оформлен! Имя: ${this.name}, Email: ${this.email}, Адрес: ${this.address}, Сумма: ${this.totalAmount} ₽`);
    },
  },
};
</script>

<style>
form {
  display: flex;
  flex-direction: column;
  max-width: 400px;
  margin: 0 auto;
}
form div {
  margin-bottom: 10px;
}
button {
  padding: 10px;
}
</style>
