<template>
    <img
        :src="src"  
        >
</template>

<script>
    export default {
        props: ['src']
    }
</script>

<style scoped>
.leafs1 {
    position: absolute;
    bottom: 20px;
    left: -272px;
}

.leafs2 {
    position: absolute;
    top: -48px;
    right: -240px;
}
</style>