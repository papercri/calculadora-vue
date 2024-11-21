<template>
    <input type="text" placeholder="search..." class="form-control mt-5 w-25" v-model="searchTerm"/>
</template>
<script>
    export default {
        name: "Search",
        props: "searchTerm",
    };  
</script>
    
<styles>
</styles>