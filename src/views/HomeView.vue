<template>
  <div class="home">
    <NavbarWorld />
    <div class="container mt-4">
      <HeroView />

      <div class="row mt-5">
        <div class="col">
          <h2>Best <strong>Foods</strong></h2>
        </div>
        <div class="col">
          <router-link to="/foods" class="btn btn-success float-right">
            <b-icon-eye></b-icon-eye> LIhat Semua</router-link
          >
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
// @ is an alias to /src
import NavbarWorld from "@/components/NavbarWorld.vue";
import HeroView from "@/components/HeroView.vue";
import CardView from "@/components/CardView.vue";
import axios from "axios";

export default {
  name: "HomeView",
  components: {
    NavbarWorld,
    HeroView,
    CardView,
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProduct(data) {
      this.products = data;
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/best-products")
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error));
  },
};
</script>
