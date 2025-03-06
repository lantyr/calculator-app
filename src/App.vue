<template>
  <div class="calculator">
    <h2>🖩 計算機</h2>
    <input type="text" v-model="display" disabled />

    <div class="buttons">
      <button @click="clearAll">AC</button>
      <button @click="deleteLast">DEL</button>
      <button @click="appendToDisplay('%')">%</button>
      <button @click="appendToDisplay('/')">÷</button>

      <button @click="appendToDisplay('7')">7</button>
      <button @click="appendToDisplay('8')">8</button>
      <button @click="appendToDisplay('9')">9</button>
      <button @click="appendToDisplay('*')">×</button>

      <button @click="appendToDisplay('4')">4</button>
      <button @click="appendToDisplay('5')">5</button>
      <button @click="appendToDisplay('6')">6</button>
      <button @click="appendToDisplay('-')">-</button>

      <button @click="appendToDisplay('1')">1</button>
      <button @click="appendToDisplay('2')">2</button>
      <button @click="appendToDisplay('3')">3</button>
      <button @click="appendToDisplay('+')">+</button>

      <button @click="appendToDisplay('0')" class="zero">0</button>
      <button @click="appendToDisplay('.')">.</button>
      <button @click="calculateResult">=</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const display = ref(""); // 計算機螢幕顯示的數字

// 新增數字或符號到輸入欄
const appendToDisplay = (value) => {
  display.value += value;
};

// 計算結果
const calculateResult = () => {
  try {
    display.value = eval(display.value); // 使用 eval() 計算（安全性注意）
  } catch (error) {
    display.value = "錯誤";
  }
};

// 刪除最後一個輸入字元
const deleteLast = () => {
  display.value = display.value.slice(0, -1);
};

// 清空所有輸入
const clearAll = () => {
  display.value = "";
};
</script>

<style scoped>
.calculator {
  width: 250px;
  margin: auto;
  text-align: center;
  background: #f8f9fa;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

input {
  width: 100%;
  height: 50px;
  font-size: 1.5rem;
  text-align: right;
  padding: 5px;
  margin-bottom: 10px;
  border: none;
  background: #eb0f7d;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 5px;
}

button {
  padding: 15px;
  font-size: 1.2rem;
  border: none;
  background: #b85402;
  cursor: pointer;
}

button:hover {
  background: #bdadad;
}

.zero {
  grid-column: span 2;
}
</style>
