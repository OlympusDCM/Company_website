<template>
    <div class="productsSection">
        <div class="productsSection__content">
            <h2>Some of our Products</h2>
            <div class="carousel">
                <button class="carousel__arrow" @click="prevProduct">&#8592;</button>
                <div class="carousel__item">
                    <template v-if="products[current].img">
                        <img :src="products[current].img" :alt="products[current].name" />
                    </template>
                    <template v-else>
                        <div class="carousel__icon-placeholder">
                            <ion-icon name="help-circle-outline"></ion-icon>
                        </div>
                    </template>
                    <h3>{{ products[current].name }}</h3>
                    <p>Coming soon...</p>
                </div>
                <button class="carousel__arrow" @click="nextProduct">&#8594;</button>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const products = [
    { img: null, name: 'Pormesa' },
    { img: null, name: 'Technical' },
    { img: null, name: 'Flare' },
    { img: null, name: 'Morada' }
];
const current = ref(0);

function prevProduct() {
    current.value = (current.value - 1 + products.length) % products.length;
}
function nextProduct() {
    current.value = (current.value + 1) % products.length;
}
</script>

<style scoped lang="scss">

.productsSection {
    width: 100%;
    padding-top: 50px;
    padding-bottom: 200px;

    h2 {
        font-family: 'Inter', sans-serif;
        margin-bottom: 20px;
    }


    .productsSection__content {
        text-align: center;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        font-family: 'Roboto Condensed', sans-serif;

        h3 {
        
            margin-bottom: 20px;
        }
    }
}


.carousel {
    padding-top: 20px;
    padding-bottom: 20px;
    width: 80%;
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    gap: 2rem;
}
.carousel__arrow {
    background: #eee;
    border: none;
    font-size: 1.2rem;
    cursor: pointer;
    padding: 0.5rem 1rem;
    border-radius: 50%;
    transition: background 0.2s;
    &:hover {
        background: #ccc;
    }
}
.carousel__item {
    text-align: center;
    min-width: 200px;
    border-radius: 5px;
    border: 1px solid gainsboro;
    width: 80%;
}
.carousel__item img {
    width: 120px;
    height: 120px;
    object-fit: cover;
    margin-bottom: 1rem;
    background: #f5f5f5;
    border-radius: 1rem;
}

.carousel__icon-placeholder {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 120px;
    margin: 0 auto 1rem auto;
    background: #f5f5f5;
    ion-icon {
        font-size: 5rem;
        color: #bbb;
    }
}
</style>