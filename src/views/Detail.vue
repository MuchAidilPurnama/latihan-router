<template>
    <br><br>
    <center>
        <div v-if="detail == undefined">Produk Tidak Tersedia</div>
        <div v-else>
        <h1>Detail {{ detail.nama }}</h1>
        <img :src="getImgSrc(detail.img)" alt="Category Image" />
        <h4>Harga : {{ detail.harga }}</h4>
        <h4>Deskripsi :  </h4>
        <P>{{ detail.des }}</P>
        </div>
        
    </center>
    
</template>

<script>
import { produk } from '@/assets/Produk';

export default{
    props: [
        "id_produk",
    ],
    setup(props){
        const detail = produk["produk"].find(function(item) {
            return item.id == props.id_produk;
        });
        const getImgSrc = (imgFileName) => {
            return '../src/assets/img/' + imgFileName + '';
        }
        return{
            detail,
            getImgSrc
        }
    }
}
</script>

<style>
img{
    width: 500px;
}
</style>