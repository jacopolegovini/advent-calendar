<script>
export default {
    data() {
        return {

        }
    }
}
</script>

<template>
    <div class="page">
        <header class="container img-container">
            <img src="../../images/header-bg.png" alt="header">
        </header>
        <main class="container icons-container">
            <div class="icons">
                <div class="icon" v-for="icon in 24">{{ icon }}</div>
            </div>
        </main>
    </div>
</template>

<style scoped>
header img {
    background-color: #2D28EB;
}

.img-container,
.icons-container {
    width: 1040px;
}

.icons-container {
    margin-top: 20px;
}

.icons {
    display: flex;
    justify-content: space-between;
    gap: 30px;
    row-gap: 20px;
    flex-wrap: wrap;
    width: 1040px;
}

.icon {
    background-color: #2E6754;
    border-radius: 10px;
    width: 100px;
    height: 100px;
}
</style>