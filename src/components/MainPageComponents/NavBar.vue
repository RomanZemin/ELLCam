<template>
    <div class="navbar">
        <a href="#catalog" class="navpage">
            Каталог
        </a>
        <a href="#about" class="navpage">
            О Нас
        </a>
        <a href="#reviews" class="navpage">
            Отзывы
        </a>
        <div class="logo">
            Ell Group
        </div>
        <a href="#partners" class="navpage">
            Партнерам
        </a>
        <a href="#faq" class="navpage">
            FAQ
        </a>
        <a href="#contacts" class="navpage">
            Контакты
        </a>
    </div>
</template>

<script setup>
</script>

<style scoped>
@font-face {
  font-family: 'Akony';
  src: url('../../fonts/AKONY.woff2') format('woff2'),
       url('../../fonts/AKONY.woff') format('woff');
  font-weight: normal;
  font-style: normal;
}

.navbar {
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
    background-color: rgba(67, 176, 241, 0);
    color: #e8eef1;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.navbar .logo {
    font-size: 24px;
    font-weight: bold;
    margin: 0 30px;
    font-family: 'Akony', sans-serif;
}

.navbar .navpage {
    text-decoration: none;
    color: #e8eef1;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    margin: 0 15px;
    font-size: 16px;
}

.navbar .navpage:hover {
    text-decoration: underline;
}
</style>