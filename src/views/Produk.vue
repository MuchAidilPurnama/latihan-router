<template>
    <h1>Produk</h1>
    <div class="flex-container">
        <div v-for="produk in jual" :key="produk.id" class="card">
            <img :src="getImgSrc(produk.img)" alt="Category Image" />
            <router-link class="container" :to="{ name: 'Detail', params: { id_produk: produk.id} }">
            <h4 align="center">{{ produk.nama }}</h4>
        </router-link>
        </div>
    </div>
</template>

<script>
import { onMounted, reactive } from 'vue';
import { produk } from '@/assets/Produk';

export default{
    setup(props, context)
    {
        const jual = reactive(produk["produk"]);

        const getImgSrc = (imgFileName) => {
            return '../src/assets/img/' + imgFileName + '';
        }

        onMounted(() => {
            context.emit("id-menu", 4);
        });

        return {
            jual,
            getImgSrc
        }
    }
}
</script>

<style scoped>
.flex-container {
    display: flex;
    flex-wrap: wrap;
}
.card {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    margin: 10px;
    min-width: 330px;
    cursor: pointer;
}

.card:hover{
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

.container{
    padding: 2px 16px;
}
img{
    width: 350px;
    height: 270px;
}
</style>