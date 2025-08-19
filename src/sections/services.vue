<template>
    <div class="servicesSection">
        <div class="servicesSection__content">
            <h2>Our Services</h2>
            <br>
            <br>
            <div class="servicesList">
                <div class="serviceItem" v-for="(service, index) in services" :key="index">
                    <ion-icon :name="service.icon"></ion-icon>
                    <h3>{{ service.name }}</h3>
                </div>

            </div>
        </div>

    </div>
</template>

<script>
import { ref } from 'vue';
const services = ref([
    { icon: 'code-slash', name: 'Software Development' },
    { icon: 'server', name: 'Server Management' },
    { icon: 'build', name: 'Legacy Application Maintenance' },
    { icon: 'color-palette', name: 'Web Design' },
    { icon: 'brush', name: 'Graphic Design' },
    { icon: 'desktop', name: 'Landing Pages Development' },
    { icon: 'clipboard', name: 'Project Management' },
    { icon: 'help-buoy', name: 'Project Consulting Services' },
    { icon: 'cube', name: 'Architecture Solutions' }
]);
export default {
    setup() {
        return { services };
    }
};


</script>

<style scoped lang="scss">
    .servicesSection {
        padding: 50px;
        padding-top: 40px;
        padding-bottom: 150px;

        h2 {
            font-family: 'Inter', sans-serif;
        }

        .servicesSection__content {
            text-align: center;
            h2 {
                margin-bottom: 20px;
            }
            .servicesList {
                display: flex;
                justify-content: center;
                gap: 40px;
                flex-wrap: wrap;

                .serviceItem {
                    background: white;
                    border: 1px solid #ddd;
                    border-radius: 8px;
                    padding: 20px;
                    width: 250px;
                    text-align: center;
                    font-family: 'Inter', sans-serif;

                    ion-icon {
                        font-size: 3rem;
                        color: rgb(0, 102, 204);
                    }

                    h3 {
                        margin-top: 10px;
                        font-size: 1.2em;

                    }


                }
            }
        }
    }


</style>