<template>
    <div class="container mt-3">
        <h1>Semua Produk</h1>
        <table-component :produk="produk" :keranjang="keranjang"></table-component>
        <h1>Keranjang Produk</h1>
        <table-checkout :produk="produk" :keranjang="keranjang" :totalHarga="totalHarga" @emitAdd="addProduk"></table-checkout>
        <button-component tombol="success mb-4" nama="Checkout" class="bi bi-cart-check-fill" @fungsiEmit="succesCheckout()"></button-component>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                produk : [
                    {
                        id : 0,
                        gambar : require('../../../public/images/indomie.jpg'),
                        nama : "Indomie Goreng Rendang",
                        deskripsi : "Masakan instan terenak di dunia",
                        stock : 10,
                        harga : 5000
                    },
                    {
                        id : 1,
                        gambar : require('../../../public/images/miegelas.jpeg'),
                        nama : "Mie Gelas Rendang",
                        deskripsi : "Mie Instan Khusus Anak Kosan",
                        stock : 3,
                        harga : 3000
                    },
                    {
                        id : 2,
                        gambar : require('../../../public/images/bakmi.jpg'),
                        nama : "Bakmi Mewah",
                        deskripsi : "Kalau anak kos jangan macam-macam deh",
                        stock : 80,
                        harga : 10000
                    }
                ],
                keranjang : [
                    {
                        id : 0,
                        nama : "Indomie Goreng Rendang",
                        jumlah : 0,
                        harga : 0
                    },
                    {
                        id : 1,
                        nama : "Mie Gelas Rendang",
                        jumlah : 0,
                        harga : 0
                    },
                    {
                        id : 2,
                        nama : "Bakmi Mewah",
                        jumlah : 0,
                        harga : 0
                    },
                ]
            }
        },
        mounted() {
            console.log('Component mounted.')
        },
        methods: {
            succesCheckout() {
                const jum = this.keranjang[0].harga + this.keranjang[1].harga + this.keranjang[2].harga
                if(jum > 0){
                    window.alert("Total pesanan anda adalah Rp." + jum)
                    location.reload();
                }else{
                    window.alert("Minimal pesen dulu bang")
                }
            }
        },
        computed: {
            totalHarga : function(){
                return this.keranjang[0].harga + this.keranjang[1].harga + this.keranjang[2].harga
            }
        }
    }
</script>
