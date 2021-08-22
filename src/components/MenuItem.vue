<template>
    <div class="menu-item">
        <div class="item flex jc-between" @click="toggle">
            <div class="flex">
                <i :class="icon"></i>
                <div class="title">{{title}}</div>
            </div>
            <i v-if="close" class="fas fa-chevron-down"></i>
            <i v-else class="fas fa-chevron-up"></i>
        </div>
        <div v-show="!close" class="menu-content">
            <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MenuItem',
    props:{
        icon: String,
        title: String,
    },
    data(){
        return {
            close: true,
        }
    },
    methods:{
        toggle(){
            this.close = !this.close;
        }
    }
}
</script>

<style lang="scss" scoped>
    .menu-item{
        cursor: pointer;

        .title{
            margin-left: 15px;
        }
    
        .item{
            padding-bottom: 10px;
        }
    
        .menu-content{
            margin-bottom: 20px;
            font-size: 0.9rem;
        }
    }
</style>