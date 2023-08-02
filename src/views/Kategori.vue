<template>
    <h1 align="center">Kategori</h1>
    <div class="flex-container"> 
        <div v-for="kategori in state" :key="kategori.id" class="card">
            <img :src="getImgSrc(kategori.img)" alt="Category Image" />
            <router-link class="container" :to="{ name: 'KategoriProduk', params: { id_kategori: kategori.id} }">
            <h4 align="center">{{ kategori.nama }}</h4>
        </router-link>
        </div>
    </div>
</template>

<script>
import { onMounted, reactive } from 'vue';
import { kategori } from '@/assets/Kategori';


export default{
    setup(props, context)
    {
        const state = reactive(kategori["kategori"]);

        const getImgSrc = (imgFileName) => {
            return '../src/assets/img/' + imgFileName + '';
        }

        onMounted(() => {
            context.emit("id-menu", 5);
        });

        return {
            state,
            getImgSrc
        }
    }
}
</script>

<style scoped>
.flex-container {
    display: flex;
}
.card {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    margin: 8px;
    min-width: 100px;
    cursor: pointer;
}

.card:hover{
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

.container{
    padding: 2px 16px;
}

img{
    width: 250px;
    height: 220px;
}
</style>