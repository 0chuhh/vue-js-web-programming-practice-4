<template>
    <div class="main">
        <div class="wrapp">
            <slot></slot>
        </div>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>
.main {
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    background: #2E015C;
    overflow: hidden;
}

.wrapp {
    width: 1095px;
    height: 813px;
    max-width: 95vw;
    max-height: 95vh;
    position: relative;
}
@media (max-width: 1024px) {
    .main {
        height: auto;
        min-height: 100vh;
    }
    .wrapp {
        height: auto;
        max-height: none;
    }
}
</style>