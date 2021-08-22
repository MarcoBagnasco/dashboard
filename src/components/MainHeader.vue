<template>
    <header class="main-header flex jc-between ai-center">
        <i class="fas fa-bars"></i>
        <div class="flex ai-center">
            <i class="far fa-envelope"></i>
            <img src="../assets/avatar_8.jpg" alt="avatar">
            <div>Marco Bagnasco</div>
            <i class="fas fa-angle-down"></i>
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
        padding: 10px 20px;
        background-color: #eee;
        img{
            height: 25px;
            margin: 0 7px;
            border-radius: 50%;
        }
    }
</style>