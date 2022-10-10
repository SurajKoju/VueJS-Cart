<script>
import axios from "axios";
const baseUrl = "https://fakestoreapi.com/products";

export default{
  data(){
    return {
      todos:[],
      counter: 0
    }},
  methods: {
    async GetApi(){
      await axios
      .get(baseUrl)
      .then((resp)=>{this.todos = resp.data;})
      .catch(
        (err)=>{
          console.log(err);
        });
    },
  },
  mounted(){
    this.GetApi();
  },
};
</script>

<template>

  <div class = "d-flex justify-content-between px-5 py-3 bg-light">
    <div class = "fs-1 p-0 text-start bg-light">Fake Store API</div>
    <div class = "fs-5 text-end mt-4 me-5 fixed-top" style="cursor:pointer;">CART <sup>[{{counter}}]</sup></div>
  </div>

  <span class="d-block"></span>

  <div v-for = "todo in todos" class="py-5">  
    <div class="card m-3">
      <img :src="todo.image">  
        <div class="card-body text-dark">
          <h5 class="card-title fs-5 px-3 text-center">{{todo.title}}</h5>   
            <div class="card-header text-dark">
              <p class="card-text p-0">
                <span class = "fst-italic">{{todo.category}}</span><br/>
                <span class = "fst-italic">Ratings: {{todo.rating.rate}}</span>
              </p>
              <p class = "fw-bold fs-5 ps-4">
                Rs. {{todo.price}}
              </p>
            </div>
        </div>
              
              <!-- <div class="description">
                <p class = 'fs-4'>Description</p>
              <p class = "text-wrap">{{todo.description}}</p>
            </div> -->
          
      <div class = "d-flex justify-content-between px-5 py-3">
        <a href="#" class="btn btn-primary px-3 py-2">View Product</a>
        <a href="#" class="btn btn-success px-3 py-2" @click="counter++">Add to Cart</a>
      </div>
    </div>    
  </div>
</template>

<style scoped>

img{
  width: 20vh;
  height:50vh;
  padding: 10px;
  object-fit: contain;
  display: block;
  margin: auto;
}


.card{
  border-radius: 20px;
}
.card-title{
  height: 100px;
}

.card-header{
  height:50px;
  display: flex; 
  justify-content: space-between;
  align-items: center;
  border-bottom: none;
}

.title{
  text-align: center;
}


.card{
  width: 25rem;
  height: 34rem;
  border: 0.5px solid black;
}

a{
  cursor: pointer;
}
</style>