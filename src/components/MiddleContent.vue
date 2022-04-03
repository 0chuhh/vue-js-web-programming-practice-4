<template>
    <div class="middle-content">
        <slot></slot>
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style scoped>
.middle-content {
    font-family: PT Sans Caption;
    font-style: normal;
    font-weight: bold;
    font-size: 22px;
    line-height: 40px;
    text-align: center;
    color: #FFFFFF;
    max-width: 589px;
    margin: 0 auto;
    position: relative;
}
@media (max-width: 1024px) {
    .middle-content {
        margin: 40px auto;
    }
}
</style>