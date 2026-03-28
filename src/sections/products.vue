<template>
    <div class="productsSection">
        <div class="productsSection__content">
            <h2>Some of our customers and projects</h2>
            <br>
            <div class="mosaic">
                <div
                    v-for="(product, index) in products"
                    :key="index"
                    class="mosaic__item"
                    :class="{ 'mosaic__item--clickable': product.url }"
                    :style="{ animationDelay: `${index * 0.1}s` }"
                    @click="product.url && openProductUrl(product.url)"
                >
                    <template v-if="product.img">
                        <div class="mosaic__image-card">
                            <img :src="product.img" :alt="product.name" />
                            <div class="mosaic__overlay">
                                <span>{{ product.name }}</span>
                            </div>
                        </div>
                    </template>
                    <template v-else>
                        <div class="mosaic__fallback">
                            <div class="mosaic__icon-placeholder">
                                <ion-icon name="help-circle-outline"></ion-icon>
                            </div>
                            <h3>{{ product.name }}</h3>
                            <p>Coming soon...</p>
                        </div>
                    </template>
                </div>
            </div>
        </div>
    </div>
</template>
<script setup>

const products = [
    { img: "../../public/pics/EnviosVenezuela.png", name: 'Envios Venezuela', url: 'https://www.enviosvenezuela.es/enviosve/public/index.php' },
    { img: "../../public/pics/Bitsafve.png", name: 'Bitsafve', url: 'https://bitsaveapp.com/es/' },
    { img: "../../public/pics/TuRegistroEscolar.png", name: 'Tu registro escolar', url: 'https://www.turegistroescolar.com/' },
    { img: "../../public/pics/Celucenter.png", name: 'Celufio App', url: 'https://play.google.com/store/apps/details?id=mx.celufio.clientes&hl=es_VE' },
    { img: "../../public/pics/BusinessOptics.png", name: 'Business Optics', url: 'https://www.businessoptics.org/' },
    { img: "../../public/pics/Gather.png", name: 'Gather Technology', url: 'https://www.gatherverify.com/' },
    { img: null, name: 'Pormesa' },
    { img: null, name: 'Technical' },
    { img: null, name: 'Flare' },
    { img: null, name: 'Morada' }
];

function openProductUrl(url) {
    window.open(url, '_blank', 'noopener noreferrer');
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


.mosaic {
    padding: 10px 0;
    padding-bottom: 200px;
    width: 98%;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(3, 33%);
    box-sizing: border-box;
}

@media (max-width: 900px) {
    .mosaic {
        grid-template-columns: repeat(1, 100%);
    }
}

.mosaic__item {
    position: relative;
    overflow: hidden;
    min-height: 260px;
    box-shadow: 0 12px 35px rgba(0, 0, 0, 0.08);
    background: #111;
    transition: transform 0.35s ease, box-shadow 0.35s ease;
    opacity: 0;
    animation: fadeIn 0.5s ease-in-out forwards;
    &:hover {
        transform: translateY(-4px);
        box-shadow: 0 18px 40px rgba(0, 0, 0, 0.16);
    }
    &.mosaic__item--clickable {
        cursor: pointer;
    }
}

.mosaic__image-card {
    position: relative;
    width: 100%;
    height: 100%;
}

.mosaic__image-card img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    transition: transform 0.4s ease;
}

.mosaic__item:hover .mosaic__image-card img {
    transform: scale(1.05);
}

.mosaic__overlay {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    padding: 1.5rem;
    background: linear-gradient(180deg, rgba(0, 0, 0, 0) 40%, rgba(0, 0, 0, 0.72) 100%);
    opacity: 0;
    transition: opacity 0.35s ease;
}

.mosaic__item:hover .mosaic__overlay {
    opacity: 1;
}

.mosaic__overlay span {
    color: #fff;
    font-size: 1.2rem;
    font-weight: 700;
    letter-spacing: 0.02em;
}

.mosaic__fallback {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    padding: 2rem 1rem;
    color: #333;
    background: #fff;
    min-height: 250px;
}

.mosaic__fallback h3 {
    margin: 0;
    font-size: 1.3rem;
}

.mosaic__fallback p {
    margin: 0;
    color: #666;
}

.mosaic__icon-placeholder {
    width: 100px;
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 16px;
    ion-icon {
        font-size: 2rem;
        color: #666;
    }
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
</style>