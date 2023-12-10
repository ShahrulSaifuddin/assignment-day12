<template>
  <div class="Product_list">
    <div class="title">
      <h1>Products</h1>
    </div>
    <br />
    <div class="card" v-for="item in paginatedList" :key="item.id">
      <img :src="item.images" alt="Product" />
      <div class="container">
        <h4><b>{{ item.title }}</b></h4>
        <h4><b>{{ item.price }}</b></h4>
        <p>{{ item.description }}</p>
      </div>
    </div>

    <div class="pagination">
      <button @click="goToPage(page - 1)" :disabled="page === 1">Previous</button>
      <span>{{ page }}</span>
      <button @click="goToPage(page + 1)" :disabled="page === totalPages">Next</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "ProductApp",
  data() {
    return {
      list: [],
      pageSize: 5,
      page: 1,
    };
  },
  computed: {
    totalPages() {
      return Math.ceil(this.list.length / this.pageSize);
    },
    paginatedList() {
      const startIndex = (this.page - 1) * this.pageSize;
      const endIndex = startIndex + this.pageSize;
      return this.list.slice(startIndex, endIndex);
    },
  },
  async mounted() {
    let result = await axios.get("https://api.escuelajs.co/api/v1/products");
    this.list = result.data;
  },
  methods: {
    goToPage(newPage) {
      if (newPage >= 1 && newPage <= this.totalPages) {
        this.page = newPage;
      }
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.title {
  text-align: center;
  margin: 30px 0;
}

.Product_list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  margin: 10px;
  padding: 10px;
  border-radius: 5px;
  width: 200px;
  text-align: center;
}

.card img {
  width: 100%;
  height: auto;
  border-radius: 5px 5px 0 0;
}

.container {
  padding: 15px;
}

h4,
p {
  margin-bottom: 10px;
}

.pagination {
  margin-top: auto;
  text-align: center;
  margin-bottom: 20px;
}

.pagination button {
  margin: 0 5px;
  padding: 5px 10px;
  cursor: pointer;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 3px;
}

.pagination button:disabled {
  background-color: #bdc3c7;
  cursor: not-allowed;
}
</style>
