<template>
  <div>
    <textarea v-model="jsonData" rows="10" cols="50"></textarea>
    <button @click="saveChanges">Перезаписать</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      jsonData: ''  // Здесь будет храниться содержимое JSON файла
    };
  },
  mounted() {
    // Подгрузка данных из JSON файла при загрузке компонента
    this.loadJsonData();
  },
  methods: {
    async loadJsonData() {
      try {
        const response = await axios.get('en.json');
        this.jsonData = JSON.stringify(response.data, null, 2);
      } catch (error) {
        console.error('Ошибка при загрузке JSON файла:', error);
      }
    },
    async saveChanges() {
      try {
        const newData = JSON.parse(this.jsonData);
        await axios.post('en.json', newData);
        console.log('JSON файл успешно перезаписан');
      } catch (error) {
        console.error('Ошибка при перезаписи JSON файла:', error);
      }
    }
  }
};
//для бэка
/*
const express = require('express');
const bodyParser = require('body-parser');
const fs = require('fs');
const app = express();
const port = 3000;

app.use(bodyParser.json());

app.get('/locale/en', (req, res) => {
  try {
    const jsonData = fs.readFileSync('../../locale/en.json', 'utf8');
    res.json(JSON.parse(jsonData));
  } catch (error) {
    console.error('Ошибка при чтении JSON файла:', error);
    res.status(500).json({ error: 'Ошибка при чтении JSON файла' });
  }
});

app.post('/locale/en', (req, res) => {
  try {
    const newData = req.body;
    fs.writeFileSync('../../locale/en.json', JSON.stringify(newData, null, 2));
    res.json({ message: 'JSON файл успешно перезаписан' });
  } catch (error) {
    console.error('Ошибка при записи JSON файла:', error);
    res.status(500).json({ error: 'Ошибка при записи JSON файла' });
  }
});

app.listen(port, () => {
  console.log(`Сервер запущен на порту ${port}`);
});
*/
</script>

