<template>
  <div class="Product_list">
    <div class="title">
  <h1>Products</h1>
    </div>
 <br/>
  <div class="card" v-for="item in list" :key="item.id">
        <img :src="item.images" alt="Product">
        <div class="container">
        <h4><b>{{ item.title }}</b></h4>
        <h4><b>{{ item.price }}</b></h4>
        <p>{{ item.description }}</p>
      </div>
  </div>


</div>
</template>

<script>
import axios from "axios";
export default{

name: "ProductApp",
data(){
    return{

        list:[]

    }


},
async mounted(){

let result = await axios.get("https://api.escuelajs.co/api/v1/products");
    console.warn(result.data);
    this.list = result.data;



}

}

</script>

<style scoped>

img{

  width: 100px;
  height: 100px;

}
.title{

  margin: 30px 50px;
  


}
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  margin-top: 50px;
  padding: 10px;
  border-radius: 5px; /* 5px rounded corners */
}

/* Add rounded corners to the top left and the top right corner of the image */
img {
  border-radius: 5px 5px 0 0;
}

.Product_list{

  display: flex;


}


</style>
