<template>
  <table class="table table-bordered-bottom mt-1">
    <thead class="table-success">
        <tr>
            <td>Nama</td>
            <td>Jumlah</td>
            <td>Harga</td>
            <td></td>
            <td></td>
        </tr>
    </thead>
    <tbody>
        <tr v-for="item in keranjang" :key="item" class="mb-3">
            <td>{{ item.nama }}</td>
            <td>{{ item.jumlah }}</td>
            <td>Rp.{{ item.harga }}</td>
            <td><button-component tombol="warning" nama="-1" class="bi bi-cart-dash" @fungsiEmit="deleteItem(item.id)"></button-component></td>
            <td><button-component tombol="danger" nama="Delete All" class="bi bi-cart-x" @fungsiEmit="deleteAll(item.id)"></button-component></td>
        </tr>
        <tr>
          <td>Total : </td>
          <td colspan="4">Rp.{{ totalHarga }}</td>
        </tr>
    </tbody>
</table>
</template>

<script>
export default {
    props: ['produk', 'keranjang', 'totalHarga'],
    methods: {
        deleteItem(id){
            if(this.keranjang[id].jumlah > 0){
                this.keranjang[id].jumlah -= 1
                this.keranjang[id].harga -= this.produk[id].harga
                this.produk[id].stock += 1
            }else{
                window.alert('Pesanan masih kosong bang !!')
            }
        },
        deleteAll(id){
            if(this.keranjang[id].jumlah > 0){
                this.keranjang[id].harga = 0
                this.produk[id].stock += this.keranjang[id].jumlah
                this.keranjang[id].jumlah = 0
            }else{
                window.alert('Pesanan masih kosong bang !!')
            }
        }
    },
}
</script>

<style>

</style>