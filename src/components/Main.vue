<template>
    <div class="main-content">
        <MainHeader/>
    </div>
</template>

<script>
import MainHeader from './MainHeader.vue';
import axios from 'axios';

export default {
    name: 'Main',
    components:{
        MainHeader,
    },
    data(){
        return {
            data: [],
        }
    },
    created(){
        this.getData();
    },
    methods: {
        getData(){
            let config = {
                headers: {
                    'X-Master-Key': '$2b$10$uF.P5J6WPLO1FKJz.ms4BuEirEJB0LqkQzw4Pfg6U48oBjz2nd21.',
                    'X-Bin-Meta' : false
                }
            }
            console.log('ciao');
            axios.get('https://api.jsonbin.io/v3/b/6123d5ab2aa80036126e9315', config)
            .then(res => {
                this.data = res.data;
            })
            .catch(err => {
                console.log(err);
            });
        }
    }
}
</script>

<style lang="scss" scoped>
    .main-content {
        flex-grow: 1;
        color: #666;
        background-color: #eee;
    }
</style>