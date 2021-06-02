<template>
<nav class="navbar navbar-expand-lg navbar-dark bg-primary">
  <div class="container">
    <a class="navbar-brand"><strong>Elysium EXO Store</strong></a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Cart</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">About</a>
        </li>
      </ul>
      <form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn btn-secondary" type="submit">Search</button>
      </form>
    </div>
  </div>
</nav>


<div class="container">
<br>
  <h1 style="text-align: center;"><strong>Elysium EXO Store</strong></h1><br><br>

  <div class="row">
    <div class="col-md-4">
      <h2>Top Products</h2>

      <div class="titles">

        <ul class="list-group">
          <li class="list-group-item" v-for="get in products" :key="get.id">
            <a href="#" class="list-group-item-action" @click.prevent="selectProduct(get)">
              {{ get.title }}
            </a>
          </li>
        </ul>

      </div>

    </div>
    <div class="col-md-7">
     <Product :get="selectedProduct" v-if="selectedProduct!=null" />
    </div>
  </div>

</div>
  
</template>

<script>
import axios from 'axios'
import Product from './components/Product.vue'

export default {
  name: 'App',
  components: {
    Product
  },
  data() {
    return{
      products:[],
      selectedProduct: null
    }
  },
  methods: {
    async getProducts(){
      await axios.get('https://fakestoreapi.com/products')
      .then(res=> {
        if(res.status==200){
          this.products = res.data;
          console.log(this.products)
        }
      })
    },
    selectProduct(get) {
      this.selectedProduct = get
    }
  },
  created(){
    this.getProducts()
  }
}
</script>

<style>
  .titles{
    height: 69vh;
    overflow: scroll;
  }
</style>
