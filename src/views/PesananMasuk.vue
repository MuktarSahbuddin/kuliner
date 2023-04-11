<template>
  <div class="pesanan-masuk">
    <NavbarWorld />
    <div class="container">
      <div class="row justify-content-center">
        <div class="col text-center">
          <img src="../assets/image/menunggu.png" alt="" width="300px" />
          <h2><strong>Sukses</strong></h2>
          <h4>
            Pesanan anda sedang diproses <br />
            Selamat menunggu
          </h4>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavbarWorld from "@/components/NavbarWorld.vue";
export default {
  nama: "PesananMasuk",
  components: {
    NavbarWorld,
  },
};
</script>