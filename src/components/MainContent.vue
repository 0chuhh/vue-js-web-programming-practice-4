<template>
    <div class="content">
        <slot></slot>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>
.content {
    width: 100%;
    height: 100%;
    background: linear-gradient(241.84deg, #003DCE -3.61%, rgba(21, 170, 255, 0) 48.73%, rgba(20, 164, 252, 0.0598291) 48.74%, #003DCE 95.39%), linear-gradient(37.63deg, #2B62D5 5.17%, #15AAFF 59.05%);
    border-radius: 51px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 40px 73px 82px;
    box-sizing: border-box;
    position: relative;
}
@media (max-width: 1024px) {
    .content {
        height: auto;
    }
}
</style>