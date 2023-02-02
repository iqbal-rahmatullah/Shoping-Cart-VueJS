<template>
  <table class="table table-bordered mt-1">
    <thead class="table-primary">
        <tr class="fw-bold">
            <td>Picture</td>
            <td>Name</td>
            <td>Description</td>
            <td>Stock</td>
            <td>Price</td>
            <td></td>
            <td></td>
        </tr>
    </thead>
    <tbody>
        <tr class="align-middle" v-for="item in produk" :key="item">
            <td><img :src="item.gambar" width="150px"></td>
            <td>{{ item.nama }}</td>
            <td>{{ item.deskripsi }}</td>
            <td>{{ item.stock }}</td>
            <td>Rp. {{ item.harga }}</td>
            <td><button-component tombol="info" nama="+1" class="bi bi-cart-plus" @fungsiEmit="addProduk(item.id)"></button-component></td>
            <td><button-component tombol="primary" nama="All" class="bi bi-cart-plus-fill" @fungsiEmit="addAll(item.id)"></button-component></td>
        </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: ['produk', 'keranjang'],
  methods: {
    addProduk(id){
      if(this.produk[id].stock > 0){
        this.keranjang[id].jumlah += 1
        this.keranjang[id].harga += this.produk[id].harga
        this.produk[id].stock -= 1
      }else{
        window.alert('Stock habis bang !!')
      }
    },
    addAll(id){
        if(this.produk[id].stock > 0){
          this.keranjang[id].jumlah += this.produk[id].stock
          this.keranjang[id].harga = this.keranjang[id].jumlah * this.produk[id].harga
          this.produk[id].stock = 0
        }else{
          window.alert('Stock habis bang !!')
        }
    }
  },
}
</script>

<style>

</style>