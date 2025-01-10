<template>
    <section id="catalog">
        <div class="container">
            <div class="content">
                <h2>
                    КАТАЛОГ
                </h2>
            </div>
            <div class="gallery" ref="gallery" @mouseenter="stopScroll" @mouseleave="startScroll" @mousedown="startDrag"
                @mouseup="stopDrag" @mousemove="onMouseMove">
                <div class="gallery-item" v-for="(item, index) in items" :key="index">
                    <img class="gallery-image" :src="item.image" alt="Product Image" />
                    <p class="gallery-text">{{ item.name }}</p>
                    <p class="price">{{ item.price }} ₽</p>
                    <button class="gallery-button" @click="openModal(item)">Подробнее</button>
                </div>
            </div>
            <div v-if="isModalOpen" class="modal-overlay" @click="closeModal">
                <div class="modal-content" @click.stop>
                    <h3>{{ selectedItem.name }}</h3>
                    <img :src="selectedItem.image" alt="Product Image" />
                    <p>Цена: {{ selectedItem.price }} ₽</p>
                    <p class="description">{{ selectedItem.desc }}</p>
                    <button @click="closeModal">Закрыть</button>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import {
    ref,
    onMounted,
    onUnmounted
} from 'vue'

import { items } from './products'

const isModalOpen = ref(false);
const selectedItem = ref({});
const gallery = ref(null);

let scrollInterval = null;
let isDragging = false;
let startX = 0;
let scrollLeft = 0;
let scrollBack = false;

const openModal = (item) => {
    selectedItem.value = item;
    isModalOpen.value = true;
};

const closeModal = () => {
    isModalOpen.value = false;
};

const startScroll = () => {
    scrollInterval = setInterval(() => {
        if (gallery.value) {
            if (!scrollBack)
                gallery.value.scrollTo({ left: gallery.value.scrollLeft += 1, behavior: 'smooth' });
            else
                gallery.value.scrollTo({ left: gallery.value.scrollLeft -= 1, behavior: 'smooth' });
            if (gallery.value.scrollLeft + gallery.value.clientWidth >= gallery.value.scrollWidth) {
                scrollBack = !scrollBack;
            }
            if (gallery.value.scrollLeft <= 0) {
                scrollBack = !scrollBack;
            }
        }
    }, 15);
};

const stopScroll = () => {
    if (scrollInterval) {
        clearInterval(scrollInterval);
        scrollInterval = null;
    }
};

const startDrag = (e) => {
    isDragging = true;
    startX = e.pageX - gallery.value.offsetLeft;
    scrollLeft = gallery.value.scrollLeft;
    stopScroll();
};

const stopDrag = () => {
    isDragging = false;
};

const onMouseMove = (e) => {
    if (!isDragging) return;
    e.preventDefault();
    const x = e.pageX - gallery.value.offsetLeft;
    const walk = (x - startX) * 1;
    gallery.value.scrollLeft = scrollLeft - walk;
};

onMounted(() => {
    startScroll();
});

onUnmounted(() => {
    stopScroll();
});
</script>

<style scoped>
section {
    text-align: center;
}

.container {
    margin-top: 20px;
    position: relative;
    width: 100%;
    height: 650px;
    overflow: hidden;
    text-align: center;
}

.content {
    text-align: center;
}

.content h2 {
    font-size: 2em;
    font-weight: 550;
    color: #1e3d58;
}

.content p {
    font-size: 1em;
    line-height: 1.5em;
}

.gallery {
    position: absolute;
    top: 20%;
    display: flex;
    overflow: auto;

    width: 100%;
    -ms-overflow-style: none;
    scrollbar-width: none;
}

.gallery-item {
    flex: 0 0 auto;
    display: flex;
    flex-direction: column;
    margin: 1rem;
    align-items: center;
    justify-content: center;
    box-shadow: 0.3rem 0.4rem 0.4rem rgba(0, 0, 0, 0.4);
    overflow: hidden;
    border-radius: 5px;
}

.gallery::-webkit-scrollbar {
    display: none;
}

.gallery-image {
    display: block;
    width: 17em;
    height: 14em;
    object-fit: scale-down;
    transition: transform 400ms ease-out;
}

.gallery-text {
    margin-top: 7px;
    text-align: center;
    word-wrap: break-word;
    max-width: 200px;
    font-size: 16px;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 550;
    color: #43b0f1;
}

.price {
    margin: 25px 0;
    font-size: 1.5em;
    font-weight: 700;
    color: #1e3d58;
}

.gallery-button {
    border: 4px solid #43b0f1;
    border-radius: 4px;
    padding: 8px;
    font-size: 22px;
    font-weight: 800;
    font-family: Arial, Helvetica, sans-serif;
    color: #43b0f1;
    margin-top: 10px;
    margin-bottom: 10px;
}

.gallery-button:hover {
    background: #43b0f1;
    color: #e8eef1;
    transition: 0.6s;
}

.gallery-image:hover {
    transform: scale(1.25);
}

.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    align-items: center;
    justify-content: center;
}

.modal-content {
    background: white;
    padding: 20px;
    border-radius: 8px;
    height: auto;
    width: 60vh;
    text-align: center;
}

.modal-content h3 {
    text-align: center;
    word-wrap: break-word;
    font-size: 16px;
    margin-bottom: 15px;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 550;
    color: #43b0f1;
}

.modal-content img {
    width: 80em;
    height: 14em;
    object-fit: scale-down;
}

.modal-content p {
    font-size: 2em;
    font-weight: 700;
    color: #1e3d58;
}

.modal-content .description {
    font-size: 1em;
    font-weight: 300;
    color: #1e3d58;
}


.modal-content button {
    border: 4px solid #43b0f1;
    border-radius: 4px;
    padding: 8px;
    font-size: 22px;
    font-weight: 800;
    font-family: Arial, Helvetica, sans-serif;
    color: #43b0f1;
    margin-top: 10px;
    margin-bottom: 10px;
}

.modal-content button:hover {
    background: #43b0f1;
    color: #e8eef1;
    transition: 0.6s;
}

@media (max-width: 768px) {
    .content {

        top: 20%;

    }

    .images {

        top: 60%;

    }
}
</style>