<template>
    <div class="col-8 offset-2 d-flex flex-column">
   
      <div class="d-flex mb-3">
        <div class="form-check me-4">
          <input
            type="radio"
            id="income"
            class="form-check-input"
            value="income"
            v-model="transactionType"
          />
          <label class="form-check-label" for="income">Ingreso</label>
        </div>
        <div class="form-check">
          <input
            type="radio"
            id="expense"
            class="form-check-input"
            value="expense"
            v-model="transactionType"
          />
          <label class="form-check-label" for="expense">Gasto</label>
        </div>
      </div>
  

      <div class="d-flex justify-content-between">
        <input
          class="form-control me-4"
          type="text"
          placeholder="Add a new item"
          v-model="name"
        />
        <input
          class="form-control me-4"
          type="number"
          placeholder="Amount"
          v-model.number="amount"
        />
        <button class="btn btn-primary" @click="addItem">Add</button>
      </div>
    </div>
  </template>

<script>
    export default {
        name: "New",
        data() {
        return {
            nextId: 4,
            name: "",
            amount: 0,
            transactionType: "income",
       };
    },  
    
    methods: {
    addItem() {
      if (this.name !== "" && this.amount !== null) {
        // Ajusta el signo dependiendo del tipo
        const finalAmount =
          this.transactionType === "expense"
            ? -Math.abs(this.amount)
            : Math.abs(this.amount);

        this.$emit("addItem", {
          name: this.name,
          amount: finalAmount,
        });

        this.resetForm();
      } else {
        alert("Por favor completa todos los campos");
      }
    },
    resetForm() {
      this.name = "";
      this.amount = null;
      this.transactionType = "income";
    },
  },
};
</script>
<styles></styles>