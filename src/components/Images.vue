<template>
        <div 
            class="image"
        >
        <img
            :src="src"
        >

        </div>
</template>

<script>
    export default {
        props: ['src'],
        methods:{
        },
    }
</script>

<style>
.image__success {
    outline: 10px solid #9AFF21;
}

.image__success::before {
    width: 52px;
    height: 38px;
    background-image: url("data:image/svg+xml,%3Csvg width='52' height='38' viewBox='0 0 52 38' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M4 17.5L19 32.5L47.5 4' stroke='url(%23paint0_linear_947_6985)' stroke-width='10' stroke-linejoin='round'/%3E%3Cdefs%3E%3ClinearGradient id='paint0_linear_947_6985' x1='25.75' y1='4' x2='25.75' y2='32.5' gradientUnits='userSpaceOnUse'%3E%3Cstop stop-color='%239AFF21'/%3E%3Cstop offset='1' stop-color='%2366FF31'/%3E%3C/linearGradient%3E%3C/defs%3E%3C/svg%3E%0A");
}

.image__failure {
    outline: 10px solid #FF0F8E;
}

.image__success img,
.image__failure img {
    transition: 0s;
}

.image__success::before,
.image__failure::before {
    content: '';
    display: inline-block;
    position: absolute;
    top: -25px;
    left: 50%;
    transform: translate(-50%, -100%);
}
.image {
        margin-bottom: 20px;
    }

.image__failure::before {
    width: 36px;
    height: 37px;
    background-image: url("data:image/svg+xml,%3Csvg width='36' height='37' viewBox='0 0 36 37' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M4 4L32 33' stroke='url(%23paint0_linear_947_6981)' stroke-width='10'/%3E%3Cpath d='M4 33L32 4' stroke='url(%23paint1_linear_947_6981)' stroke-width='10'/%3E%3Cdefs%3E%3ClinearGradient id='paint0_linear_947_6981' x1='18' y1='4' x2='18' y2='33' gradientUnits='userSpaceOnUse'%3E%3Cstop stop-color='%23FF0F8E'/%3E%3Cstop offset='1' stop-color='%23FF549C'/%3E%3C/linearGradient%3E%3ClinearGradient id='paint1_linear_947_6981' x1='4' y1='18.5' x2='32' y2='18.5' gradientUnits='userSpaceOnUse'%3E%3Cstop stop-color='%23FF0F8E'/%3E%3Cstop offset='1' stop-color='%23FF549C'/%3E%3C/linearGradient%3E%3C/defs%3E%3C/svg%3E%0A");
}

.image {
    background: #004BAA;
    border-radius: 26px;
    position: relative;
    z-index: 2000;
}

.image img {
    border-radius: 26px;
    display: block;
    transition: 0.5s;
}

.image:not(.image__success, .image__failure):hover img {
    transform: translate(-10px, -12px);
    cursor: pointer;
}

.images {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}




@media (max-width: 1024px) {
    .images {
        flex-wrap: wrap;
    }
}

</style>