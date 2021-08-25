<template>
    <header class="main-header flex jc-between ai-center">
        <i class="fas fa-bars"></i>
        <div class="flex ai-center">
            <i class="far fa-envelope"></i>
            <img src="../assets/avatar_8.jpg" alt="avatar">
            <div>Marco Bagnasco</div>
            <i class="fas fa-chevron-down"></i>
        </div>
    </header>
</template>

<script>
export default {
    name: 'MainHeader',
}
</script>

<style lang="scss" scoped>
    .main-header {
        position: absolute;
        top: 0;
        left: 0;
        height: 45px;
        width: 100%;
        padding: 10px 20px;
        background-color: #ddd;
        z-index: 10;
        
        img{
            height: 25px;
            margin: 0 7px;
            border-radius: 50%;
        }
    }
</style>