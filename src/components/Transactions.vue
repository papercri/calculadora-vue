<template>
<div class="grid grid-cols-3 content-center items-center" v-for="(tran, index) in transactions" :key="tran.id">
    <div> {{ tran.name }}</div>
    <div :class="{'text-red-600': tran.amount < 0}">{{ tran.amount }}</div>
    <button @click="handleClick(tran.id)">Delete</button>
</div>
 </template>
 
 <script>
 export default {
   name: "Transactions",
   data() {
     return {
       
     }
   },
   props: ["transactions"],
   methods: {
    handleClick(id) {
      this.$emit("deleteTransaction", {
        id
      });
    },
  },
 };
 </script>
 
 <style></style>
 