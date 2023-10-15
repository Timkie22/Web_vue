<template>
    <div class="store-item">
      <img :src="image" alt="Product image">
      <h2>{{ name }}</h2>
      <p>{{ description }}</p>
      <p>Price: ${{ price }}</p>
      <p>Rating:  <span v-for="(star, index) in displayStars(rating)" :key="index" :class="star"></span>
      {{ rating }} / 5</p>
      <p>Stock: {{ stock }} items available</p>
      <p>Category: {{ category }}</p>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent } from 'vue';
  
  export default defineComponent({
    name: 'StoreItem',
    props: {
      name: {
        type: String,
        required: true
      },
      description: {
        type: String,
        required: true
      },
      price: {
        type: Number,
        required: true
      },
      rating: {
        type: Number,
        required: true
      },
      stock: {
        type: Number,
        required: true
      },
      image: {
        type: String,
        required: true
      },
      category: {
        type: String,
        required: true
      }
      
    },
    methods: {
    displayStars(rating: number) {
      let stars = [];
      for (let i = 1; i <= 5; i++) {
        if (i <= rating) {
          stars.push('fas fa-star'); // voller Stern
        } else if (i - rating < 1) {
          stars.push('fas fa-star-half-alt'); // halber Stern
        } else {
          stars.push('far fa-star'); // leerer Stern
        }
      }
      console.log(stars);
      return stars;
      
    }
  }
});

  
  </script>
  
  <style scoped>
  .store-item {
  flex: 0 0 calc(50% - 10px);
  box-sizing: border-box;
  margin: 0 5px;
  vertical-align: top;
  }
  </style>
  