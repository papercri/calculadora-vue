<template>
  <div class="col">
    <div class="card card-body shadow border-0">
      <h4> {{ title }} </h4>
      <h2 :class="[data>0 ? 'text-success' : 'text-danger']"> {{ data }} €</h2>
    </div>
  </div>
</template>

<script>
  export default {
      name: "Box",
      props: {
      title: String,
      data: Number,
    },
  };
</script>

<style></style>