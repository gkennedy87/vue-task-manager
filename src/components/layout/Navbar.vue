<template>
    <nav class="navbar navbar-dark bg-darkBlue mb-3">
        <h1 class="navbar-brand">Task Manager</h1>
    </nav>
</template>

<script>
export default {
    name: "Navbar",
    mounted() {
        console.log('navbar mounted');
    }
}
</script>

<style scoped>
    .bg-darkBlue {
        background-color: #202d3a;
    }
</style>