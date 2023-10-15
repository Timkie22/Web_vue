<script setup lang="ts">
import { ref } from 'vue';
import StoreItem from './components/StoreItem.vue'
import logo from 'src/logo.jpg'



const items = ref([
  {
    id: 1,
    name: 'Iphone 15',
    description: 'The best Iphone ever made',
    price: 900,
    rating: 3.5,
    stock: 10,
    image: '/Iphone_15.jpg',
    category: 'Phones'
  },

  {
    id: 2,
    name: 'Nintendo Switch',
    description: 'Your kids favorite console',
    price: 399,
    rating: 5,
    stock: 22,
    image: '/switch.jpg',
    category: 'consoles'
    
  }
  
]);
</script>

<template>
  <div id="app">
    <header>
      <img :src="logo" alt="Tims Tech-store Logo" class="store-logo">
      <h1>Tims Tech-store</h1>
    </header>

    <nav>
      <!-- Navigation links -->
      <ul>
        <li><a href="#category1">Devices</a></li>
        <li><a href="#category2">Accessories</a></li>
        
      </ul>
    </nav>

    <main>
      <!-- Display a grid of store items -->
      <StoreItem
        v-for="item in items"
        :key="item.id"
        :name="item.name"
        :description="item.description"
        :price="item.price"
        :rating="item.rating"
        :stock="item.stock"
        :image="item.image"
        :category="item.category"
      />
    </main>

    <footer>
      <!-- Attributions, copyrights -->
      <p>© 2023 Tims Tech-store</p>
    </footer>
  </div>
</template>


<style>
#app {
  width: 100vw; 
  display: grid;
  grid-template-areas:
    "header header"
    "nav nav"
    "main main"
    "footer footer";
  grid-template-columns: 1fr 3fr;
  grid-template-rows: auto auto 1fr auto; 
  grid-gap: 20px;
}

nav {
  grid-area: nav;
  display: flex; 
  justify-content: space-around; 
  padding: 10px 0; 
}

nav ul {
  display: flex;
  list-style-type: none; 
}

nav li {
  margin-right: 15px;
 
}

nav li:last-child {
  margin-right: 0; 
}

header {
  grid-area: header;
}


main {
  grid-area: main;
  display: flex;
  flex-wrap: wrap; 
  justify-content: space-between; 
  align-items: flex-start;
}

footer {
  grid-area: footer;
}
.store-item:hover {
  background-color: #f5f5f5;
  transform: scale(1.03);    
  transition: 0.3s all;     
  cursor: pointer; 
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

</style>
