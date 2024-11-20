<template>

    <form class="flex flex-wrap justify-between max-w-screen-lg m-auto mt-8">
      <div class="w-5/12 m-2 flex flex-col">
      <label for="newItem" class="uppercase font-bold text-sm mb hidden">Add new item</label>
   
      <input v-model="name" id="newItem"  type="text" placeholder="Add new item" class="rounded-md border p-2 text-black">

      </div>
      <div class="w-5/12 m-2  flex flex-col">
      <label for="newPrice" class="uppercase font-bold text-sm mb hidden">Price</label>

      <input v-model="amount" id="newPrice"  type="number" placeholder="0"  class="rounded-md border p-2 text-black">

      </div>

      <div class="my-2 flex justify-center w-full">

      <button @click.prevent="addItem()"  type="submit" class="border py-2 px-4 rounded-md  text-white transition-all bg-orange-400 hover:bg-orange-300">Add</button>
      
      </div> 
    </form>

</template>
  
  <script>
 
  
  export default {
    name: "addItem",
    data() {
      return {
        id: 1,
        name: "",
        amount: ""
      };
    },
    
    methods: {
      increaseId(){
        this.id++;
      },
      addItem() {
        this.increaseId();
        this.$emit("addItem", {
          id: this.id,
          name: this.name,
          amount: this.amount,
        });
      },
    },
  };
  </script>
  
  <style></style>
  