<template>
    <div class="productsSection">
        <div class="productsSection__content">
            <h2>Some of our Products</h2>
            <div class="carousel">
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
                <div class="carousel__arrows">
                    <button class="carousel__arrow" @click="prevProduct">&#8592;</button>
                    <button class="carousel__arrow" @click="nextProduct">&#8594;</button>
                </div>
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
    padding: 32px 0;
    width: 98vw;
    max-width: 520px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1.5rem;
    box-sizing: border-box;
// ...existing code...
}

.carousel__item {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    border: 1px solid #ddd;
    padding: 1rem;
    border-radius: 8px;
    width: 70%;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    img {
        width: 100%;
        height: auto;
        max-width: 100%;
        border-radius: 8px;
        margin-bottom: 1rem;
    }
    h3 {
        font-size: 1.5rem;
        margin-bottom: 0.5rem;
    }
    p {
        font-size: 1rem;
        color: #666;
    }
}
.carousel__arrows {
    display: flex;
    flex-direction: row;
    gap: 1.5rem;
    align-items: center;
    justify-content: center;
    margin-top: 1.2rem;
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
// ...existing code...
</style>