<template>
    <div class="main-content">
        <MainHeader/>
    </div>
</template>

<script>
import MainHeader from './MainHeader.vue';

export default {
    name: 'Main',
    components:{
        MainHeader,
    }
}
</script>

<style lang="scss" scoped>
    .main-content {
        // height: 100vh; //fake
        flex-grow: 1;
        color: #666;
        background-color: #f00;
    }
</style>