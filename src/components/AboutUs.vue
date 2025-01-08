<template>
    <section id="about">
        <div class="partners section">
            <h2>
                О НАС
            </h2>
            <div class="about-container">
                <img src="../assets/logo.png" class="ell-store-logo" />
                <p>
                    <label class="company-name">Ell Group</label> - это динамичная компания, предоставляющая
                    высококачественные товары и услуги для клиентов,
                    стремящихся к совершенству. Мы верим, что каждая деталь значима, и наша миссия — вдохновлять людей и
                    помогать им творить уникальные истории через наши изделия.
                </p>
            </div>
        </div>
    </section>
</template>

<script setup>

</script>

<style scoped>
.section {
    padding: 20px;
    text-align: center;
}

.partners {
    background-color: #1a1a1a;
    color: #e8eef1;
    padding: 40px 20px;
}

.partners h2 {
    font-size: 2em;
    font-weight: 550;
    color: #43b0f1;
    margin-bottom: 20px;
}

.partners .about-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row; /* По умолчанию - горизонтально */
}

.company-name {
    color: #43b0f1;
}

.ell-store-logo {
    width: 350px;
    margin-right: 20px;
    border-radius: 15px;
}

.partners p {
    width: 400px;
    font-size: 16px;
    margin-bottom: 10px;
    word-wrap: break-word;
}

@media (max-width: 768px) {
    .partners .about-container {
        flex-direction: column; 
        align-items: center;
    }

    .ell-store-logo {
        margin-right: 0;
        margin-bottom: 20px;
    }

    .partners p {
        width: auto;
    }
}
</style>