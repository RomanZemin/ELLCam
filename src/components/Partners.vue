<template>
    <section id="partners">
        <div class="partners section">
            <h2> ДЛЯ ПАРТНЕРОВ И ПОКУПАТЕЛЕЙ </h2>
            <p> Мы рады возможности сотрудничества! </p>
            <p> Для получения коммерческих предложений и вопросов по покупке, пожалуйста, обращайтесь в Telegram:
                <a href="https://t.me/Ell_Group"> @Ell_Group </a>
            </p>
            <p>
                Номер телефона:
                <a href="tel:+7(999)3116000">
                    +7 (999) 311-60-00
                </a>
            </p>
            <button class="button" @click="openModal">
                ОСТАВИТЬ ЗАЯВКУ
            </button>
        </div>
        <div v-if="isModalOpen" class="modal-overlay" @click="closeModal">
            <div class="modal-content" @click.stop>
                <form @submit.prevent="submitForm">
                    <h3>Форма заявки</h3>
                    <input type="text" v-model="formData.name" required placeholder="Имя"/>
                    <input type="email" v-model="formData.email" required placeholder="Почта"/>
                    <input 
                        type="tel" 
                        v-model="formData.phone" 
                        required 
                        @input="formatPhone"
                        placeholder="+7(999)-999-99-99"
                    />
                    <textarea v-model="formData.message" required placeholder="Текст заявки"></textarea>

                    <button type="submit" class="submit-button">Отправить заявку</button>
                </form>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'

const isModalOpen = ref(false);
const formData = ref({
    name: '',
    email: '',
    phone: '',
    message: ''
});

const validateEmail = (email) => {
    const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return emailPattern.test(email);
};

const validatePhone = (phone) => {
    const phonePattern = /^\+7\(\d{3}\)-\d{3}-\d{2}-\d{2}$/;
    return phonePattern.test(phone);
};

const formatPhone = (event) => {
    const input = event.target.value.replace(/\D/g, '');
    let formattedPhone = '+7(';

    if (input.length > 1) {
        formattedPhone += input.substring(1, 4);
    }
    if (input.length >= 4) {
        formattedPhone += ')-' + input.substring(4, 7);
    }
    if (input.length >= 7) {
        formattedPhone += '-' + input.substring(7, 9);
    }
    if (input.length >= 9) {
        formattedPhone += '-' + input.substring(9, 11);
    }

    formData.value.phone = formattedPhone;
};

const openModal = () => {
    isModalOpen.value = true;
};

const closeModal = () => {
    isModalOpen.value = false;
    formData.value = { name: '', email: '', phone: '', message: '' };
};

const submitForm = () => {
    const { name, email, phone, message } = formData.value;

    if (!validateEmail(email)) {
        alert('Введите корректный адрес электронной почты.');
        return;
    }

    if (!validatePhone(phone)) {
        alert('Введите номер телефона в формате +7(999)-999-99-99.');
        return;
    }

    Email.send({
        Host: "smtp.yourisp.com",
        Username: "your_email@example.com",
        Password: "your_password", 
        To: 'ell_group99@mail.ru',
        From: email,
        Subject: "Новая заявка",
        Body: `Имя: ${name}<br>Почта: ${email}<br>Телефон: ${phone}<br>Сообщение: ${message}`
    })
    .then(() => {
        alert("Заявка отправлена!");
        closeModal();
    })
    .catch(() => {
        alert('Ошибка при отправке заявки.');
    });
};
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

.partners p {
    font-size: 16px;
    margin-bottom: 10px;
}

.partners a {
    color: #43b0f1;
    text-decoration: none;
}

.partners .button {
    background-color: #057dcd;
    color: #e8eef1;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
    font-size: 16px;
    margin-top: 20px;
}

.partners .button:hover {
    background-color: #43b0f1;
    color: #e8eef1;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
    font-size: 16px;
    margin-top: 20px;
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
    width: 60vh;
    text-align: center;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
}

.modal-content h3 {
    text-align: center;
    word-wrap: break-word;
    font-size: 16px;
    margin-bottom: 20px;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 550;
    color: #1e3d58;
}

label {
    display: block;
    margin: 10px 0 5px;
    font-weight: bold;
}

input, textarea {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 16px;
}

input:focus, textarea:focus {
    border-color: #43b0f1;
    outline: none;
}

.submit-button {
    background-color: #43b0f1;
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
 cursor: pointer;
    font-size: 16px;
    transition: background-color 0.3s;
}

.submit-button:hover {
    background-color: #057dcd;
}

.close-button {
    background-color: #e74c3c;
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    margin-left: 10px;
    transition: background-color 0.3s;
}

.close-button:hover {
    background-color: #c0392b;
}
</style>