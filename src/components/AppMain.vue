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
        <header>
            <img src="../../images/header-bg.png" alt="header">
        </header>
        <main>
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

.icons {
    display: flex;
    justify-content: center;
    gap: 10px;
    flex-wrap: wrap;
}

.icon {
    background-color: #2E6754;
    border-radius: 10px;
    width: 80px;
    height: 80px;
}
</style>