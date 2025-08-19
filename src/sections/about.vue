<template>
    <div class="aboutSection">
        <h2>About Us</h2>
        <div class="aboutSection__content">
            <div class="aboutSection__text">
                <ion-icon name="desktop-outline"></ion-icon>
                <h2>Design</h2>
                <p>We craft innovative digital solutions tailored to your business needs, blending creativity with technical expertise.</p>
            </div>
            <div class="aboutSection__text">
                <ion-icon name="build-outline"></ion-icon>
                <h2>Construction</h2>
                <p>Our team builds robust and scalable IT infrastructures, ensuring reliability and performance for your organization.</p>
            </div>            
            <div class="aboutSection__text">
                <ion-icon name="reader-outline"></ion-icon>
                <h2>Management</h2>
                <p>We provide strategic consulting and ongoing support, empowering clients to achieve operational excellence and growth.</p>
            </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
    .aboutSection {
        width: 100%;
        text-align: center;
        padding-bottom: 200px;
        padding-top: 100px;

        ion-icon {
            font-size: 4rem;
            color: rgb(0, 102, 204);
        }

        h2 {
            font-family: 'Inter', sans-serif;
        }

        p{ 
            font-family: 'Roboto Condensed', sans-serif;
            font-size: 1rem;
        }

        .aboutSection__content {
            display: flex;
            justify-content: space-around;
            padding: 20px;
            gap: 20px;
            .aboutSection__text {
                padding-top: 40px;
                width: 30%;
                min-width: 220px;
                padding: 10px;
                background-color: white;
                border-radius: 5px;
                box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
                h2 {
                    margin-bottom: 10px;
                    color: #333;
                }
                p {
                    color: #666;
                }
            }
            @media (max-width: 900px) {
                flex-direction: column;
                align-items: center;
                .aboutSection__text {
                    width: 90%;
                    margin-bottom: 20px;
                }
            }
        }
    }

</style>