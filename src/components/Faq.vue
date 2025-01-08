<template>
    <section id="faq">
        <div class="faq section">
            <h2>ЧАСТО ЗАДАВАЕМЫЕ ВОПРОСЫ</h2>
            <div class="faq-container">
                <div class="faq-item" v-for="(item, index) in faqItems" :key="index">
                <h3 @click="toggleAnswer(index)" class="faq-question">
                    {{ item.question }}
                    <div class="underline"></div>
                </h3>
                <p v-if="item.isOpen" class="faq-answer">
                    {{ item.answer }}
                </p>
            </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';

const faqItems = ref([
    {
        question: 'Как я могу оформить заказ?',
        answer: 'Чтобы оформить заказ, добавьте товары в корзину и следуйте инструкциям на экране. Выберите способ доставки и оплатите заказ.',
        isOpen: false
    },
    {
        question: 'Какой срок доставки?',
        answer: 'Срок доставки зависит от вашего местоположения и выбранного способа доставки. Обычно доставка по Москве занимает 3-4 часа, а по России — от 3 до 7 дней.',
        isOpen: false
    },
    {
        question: 'Как я могу отслеживать свой заказ?',
        answer: 'После отправки заказа вы получите номер для отслеживания на указанный вами электронный адрес. Вы можете использовать его на сайте службы доставки.',
        isOpen: false
    },
    {
        question: 'Что делать, если я получил поврежденный товар?',
        answer: 'Если вы получили поврежденный товар, пожалуйста, свяжитесь с нашей службой поддержки в течение 24 часов. Мы поможем вам решить эту проблему.',
        isOpen: false
    },
    {
        question: 'Как я могу вернуть товар?',
        answer: 'Для возврата товара, пожалуйста, свяжитесь с нашей службой поддержки. Мы предоставим вам инструкции по возврату и оформлению необходимых документов.',
        isOpen: false
    },
    {
        question: 'Как я могу связаться с вашей службой поддержки?',
        answer: 'Вы можете связаться с нашей службой поддержки по телефону или электронной почте, указанным на нашем сайте. Мы всегда готовы помочь вам!',
        isOpen: false
    }
]);

const toggleAnswer = (index) => {
    faqItems.value[index].isOpen = !faqItems.value[index].isOpen;
};
</script>

<style scoped>
p {
    word-wrap: break-word;
    max-width: 1500px;
}
.section{
    justify-content: center;
    align-items: center;
}
.faq {
    display: flex;
    background-color: white;
    color: black;
    padding: 40px 20px;
    flex-direction: column;
}

.faq h2 {
    font-size: 2em;
    font-weight: 550;
    color: #1e3d58;
    margin-bottom: 20px;
}
.faq-container{
    align-items:flex-start;
}
.faq-question {
    font-size: 1.5em;
    font-weight: 500;
    color: #1e3d58;
    margin-top: 20px;
    margin-bottom: 10px;
    cursor: pointer;
}
.underline{
    border: 1px solid #1e3d58;
}

.faq-answer {
    font-size: 16px;
    font-weight: 550;
    max-width: 600px;
    margin-bottom: 10px;
    word-wrap: break-word;
    transition: max-height 0.3s ease;
}
</style>