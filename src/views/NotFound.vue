<template>
  <div class="body-text">
    <h1>404 - Page Not Found</h1>
    <p>The page you're looking for doesn't exist.</p>
    <button @click="goHome">Go to Home</button>
  </div>
</template>

<script>
export default {
  name: 'NotFound', 
  methods: {
    goHome() {
      this.$router.push('/'); 
    },
  },
};
</script>

<style scoped>
h1 {
  color: red;
  font-size: 36px;
}

.body-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  padding: 20px;
  background-color: #f8f8f8;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.button {
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.button:hover {
  background-color: #0056b3;
}
</style>