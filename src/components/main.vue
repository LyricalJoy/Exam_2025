<script setup>
import {ref, reactive} from 'vue'

// переменные для сохранения данных

const userName = ref('');
const number1 = ref('');
const nameError = ref('');
const error = ref('');



// функция валидация полей
function validateAnswer(question) {
  const val = question.userAnswer.trim()

  if (!val) {
    errors.value[question.id] = 'Поле обязательно для заполнения'
    return false
  }

  if (question.validation === 'rus' && !/^[А-Яа-яЁё\s]+$/.test(val)) {
    errors.value[question.id] = 'Только русские буквы и пробелы'
    return false
  }

  if (question.validation === 'num' && !/^\d+$/.test(val)) {
    errors.value[question.id] = 'Только цифры'
    return false
  }

  errors.value[question.id] = ''
  return true
} 

</script>

<template>
    <div class="form">   
        <h1>Форма заявки.</h1>
        <h2>Для тогоч тобы закзать услугу фотостудии заполните форму!</h2>
        <label> Имя<input type="text" v-model="userName" placeholder="Иван"/></label>
        <p v-if="nameError" class="error">{{ nameError }}</p>
        <label> Фамилия<input type="test" placeholder="Иванов"></label>
        <p v-if="nameError" class="error">{{ nameError }}</p>
        <label> Отчетсво<input type="test" placeholder="Иванович"></label>
        <p v-if="nameError" class="error">{{ nameError }}</p>
        <label> Тел.<input type="test" placeholder="+7 948 334 89 44    "></label>
        <p v-if="nameError" class="error">{{ nameError }}</p>
        <label> Почта<input type="test" placeholder="Иван"></label>
        <p v-if="nameError" class="error">{{ nameError }}</p>
        <label> Дата аренды<input type="text" v-model="number1" placeholder="03.03.2025"></label>
        <p v-if="error" class="error">{{ error }}</p>
        <label> Время аренды<input type="number" placeholder="15:00"></label>
        <p v-if="nameError" class="error">{{ nameError }}</p>
        <button @click="order">Заказать</button>
        <p v-if="error" class="error">{{ error }}</p>
    </div>
    <div class="footer">
        <p>"ООО" Фотостудия “Салют” все права защищены.</p>
    </div>
</template>

<style scoped>
input {
  padding: 8px;
  font-size: 14px;
  margin-bottom: 10px;
  width: 100%;
  max-width: 300px;
}

.error {
  color: red;
  font-size: 14px;
}
.form {
    display: flex;
    justify-content: center;
    flex-direction: column;
    gap: 20px;
}
button {
    margin-left: 500px;
    justify-content: center;
    width: 200px;
    background-color: tomato;
}
.footer {
    margin-top: 100px;
    width: 1200px;
    height: 300px;
    background-color: rgb(131, 131, 131);
}
p {
    padding: 70px;
}
input {
    margin-left: 20px;
    padding-left: 20px;
}
</style>
