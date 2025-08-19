<template>
    <footer class="contactSection">
        <div class="contactContent">
            <h2>Contact us</h2>
            <p>Olympusdcm@gmail.com</p>
            <div class="contactIcons">
                <a class="contactIcon" href="https://wa.me/573244764770" target="_blank" rel="noopener">
                    <ion-icon name="logo-whatsapp"></ion-icon>
                </a>
                <a class="contactIcon" href="https://www.linkedin.com/company/olympus-dcm/" target="_blank" rel="noopener">
                    <ion-icon name="logo-linkedin"></ion-icon> 
                </a>
                <a class="contactIcon" href="https://instagram.com/olympusdcm" target="_blank" rel="noopener">
                    <ion-icon name="logo-instagram"></ion-icon>
                </a>
            </div>
        </div>
        <div class="darkIconContainer">
            <img src="../../public/resources/VARIANTES/MainLogoWhite.png" alt="Olympus Logo" />
        </div>
    </footer>
</template>


<style scoped lang="scss">
    .contactSection {
        background: #222;
        color: #fff;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 150px 0 150px 0;
        width: 100%;
        gap: 60px;
        font-family: 'Inter', sans-serif;
        .contactContent {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            justify-content: center;
            h2 {
                margin-bottom: 10px;
                font-size: 2rem;
            }
            p {
                margin-bottom: 20px;
                font-size: 1.1rem;
            }
            .contactIcons {
                display: flex;
                gap: 20px;
                .contactIcon {
                    width: 48px;
                    height: 48px;
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    border-radius: 50%;
                    background: #333;
                    transition: background 0.2s;
                    text-decoration: none;
                    &:hover {
                        background: #666;
                    }
                    ion-icon {
                        font-size: 2rem;
                        color: #fff;
                    }
                }
            }
        }
        .darkIconContainer {
            display: flex;
            align-items: center;
            justify-content: center;
            img {
                width: 140px;
                height: auto;
                max-width: 100%;
            }
        }
        @media (max-width: 900px) {
            flex-direction: column;
            gap: 20px;
            .contactContent {
                align-items: center;
                text-align: center;
            }
            .darkIconContainer {
                margin-top: 20px;
            }
        }
    }

</style>