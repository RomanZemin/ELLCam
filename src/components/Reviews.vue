<template>
    <section id="reviews">
        <div class="container">
            <div class="lookbook">
                <h2>
                    ОТЗЫВЫ
                </h2>
                <div class="images">
                    <img height="300" src="../assets/Reviews/1.png" width="300" />
                    <img height="300" src="../assets/Reviews/2.png" width="300" />
                    <img height="300" src="../assets/Reviews/3.png" width="300" />
                    <img height="300" src="../assets/Reviews/4.png" width="300" />
                    <img height="300" src="../assets/Reviews/5.png" width="300" />
                    <img height="300" src="../assets/Reviews/6.png" width="300" />
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>

</script>

<style scoped>
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

.lookbook {
    text-align: center;
    margin-top: 40px;
}

.lookbook h2 {
    font-size: 2em;
    font-weight: 550;
    color: #1e3d58;
    margin-bottom: 20px;
}

.lookbook .images {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    margin-top: 20px;
}

.lookbook .images img {
    width: 300px;
    height: 300px;
    object-fit: scale-down;
}

@media (max-width: 768px) {
    .content {
        flex-direction: column;
        align-items: center;
    }

    .content .text {
        text-align: center;
    }

    .lookbook .images img {
        width: 100%;
        height: auto;
    }
}
</style>