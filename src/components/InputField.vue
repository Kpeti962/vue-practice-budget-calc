<script setup>
import { ref } from "vue";
const base = ref(100000);
const inputValue = ref();
const typeOfMoney = ref();

const selected = ref(null);
const income_list = ref([]);
const expense_list = ref([]);

const addBudgetHandler = () => {
  console.log(typeOfMoney.value);
  if (inputValue.value > 0) {
    if (selected.value === "income") {
      base.value += inputValue.value;
      income_list.value.push({
        price: inputValue.value,
        type: typeOfMoney.value,
      });
    } else if (selected.value === "expense") {
      base.value -= inputValue.value;
      expense_list.value.push({
        price: inputValue.value,
        type: typeOfMoney.value,
      });
    }
  }
};
</script>
<template>
  <div class="input-field">
    <input v-model="inputValue" type="number" />
    <select v-model="selected" name="" id="">
      <option value="income">Bevétel</option>
      <option value="expense">Kiadás</option>
    </select>
    <select v-model="typeOfMoney" name="" id="">
      <option value="Fizetés">Fizetés</option>
      <option value="Rezsi">Rezsi</option>
      <option value="Dohánybolt">Dohánybolt</option>
      <option value="Élelmiszer">Élelmiszer</option>
      <option value="Szórakozás">Szórakozás</option>
      <option value="Egészségügy">Egészségügy</option>
    </select>
    <button @click="addBudgetHandler">Hozzáad</button>
  </div>
  <div class="summary-field">
    <div class="income">
      <ul class="income-list">
        <li v-for="income in income_list" :key="income">
          <span>{{ income.type }}:</span>
          <h4>+ {{ income.price }} Ft</h4>
          <button>Törlés</button>
        </li>
      </ul>
    </div>
    <div class="expense">
      <ul class="expense-list">
        <li v-for="expense in expense_list" :key="expense">
          <span>{{ expense.type }}:</span>
          <h4>- {{ expense.price }} Ft</h4>
          <button>Törlés</button>
        </li>
      </ul>
    </div>
  </div>
  <h4>Összesen: {{ new Intl.NumberFormat().format(base) }} Ft</h4>
</template>
<style>
body {
  text-align: center;
  background: radial-gradient(
    circle,
    rgba(232, 227, 229, 1) 0%,
    rgba(203, 203, 203, 1) 38%,
    rgba(205, 205, 205, 1) 51%,
    rgba(204, 209, 167, 1) 100%
  );
}
.input-field {
  width: 100%;
}
.summary-field {
  display: flex;
  height: 400px;
}
.income {
  background-color: greenyellow;
  width: 50%;
  overflow: auto;
  border-radius: 20px;
  margin: 5px;
}
.income-list {
  list-style-type: none;
  font-size: 18px;
  font-weight: bold;
}

.expense {
  background-color: red;
  width: 50%;
  overflow: auto;
  border-radius: 20px;
  margin: 5px;
}
.expense-list {
  list-style-type: none;
  font-size: 18px;
  font-weight: bold;
}
li {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h4 {
  align-items: flex-start;
}
</style>
