<template>
  <div>
    <NavbarWorld />
    <div class="container">
      <div class="row">
        <div class="col">
          <h2>Daftar <strong>Makanan</strong></h2>
        </div>
      </div>

      <div class="row mt-3">
        <div class="col">
          <div class="input-group mb-3">
            <input
              v-model="search"
              type="text"
              class="form-control"
              placeholder="Cari Makanan kesukaan Anda"
              aria-label="Cari"
              aria-describedby="basic-addon1"
              @keyup="searchProduct"
            />
            <span class="input-group-text" id="basic-addon1">
              <b-icon-search></b-icon-search
            ></span>
          </div>
        </div>
      </div>

      <div class="row mb-3">
        <div
          class="col-md-4 mt-4"
          v-for="product in products"
          :key="product.id"
        >
          <CardView :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavbarWorld from "@/components/NavbarWorld.vue";
import CardView from "@/components/CardView.vue";
import axios from "axios";

export default {
  name: "FoodView",
  components: {
    NavbarWorld,
    CardView,
  },
  data() {
    return {
      products: [],
      search: "",
    };
  },
  methods: {
    setProduct(data) {
      this.products = data;
    },
    searchProduct() {
      axios
        .get("http://localhost:3000/products?q=" + this.search)
        .then((response) => this.setProduct(response.data))
        .catch((error) => console.log(error));
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/products")
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error));
  },
};
</script>