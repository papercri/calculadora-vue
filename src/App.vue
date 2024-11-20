<template>
  <div class="container mx-auto">
<h1 class="font-bold text-3xl text-center mb-3">My Bank App</h1>
<div class="grid grid-cols-3 border">
  <div>Income: {{income()}}</div>
  <div>Expenses:  {{expenses()}}</div>
  <div>Balance:  {{balance()}}</div>
</div>
<Transactions :transactions="transactions" @deleteTransaction="deleteTransaction" />
</div>
</template>

<script>
import Transactions from "./components/Transactions.vue";
export default {
name: "App",
components: {
  Transactions,
  },
data () {
	return {
		transactions: [
      {id: 1,
        name: "Salario",
        amount: 500
      },
      {id: 2,
        name: "Supermercado",
        amount: -15
      },
      {id: 3,
        name: "Ropa",
        amount: -50
      },
    ]
	}
},
methods: {
    income() {
      const incomes = this.transactions.filter((tran) => tran.amount > 0);
      const suma = incomes.reduce((acc, tran) => acc + tran.amount, 0);
      return suma
    },
    expenses() {
      const expenses = this.transactions.filter((tran) => tran.amount < 0);
      const suma = expenses.reduce((acc, tran) => acc + tran.amount, 0);
      return suma
    },
    balance() {
      const suma = this.transactions.reduce((acc, tran) => acc + tran.amount, 0);
      return suma
    },
    deleteTransaction(id) {
      this.transactions = this.transactions.filter((tran) => tran.id !== id.id);
    }
  },
}
</script>

<style scoped>

</style>
