<template>
  <div v-for="item in items" :key="item.id">
    <img :src="item.images[0]" alt="Product name">
    <h2 class="product-name">{{ item.title }}</h2>
    <p class="product-description">{{ item.description }}</p>
    <p class="product-price">{{ item.images[0] }} </p>
    <button class="add-to-cart">Add to Cart</button>
  </div>
</template>
<script>
export default {
  name: 'MyComponent',
  data() {
    return {
      items: [],
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      try {
        const response = await fetch('https://dummyjson.com/products');
        const data = await response.json();
        this.items = data.products;
        console.log(data)
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

