<template>
  <div class="container">
    <h1 class="text-center mt-5 mb-5">My Bank App</h1>

<!-- boxes -->
    <div class="row mb-5">
      <Box title="Ingresos" :data="sumPositives" />
      <Box title="Gastos" :data="expenses" />
      <Box title="Balance" :data="balance" />
    </div>  

<!-- form -->
    <div class="row">
      <New  @addItem="newItem"/>
    </div>

<!-- search field -->
  <Search v-model="searchTerm" />
<!-- Table -->
  <!-- <div>
    <ul class="mt-4 list-group">
      <li
          class="list-group-item d-flex justify-content-between align-items-center"
          v-for="item in filteredItems"
        >
          <span> {{ item.name }} </span>
          <div>
            <span
              :class="{
                'text-danger': item.amount < 0,
                'text-success': item.amount >= 0,
              }"
            >
              {{ item.amount }} €</span
            >
            <button class="btn btn-danger ms-3" @click="deleteItem(item.id)">
              Delete
            </button>
          </div>
        </li>
      </ul>
  </div> -->
  <ContentTable 
  :filteredItems="filteredItems" 
  @deleteTransaction="deleteItem" 
/>
  </div>
</template>

<script>
import Box from "./components/Box.vue";
import New from "./components/New.vue";
import Search from "./components/Search.vue";
import ContentTable from "./components/ContentTable.vue";

export default {
  name: "App",
  components: {
    Box,
    New,
    Search,
   ContentTable,
  },
  data() {
    return {
      items: [
        { id: 1, name: "Food", amount: -30 },
        { id: 2, name: "Groceries", amount: -42 },
        { id: 3, name: "Salary", amount: 130 },
      ],
      searchTerm:"",
      amount: 0,
    };
  },
  methods: {
    newItem(item) {
      
      if(item.name!=="" && item.amount!==0) {
        this.items.push(item);
        this.nextId++;
     } else {
      alert("te has olvidado a añadir un item")
     }
    },
    deleteItem(id) {
      this.items = this.items.filter(item => item.id!==id)
    },
  },
  computed: {
    sumPositives() {
    return this.items
      .filter(item => item.amount > 0)
      .reduce((sum, item) => sum + item.amount, 0);
    },
    expenses() {
      const expenses = this.items.filter((tran) => tran.amount < 0);
      const suma = expenses.reduce((acc, tran) => acc + tran.amount, 0);
      return suma
    },
    balance() {
      return this.items.reduce((acc, tran) => acc + tran.amount, 0);
    },
    filteredItems() {
      return this.items.filter(item => item.name.toLowerCase().includes(this.searchTerm.toLowerCase()))
    },
  }
};
</script>

<style>
.container{max-width: 800px;}
</style>
