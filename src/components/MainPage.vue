<template>
    <div class="video-background">
        <video autoplay loop muted playsinline>
            <source src="../assets/background-video.mp4" type="video/mp4">
            Ваш браузер не поддерживает видео.
        </video>
        <NavBar class="navigation"/>
        <div class="main-content">
            <h1>
                Ell Group.
            </h1>
            <p>
                Ell Group — ваши идеи, наше воплощение!
            </p>
            <button @click="goToContacts">
                ХОЧУ!
            </button>
        </div>
    </div>
</template>

<script setup>
import NavBar from "./MainPageComponents/NavBar.vue"

const goToContacts = () => {
    window.location.href = '#partners';
};
</script>

<style scoped>
@font-face {
    font-family: 'Akony';
    src: url('../../fonts/AKONY.woff2') format('woff2'),
        url('../../fonts/AKONY.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

.video-background {
    position: relative;
    overflow: hidden;
    height: 100vh;
}

video {
    position: absolute;
    top: 50%;
    left: 50%;
    min-width: 100%;
    min-height: 100%;
    width: auto;
    height: auto;
    z-index: -1;
    transform: translate(-50%, -50%);
}

.navigation{
    position: relative;
    z-index: 2;
}
.main-content {
    position: relative;
    z-index: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    padding: 20px;
}

.main-content h1 {
    font-size: 48px;
    font-weight: 800;
    font-family: Arial, Helvetica, sans-serif;
    color: #e8eef1;
    margin: 20px 0;
}

.main-content p {
    font-size: 18px;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 300;
    margin: 10px 0;
    color: #e8eef1;
}

.main-content button {
    background-color: #057dcd;
    border: none;
    padding: 15px 30px;
    font-size: 18px;
    font-weight: bold;
    color: #e8eef1;
    cursor: pointer;
    margin-top: 20px;
}

.main-content button:hover {
    background-color: #43b0f1;
}

.images {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    margin-top: 20px;
}

.images img {
    max-width: 150px;
    margin: 10px;
}

@media (max-width: 768px) {

    .navbar {
        flex-direction: column;
    }
    .main-content {
        margin-top:-30vh;
    }
    .main-content h1 {
        font-size: 36px;
    }

    .main-content p {
        font-size: 16px;
    }

    .main-content button {
        padding: 10px 20px;
        font-size: 16px;
    }

    .images img {
        max-width: 100px;
    }
}
</style>