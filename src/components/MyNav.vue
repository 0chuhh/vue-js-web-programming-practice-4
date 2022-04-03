<template>
    <div class="nav">
        <a href="#" class="link link__active"></a>
        <a href="#" class="link"></a>
        <a href="#" class="link"></a>
        <a href="#" class="link"></a>
        <a href="#" class="link"></a>
        <a href="#" class="link"></a>
    </div>
</template>

<script>
    export default {
    }
</script>

<style scoped>
.nav {
    display: flex;
    flex-direction: row;
}

.link {
    flex: 1 1 100%;
    background: #0096EC;
    height: 6px;
}

.link::before {
    content: '';
    display: inline-block;
    width: 2px;
    height: 18px;
    background: #0096EC;
}

.link:first-child {
    border-radius: 3px 0 0 3px;
}

.link:first-child::before {
    display: none;
}

.link:last-child {
    border-radius: 0 3px 3px 0;
}

.link__active {
    background: #6BFF2F;
}
</style>