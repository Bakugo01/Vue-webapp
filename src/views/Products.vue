<script setup>
import Mycard from '@/views/Mycard.vue';
</script>

<template>
  <main>
    <div class="tx">
      <h1>Products</h1>
    </div>
    <div class="grid-container">
      <Mycard 
        v-for="item in items" 
        :key="item.id"
        :id="item.id"
        :title="item.title"
        :description="item.description"
        :image="item.image"
        :price="item.price"
      />
    </div>
  </main>
</template>

<script>
export default {
  name: "Products",
  components: {
    Mycard,
  },
  data() {
    return {
      items: [],
    };
  },
  created() {
    fetch("https://fakestoreapi.com/products")
      .then((res) => {
        if (!res.ok) {
          throw new Error(`HTTP error! status: ${res.status}`);
        }
        return res.json();
      })
      .then((json) => {
        this.items = json;
      })
      .catch((error) => {
        console.error("Error fetching products", error);
      });
  },
};
</script>

<style scoped>
.tx {
  position: static;
  width: 100%;
  height: 60px;
  margin-top: 2px;
  display: flex;
  align-items: center;
  padding: 0 90px;
  font-size: 20px;
  font-weight: 600;
}

main {
  margin-top: 60px;
  padding: 1rem;
}

.grid-container {
  display: grid;
  gap: 1rem;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  padding: 1rem;
}

@media (min-width: 400px) {
  .grid-container {
    grid-template-columns: repeat(1, 1fr);
  }
  .tx {
    height: 80px;
    font-size: 16px;
  }
  main {
    margin-top: 100px;
  }
}

@media (min-width: 576px) {
  .grid-container {
    grid-template-columns: repeat(2, 1fr);
  }
  .tx {
    height: 100px;
    font-size: 18px;
  }
}

@media (min-width: 992px) {
  .grid-container {
    grid-template-columns: repeat(3, 1fr);
  }
  .tx {
    height: 120px;
    font-size: 20px;
  }
  main {
    margin-top: 120px;
  }
}
</style>
