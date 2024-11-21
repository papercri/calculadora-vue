<template>
    <div>
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
            <button class="btn btn-danger ms-3" @click="deleteTransaction(item.id)">
              Delete
            </button>
          </div>
        </li>
      </ul>
    </div>
</template>

<script>

export default {
  name: "ContentTable",
  props: ["filteredItems"],
  methods: {
    deleteTransaction(id) {
      this.$emit("deleteTransaction", id);
    },
  },
};
</script>
<style>
</style>